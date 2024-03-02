
# Basic concepts

- **Processor Instruction cycle**: loop Fetch-Decode-Execute (only thing a processor is able to do)
![[Pasted image 20240125151710.png]]

- **Hardware Interrupt**: Signal. Interrupts the instruction cycle by making the processor jump to another instruction
- **TRAP Instruction**: Processor instruction that arises an interrupt
- **Processor user mode**: Execution mode with restrictions
- **Processor kernel mode**: Execute mode without restrictions

**Parts of a computer**
- **Processor**: Computes, executes and stores information on registers
- **Main memory**: Stores data and programs
- **I/O devices**: connect the computer with the rest of the world
- **System Bus**: connects all the components

# Operating System Concept and Functions

An OS aims to **simplify the management and use** of a computer, making it **safe** and **efficient**. It's **responsible for coordinating all the individual components of a computer**. It acts as an **interface** between the user and the computer. 

# OS Booting and Activation

When a computes is turned on, its design makes the CPU jump to a specific memory address where there's a **program** that checks the existing hardware configuration its state, loads the OS and launch a User Interface.
As the processor can only execute one process at a time, once the user executes an application the OS is able to take control again via ***interrupts***. This will happen when:
- When the application ends
- When the application tries to execute an illegal operation
- When the application needs the OS to execute some special operation
- When any device needs attention

## Interrupt management

Whenever an interrupt appears, the CPU stops executing whatever it's doing and jumps to execute some OS code. It:
- Keep the PC and Status resister
- Uses the Interrupt Vector Table to set the new value of the PC
- Change to Kernel mode
- **Execute the handling routine**
- Resume the execution (Restore the stored values of PC and SR and return to user mode)

# Types of Operating Systems

- Single task / Multitasking
- Single-process / Multiprocessing
- Single User / Multiuser
- Interactive / Batch
- Uniprocessor / Multiprocessor
- Embedded
- Real-time
- Mobile

## OS virtualization

Virtualization is widely used. It allows to have several different systems running in the same machine at the same time and optimizes the use of the CPU. The software that creates and manages the virtual machine is calles **hypervisor**. It can be implemented in two different ways:
- **Bare metal** hypervisor: The software is running directly on the Hw, without the OS
- Hypervisors **running on a OS**: It runs on a OS installed on the hardware


# Components of the OS

From a functional point of view, the OS contains:
- Process management system
- Memory management system
- Device management system
- File management system
- Security and Protection

# Interfaces provided by the OS

## API

- Standard POSIX (Portable Operating System Interface; X Unix)
	- Specification, not implementation
- SUS (Single Unix Specification). Evolution of POSIX
- Win32 Interface
	- Not standard but Microsoft implementation

## User Interface

- GUIs
- Command line (CLI)
- Command files or shell-scripts
	- Bourne in Unix
	- Cmd-line, Jscript, Windows PowerShell

# Design of the Operation System

## Operating System Architecture

- **Monolithic Operating System**
	- Functionality into a single program
	- Running in kernel mode
	- Hard to modify
- **Structured Operating Systems**
	- Organized in layers
	- Microkernel (Client / Server)
- **Hybrid Operating Systems**
	- Modular
	- Non pure Microkernel
- **Distributed Operating Systems**
	- Pure
	- Middleware
- **Pure microkernel architecture (client server)** 
	![[Pasted image 20240125161730.png]]
## Design of the Unix OS

![[Pasted image 20240125161927.png]]

## Design of Windows NT

![[Pasted image 20240125162000.png]]

# Evolution of Operating Systems

Serial Processing $\rightarrow$  Simple Batch System $\rightarrow$ Multiprogrammed Batch Systems $\rightarrow$ Time Sharing (interactive) Systems $\rightarrow$ Personal computers

| Period                    | Operating System Features                                                                                                                                                                                                                                                                                                                                                                                         | HW / OS / Languages                                                                                                     |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| The 40s<br>prehistory     | Nonexistent. Serial processing                                                                                                                                                                                                                                                                                                                                                                                    | Vacuum valves<br>Von Neumann Arch.<br>ENIAC (1943)<br>Assembler                                                         |
| The 50s<br>1st Generation | Resident monitor:<br>• Loading and executing programs<br>• Processing batch jobs<br>• I/O Routines (device drivers)<br>• Error Recovery<br>• Control Language                                                                                                                                                                                                                                                     | Transistors<br>IBSYS (IBM)<br>FMS (IBM)<br>FORTRAN, COBOL                                                               |
| The 60s<br>2nd Generation | Performance improvements:<br>• Multiprogramming (I/O by DMA)<br>• Interactive Multiuser: Timesharing<br>• Real Time<br>• Multiprocessor<br>Large and expensive<br>Complex control language                                                                                                                                                                                                                        | Integrated Circuits<br>PDP-8 Digital<br>IBM 360<br>CTSS (IBM 7090)<br>OS/360(IBM 360)<br>MULTICS – UNIX<br>BASIC, ALGOL |
| The 70s                   | General purpose OS<br>Dissemination of multiuser timesharing<br>**Unix**<br>•ATT Bell Laboratories<br>•Ken Thompson, Dennis Ritchie<br>•C language implementation (Dennis Ritchie)<br>(1973)<br>•Diffusion Lab. and universities (Source<br>Code)<br>•Different distributions<br>•Appearance of BSD (Berkeley Uni)<br>•Emergence of System V (Bell Lab)<br>•Other manufacturers (Sun, HP, IBM) …                  | PDP-7,11<br>Apple II<br>Intel 8008<br>UNIX (Bell 1976)<br>MVS (IBM) - Mainframes<br>VM (IBM) Minicomputers<br>CP/M- PC  |
| The 80s                   | Simplification of the OS.<br>Importance of the user<br>Network management<br>Network Operating Systems<br>Graphical User Interfaces (GUIs)<br>Internal Object Oriented Design<br>Different OS for different PC processors<br>Distributed Operating Systems                                                                                                                                                        | UNIX<br>MS-DOS<br>Windows, Amiga<br>Mc OS, OS/2<br>Mach, Chorus,<br>Amoeba                                              |
| The 90s                   | Free Operating Systems<br>Real-time Operating Systems<br>Operating Systems with parallel processing<br>Layers of middleware (Middleware)<br>Client / Server architecture<br>Interfaces standardization<br>Inclusion of multiple programming interfaces<br>Security, Cryptography<br>Operating systems for teaching                                                                                                | Linux (91) FreeBSD<br>QNX<br>CORBA, DCOM<br>Windows XP, NT..<br>POSIX<br>MINIX, SOS,<br>NACHOS                          |
| Present and<br>future     | Embedded operating systems: phones, cars,<br>PDAs<br>Parallelism<br>Distributed Computing<br>Fault Tolerance<br>Development of new interfaces<br>Customization and Usability<br>Open Systems<br>Object Oriented Design<br>Multiple Personalities<br>Distributed client-server architecture<br>Incorporating many features of security and<br>remote access<br>Significant improvements in security<br>(hopefully) | Linux (RedHat<br>Slackware SuSe…)<br>Windows Longhorn<br>Windows CE                                                     |
