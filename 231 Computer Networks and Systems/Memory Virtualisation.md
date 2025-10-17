
> [!info] Resources
> [📊 PowerPoint](Resources/MemoryVirtualisation.pdf)
> [📽️Lecture Recording]()

OSes use spatial virtualisation to share address spaces between processes. The goals:
- **Transparency**: Programmers should be unaware if memory virtualisation
- **Efficiency**: virtualisation must not affect performance of negatively impact space allocation
- **Protection**: processes must not be able to view of edit memory areas from other programs

Throughout history:

![[Excalidraw/Drawing 2025-10-17 12.45.47.excalidraw]]


## Memory Components

- **Physical Memory**: The set of actual addresses of bytes on the RAM chips of a computer.
- **Virtual Memory**: The set of addresses visible to a process.
- **Process Address Space**: The range of addresses visible by a process.
	- **Static**: Code and global variables
	- **Dynamic**: The stack, head.
- **Memory Management**: A hardware component of the CPU that translates virtual pages to physical memory frames

 Why do we need dynamic memory?:
 - The amount of required memory may be task-dependent
 - Input size may be unknown at compile time
 - Conservative pre-allocation would be wasteful
 - Recursive functions (invocation frames)

## MV: Base And Bounds

