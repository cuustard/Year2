Noted: 13/10/2025 #week2

> [!info] Resources
> [📊 PowerPoint](WK2.LC1.CPU_Virtualisation_And_OS.pdf)
> [📽️Lecture Recording](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=5288b929-ebf8-446f-b606-b36800352c47)

```table-of-contents
```
## Computer Architecture Recap

Defined by the CPU architecture, instruction-set architecture (like ARM Assembly) is the lowest interface between computer hardware and software and defines how software tells the hardware what to do. #keyTermDefinition 

In a simple assembly program, the code runs directly on the hardware and assumes **exclusive control of the CPU**, with no operating system to manage resources. In contrast, a real system runs many programs at once, and since the CPU can only execute one program’s instructions at a time, the **operating system** manages access by performing **context switching**—saving one program’s CPU state (like registers and the program counter) and loading another’s. This allows multiple programs to share the CPU efficiently, creating the illusion that they run simultaneously.

---
## The Operating System

An operating system (OS) is a software layer that acts as an intermediary between computer hardware and user applications. It manages the system’s resources such as the CPU, memory, and input/output devices to ensure programs run efficiently and safely. #keyTermDefinition 

It also provides programming abstractions (like files, processes, and memory management) that make it easier and safer for developers to write software without needing to control hardware directly. Additionally, it offers essential services such as process scheduling, which decides which program uses the CPU next, and device drivers, which allow software to communicate with hardware components.

---
### OS Scheduling

An OS scheduler is the part of the OS that decides which process gets to use the CPU (or other resources) at any given time. It ensures efficient, fair, and responsive execution of multiple processes. #keyTermDefinition 

---
## Virtualisation

Virtualisation is a combination of indirection and multiplexing. It's the process of creating a virtual version of a resources (like hardware, OS, network, or storage) so that multiple independent systems or applications can share it as if has its own dedicated resource. #keyTermDefinition 

Examples of virtualisation:
- Virtual memory
- Virtual modem
- Cloud computing

---
### OS Virtualisation

- **Goal**: Give each process the illusion of exclusive resource access.
- **Constraints**: The resources are fixed and shared among all processes, ensuring isolation and security.
- **Time-sharing**: Exclusive use, one at a time
- **Space-sharing**: Everyone gets a small chunk all the time

There are different strategies for resources:
- **CPU**: Time sharing, alternate between tasks
- **Memory**: Space sharing
- **Disk**: Space sharing

---
### CPU Virtualisation

When the user executes a program, the OS creates a process. The OS time-shares CPU across multiple processes. The OS scheduler picks one of the executable processes to run and must keep a list of processes and metadata for policy.

---
## A Process

A **program** is a collection of binary instructions and static data stored on disk. #keyTermDefinition 

A **process** is an **operating system (OS) abstraction** that represents a running instance of a program — that is, a program **loaded into memory and executed**. #keyTermDefinition 

A process encapsulates:

- **Memory resources** (code, data, heap, stack)
- **Execution state** (CPU registers, program counter)
- **Resources** (open files, sockets, devices)
- **Process Control Block (PCB)** — metadata maintained by the OS, tracking the process’s state, scheduling info, and resources

---
### Process API (UNIX)

UNIX-like systems provide a standard set of system calls to manage processes:

- **`fork()`**  
    Creates a **new process** by duplicating the calling process.
    - The child process receives a **unique PID**.
    - Both parent and child continue execution from the point of the `fork()` call.
    - The parent can distinguish itself from the child by checking the return value of `fork()`.
- **`exec()` / `execvp()`**  
    Replaces the **current process’s memory image** with a **new program**.
    - Keeps the same PID, but completely replaces the code, data, and stack.
    - Typically used after `fork()` to start a different program in the child process.
- **`wait()`**  
    Suspends the parent process until one of its child processes terminates.
    - If `wait()` is **not** called, the child process becomes a **zombie** — a terminated process whose entry still exists in the process table until the parent collects its exit status.

---
### Process Creation

When a new process is created, the operating system performs several key steps to prepare it for execution:

1. **Allocate internal data structures**
    - The OS creates bookkeeping structures (e.g., **Process Control Block**, scheduling info, resource tables).
