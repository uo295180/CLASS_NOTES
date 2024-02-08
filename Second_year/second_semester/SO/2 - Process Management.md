# Process Management basics

A process is **any running program**. It needs certain **RESOURCES** like:
- CPU time
- Memory
- Files
- I/O Devices
Resources are allocated for a process:
- When creating 
- During execution
The main duties of the OS process manager are:
 - **Create** and **manage** the concept of process
 - Create and terminate processes
 - Stop, resume, get statistics...
 - Process scheduling
 - Establishing mechanisms for process **synchronization and communication**
 - Handling **deadlocks**
Minimize the OS **overhead**.
## Multitasking

Several processes can be executed simultaneously on a machine with a single processor using *parallelism* between the processor and I/O and with processor time sharing among processes.
![[Pasted image 20240208151542.png]]

![[Pasted image 20240208151641.png]]

# Elements of a Process

It's something that's alive. It's defined by:
- It's code
- The value of their data in that instant
- The value of the execution stack
- The value of all the registers of the processor
All this information constitutes what is known as the **state of the process**.
A process is:
- **Text section** (code)
- **Data section** (global variables and dynamic memory)
- **Stack** (temporary data)
- Current activity represented in a **PCB** data structure:
	- Value of the **program counter**
	- Contents of **processor registers**
	- Priority, status, open files, memory space location, ...
The OS usually uses a **Table of PCBs** to locate all processes in the system. It's called ***Process Table***
## The Process Control Block

Or PCB, is the data structure containing all the elements that defines the execution of the process in one instant of time. It allows to **interrupt** a running process and later **resume** it's execution. It's created and managed by the operating system. Key tool to support multiprogramming techniques
![[Pasted image 20240208154326.png]]
# Process lifecycle

## Five states model

![[Pasted image 20240208153119.png]]

As a process is executed, its **state changes**. They can be in one of this states:
- **New:** The process is being created
- **Running:** The process is in the CPU executing instructions
- **Blocked:** The process is waiting for an event to occur
- **Ready:** Waiting to be assigned to a processor
- **Finished**: Execution completed, thus no further instructions to execute and the OS will withdraw the resource it consumes
Only **one process can be running on the processor** at any given time, but many other processes can be ready and waiting.

Now, state transitions in this model are:
- **None to New:** creates a new process to run a program
- **New to Ready:** the system is ready to accept a new process as it has enough resources for it
- **Ready to Running:** The system chooses one of the processes in the ready state to carry out execution (*scheduling*)
- **Running to Finished:** the running process is terminated by the OS if it indicates that it has ended, abandoned or canceled
- **Running to Ready:** OS preempt the CPU from process (its time slice has expired, a more important process is ready,...) or yields the voluntarily
- **Running to Blocked:** the process asks for a (slow) operation and waits for its completion
- **Blocked to Ready:** the (slow) operation the process is waiting for eventually finishes
- **Ready to Finished:** a parent may terminate a child process at any time, or if the parent is completed all children can be completed
- **Blocked to Finished:** the same criteria as above

The OS keeps several queues associated to each state, to store information about whet processes are in that state
![[Pasted image 20240208154621.png]]

## OS interrupt handling

The processor instruction cycle:
![[Pasted image 20240208154823.png]]

Once executed the code to handle the interrupt, and **before** executing the **IRET** instruction:
1 - A new process is chosen from the *Ready to Run* queue
2 - A context (or process) switch is executed:
	2.1 - The values of PC and PSW are copied to the PCB of the interrupted process. The values of the rest of the CPU registers are copied as well
	2.2 - The values of the new process are copied from its PCB table to the processor. PC and PWS are copied into the stack instead
IRET execution will restore these values to the CPU[[README]]