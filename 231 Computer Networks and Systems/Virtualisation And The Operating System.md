Noted: 13/10/2025 #week2

> [!info] Resources
> [📊 PowerPoint](cpuVirtualisationAndTheOS.pdf)
> [📽️Lecture Recording]()

```table-of-contents
```
## Computer Architecture Recap

Defined by the CPU architecture, instruction-set architecture (like ARM Assembly) is the lowest interface between computer hardware and software and defines how software tells the hardware what to do. #keyTermDefinition 

In a simple assembly program, the code runs directly on the hardware and assumes **exclusive control of the CPU**, with no operating system to manage resources. In contrast, a real system runs many programs at once, and since the CPU can only execute one program’s instructions at a time, the **operating system** manages access by performing **context switching**—saving one program’s CPU state (like registers and the program counter) and loading another’s. This allows multiple programs to share the CPU efficiently, creating the illusion that they run simultaneously.


## The Operating System

An operating system (OS) is a software layer that acts as an intermediary between computer hardware and user applications. It manages the system’s resources such as the CPU, memory, and input/output devices to ensure programs run efficiently and safely. #keyTermDefinition 

It also provides programming abstractions (like files, processes, and memory management) that make it easier and safer for developers to write software without needing to control hardware directly. Additionally, it offers essential services such as process scheduling, which decides which program uses the CPU next, and device drivers, which allow software to communicate with hardware components.

### OS Scheduling

#doitlater 

## Virtualisation

Virtualisation is a combination of indirection and multiplexing. It's the process of creating a virtual version of a resources (like hardware, OS, network, or storage) so that multiple independent systems or applications can share it as if has its own dedicated resource. #keyTermDefinition 

Examples of virtualisation:
- Virtual memory
- Virtual modem
- Cloud computing

### OS Virtualisation

- **Goal**: Give each process the illusion of exclusive resource access.
- **Constraints**: The resources are fixed and shared among all processes, ensuring isolation and security.
- **Time-sharing**: Exclusive use, one at a time
- **Space-sharing**: Everyone gets a small chunk all the time

There are different strategies for resources:
- **CPU**: Time sharing, alternate between tasks
- **Memory**: Space sharing
- **Disk**: Space sharing

### CPU Virtualisation

When the user executes a program, the OS creates a process. #doitlater 

## A Process

A **program** is a collection of binary instructions and static data stored on disk.

A **process** is an **operating system (OS) abstraction** that represents a running instance of a program — that is, a program **loaded into memory and executed**.

A process encapsulates:

- **Memory resources** (code, data, heap, stack)
- **Execution state** (CPU registers, program counter)
- **Resources** (open files, sockets, devices)
- **Process Control Block (PCB)** — metadata maintained by the OS, tracking the process’s state, scheduling info, and resources

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


#doitlater 