2. **Allocate an address space**
    - Reserves virtual memory regions for **code**, **data**, **heap**, and **stack**.
3. **Load program code and data from disk**
    - The executable file is read into memory; initial segments (text, data, bss) are mapped.
4. **Create runtime stack and heap**
    - The stack is set up for function calls and local variables.
    - The heap is initialized for dynamic memory allocation.
5. **Open standard I/O file descriptors**
    - `STDIN`, `STDOUT`, and `STDERR` are connected to default devices (usually the terminal).
6. **Initialize CPU registers**
    - The **program counter (PC)** points to the entry function (e.g., `_start`), and other registers are set to known states.

---
## System Call

A system call allows programs to request a service from the kernel. It's the interface between user programs (in user space) and the OS (in kernel space). The OS at boot registers the address of a system call handler function with the CPU. A process executes the trap instruction. The process context is stored in memory, the state of the OS is loaded, and the CPU executes the call handler function

---
## Limited Direct Execution (Boot)

| OS @ Boot             | Hardware                                            | Program |
| --------------------- | --------------------------------------------------- | ------- |
| initialize trap table |                                                     |         |
|                       | remember address of syscall handler & timer handler |         |
| Start interrupt timer |                                                     |         |
|                       | Start timer                                         |         |
|                       | Interrupt CPU in X msec                             |         |


---
## Limited Direct Execution (Start process)

| OS @ Boot (Kernel Mode)       | Hardware                                                        | Program (User Mode) |
| ----------------------------- | --------------------------------------------------------------- | ------------------- |
| Create entry for process list |                                                                 |                     |
| Allocate memory for program   |                                                                 |                     |
| Load program into memory      |                                                                 |                     |
| Setup user stack with argv    |                                                                 |                     |
| Fill kernel stack with reg/PC |                                                                 |                     |
| return-from-trap              |                                                                 |                     |
|                               | restore regs (from kernel stack) move to user mode jump to main |                     |
|                               |                                                                 | Run main()          |

---

## Limited Direct Execution (System Call)

| OS @ Boot (Kernel Mode)                         | Hardware                                                                 | Program (User Mode)                |
| ----------------------------------------------- | ------------------------------------------------------------------------ | ---------------------------------- |
|                                                 |                                                                          | Call system call trap into OS      |
|                                                 | save regs (to kernel stack)                                              |                                    |
|                                                 | move to kernel mode, jump to trap handler                                |                                    |
| Handle trap<br>  Do work of syscall             |                                                                          |                                    |
| return-from-trap                                |                                                                          |                                    |
|                                                 | restore regs (from kernel stack) move to user mode jump to PC after trap |                                    |
|                                                 |                                                                          | return from main trap (via exit()) |
| Free memory of process Remove from process list |                                                                          |                                    |

---
## Limited Direct Execution (Timer interrupt)

| OS @ Boot (Kernel Mode)                                                                                                        | Hardware                                   | Program (User Mode) |
| ------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ | ------------------- |
|                                                                                                                                |                                            | Process A           |
|                                                                                                                                | timer interrupt                            |                     |
|                                                                                                                                | save regs(A) to k-stack(A)                 |                     |
|                                                                                                                                | move to kernel mode, jump to timer handler |                     |
| Handle the trap                                                                                                                |                                            |                     |
| Call switch() routine<br>  save regs(A) to proc-struct(A) <br>  restore regs(B) from proc-struct(B) <br>  switch to k-stack(B) |                                            |                     |
|                                                                                                                                | restore regs(B) from k-stack(B)            |                     |
|                                                                                                                                | move to user mode, jump to B’s PC          |                     |
|                                                                                                                                |                                            | Process B           |

---
## Conclusion

**Operating System (OS) Definition:** Software layer between **hardware** and **user applications**.

- **Responsibilities:**
    - **Resource management** (CPU, memory, I/O devices).
    - Provide **safe and convenient programming abstractions**.
    - Offer **services** such as scheduling and device drivers.

- **CPU virtualization:** allows multiple processes to **share a physical CPU**.
    - **Limited direct execution** ensures the OS scheduler can control process execution.
    - Processes use **system calls** to access virtualized resources.
    - **Timer interrupts** enable the OS to pre-empt and schedule processes.

---