## IPC?
**Inter-Process Communication (IPC)** allows processes to exchange data and synchronize actions.
OS isolates processes for **protection and stability**, but real programs need cooperation.

Examples:
- GUI + background worker
- Web server + database

 Benefits:
- Improves responsiveness
- Enables parallel computation

Problem: processes cannot access each other’s memory directly.
**IPC = OS-provided mechanisms** for data exchange and synchronization.

---
## IPC Models

| Model               | Example      | Advantages     | Disadvantages   |
| ------------------- | ------------ | -------------- | --------------- |
| **Message Passing** | Pipe, Socket | Simple, safe   | Kernel overhead |
| **Shared Memory**   | `mmap()`     | Fast, flexible | Race conditions |
### Message Passing
- Data exchanged via **OS-managed channels**: pipes, queues, sockets. 
- Simple but slower due to kernel mediation.
### Shared Memory
- Processes share a mapped memory region.
- Very fast after setup (no syscall overhead).
- Requires **synchronization** to prevent races.

---
## Message Passing with Pipes
### Basics
A **pipe** is a unidirectional FIFO buffer in the kernel.
Created with `pipe() → (r_fd, w_fd)`.

Common usage:
- Parent creates a pipe.
- Calls `fork()`.
- Both child and parent inherit the same file descriptors.

![[Pasted image 20251020120212.png]]
### File Descriptors (FD)
Integer handles for open files/resources.
Table per process maps FDs to kernel “open file” objects.

Standard FDs:
- `0`: stdin
- `1`: stdout
- `2`: stderr
### Example
```
r_fd, w_fd = os.pipe()
pid = os.fork()

if pid == 0:  # Child
	os.close(w_fd)
    msg = os.read(r_fd, 100)
    print("Child received:", msg.decode())
    os.exit(0)
else:          # Parent
    os.close(r_fd)
    os.write(w_fd, b"Hello from parent!")
```
Data passes through the **kernel buffer**, not directly between processes.
![[Pasted image 20251020120155.png]]
### Pipe Behaviour
**Blocking I/O**
- `read()` blocks if the pipe is empty.
- `write()` blocks if the pipe is full (buffer ≈ 64 KiB).

**End-of-Stream detection**
- All readers closed → writers get `SIGPIPE` / `EPIPE`.
- All writers closed → readers get 0 (EOF).
### Handling Exceptions
```
try:
    os.write(w_fd, b"Hello from parent!")
except BrokenPipeError:
    print("Parent write error: no reader")
finally:
    os.close(w_fd)
```
### Pipes in Shell
Example: `ps aux | grep python`
- Shell performs **two forks** and uses `dup2()` to connect stdout → stdin.
- `dup2(oldfd, newfd)` duplicates an FD to a specific target.

---
## Message Passing via Sockets
- Similar to pipes, but supports **inter-machine communication**.
- Used with `socket.send()` and `socket.recv()`.
- Local sockets can be used for processes on the same host.
---
## Shared Memory IPC
OS maps **the same physical memory** into multiple processes’ address spaces.
- Mechanism: `mmap()`
    - Can be anonymous or file-backed.
- Once set up → direct memory access (no kernel per read/write).
### Example
```
import os, mmap

m = mmap.mmap(-1, 32)

if os.fork() == 0:
    m[:11] = b'hello world'
    m.close()
    os._exit(0)
else:
    os.wait()
    print(m[:11])  # b'hello world'
    m.close()
```
**Fastest IPC**, but requires synchronization.

---
## Synchronization in Shared Memory
- Needed to prevent **race conditions**.
- Without locks, reads/writes can overlap (partial data).
- Use **locks, semaphores, or condition variables** to ensure mutual exclusion.
---
## Threads: Shared Memory within a Process
### Concept
A **thread** is a lightweight unit of execution within a process.

Threads share:
- Address space
- Open files
- Global variables

Each thread has:
- Its own stack
- Its own registers and program counter
- Faster to create than processes (no full copy of resources).
![[Pasted image 20251020120245.png]]
### Example (Python)
```
import threading

def worker(name):
    print(f"Worker {name} starting")

t1 = threading.Thread(target=worker, args=("A",))
t2 = threading.Thread(target=worker, args=("B",))
t1.start(); t2.start()
t1.join(); t2.join()
print("Main done")
```
**Uncontrolled interleaving** → nondeterministic output order.

---
## Race Conditions
```
from threading import Thread
counter = 0

def increment():
    global counter
    for _ in range(100000):
        counter += 1  # Critical section

t1 = Thread(target=increment)
t2 = Thread(target=increment)
t1.start(); t2.start()
t1.join(); t2.join()
print(counter)
```
Counter likely incorrect due to **non-atomic updates**.

---
## Synchronization Tools
### Locks
Ensure **mutual exclusion** — one thread at a time in a critical section.
```
lock = threading.Lock()
with lock:
    counter += 1
```
### Condition Variables
Coordinate **thread progress** (not just mutual exclusion).

- `cond.wait()` → releases lock and waits.
- `cond.notify()` → wakes one waiting thread.
### Example (Producer/Consumer):
```
cond = threading.Condition()
queue = []

def producer():
    for i in range(5):
        with cond:
            queue.append(i)
            cond.notify()

def consumer():
    while True:
        with cond:
            while not queue:
                cond.wait()
            item = queue.pop(0)
        print("Consumed", item)
```
## Python’s GIL (Global Interpreter Lock)
- Only one thread executes Python bytecode at a time.
- Prevents **true parallelism** for CPU-bound code.
- Still useful for **I/O-bound** tasks.
- Race conditions still possible (especially in critical sections).
---
## From IPC to Networking
- Message passing generalizes to **sockets** across machines.
- Local IPC → pipes/shared memory
- Networked IPC → sockets/TCP
---
## Overview

| Concept             | Key Idea                                                      |
| ------------------- | ------------------------------------------------------------- |
| **Processes**       | Isolated; communicate via IPC (pipes, sockets, shared memory) |
| **Threads**         | Share memory; communicate via shared variables                |
| **Pipes**           | Simple, kernel-mediated, slower                               |
| **Shared Memory**   | Fastest IPC; requires explicit synchronization                |
| **Threads**         | Lightweight; enable concurrency and parallelism               |
| **Synchronization** | Locks for exclusion; condition variables for coordination     |

---