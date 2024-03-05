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
1. A new process is chosen from the *Ready to Run* queue
2. A context (or process) switch is executed:
	1. The values of PC and PSW are copied to the PCB of the interrupted process. The values of the rest of the CPU registers are copied as well
	2. The values of the new process are copied from its PCB table to the processor. PC and PWS are copied into the stack instead
IRET execution will restore these values to the CPU

## Context switch

It makes a process leave the CPU and assign it to another process. It implies:
- Save the state of the processor in the PCB of leaving process
- Restore the state of the processor form the PCB of the process to be executed

![[Pasted image 20240229204710.png]]

Some interrupts will cause a process switch:
- The current process cannot continue $\rightarrow$ It ends or it goes to the blocked state
- The current process can continue, but the system decides that it has been execution for too much time

## Process creation

![[Pasted image 20240229205059.png]]

# Threads

**A flow of execution within a process**:
- Multiple threads in the same task
- Each thread has:
	- Program Counter
	- Values of processor registers
	- Stack
- Threads share the
	- Code (text), data and heap
	- Open files, signals, etc

**Applications**
- Parallel Programming (task separation, modularity)
- Information Servers
**Advantages**
- Ease communication between threads
- Increase the speed of execution
- Switching between threads of the same process has little cost
- The cost of creation and destruction of threads is much lower than with process
- It therefore improves performance
**Disadvantages**
- Sharing memory space
- Greater programming difficulty

## KLT and ULT

![[Pasted image 20240215151052.png]]

|  | Advantages | Disadvantages |
| ---- | ---- | ---- |
| ULT | • More policies available<br>• Management operations are more<br>efficient (creation, switching, blocking)<br>• Synchronization operations are available<br>without kernel intervention. | • If a thread is blocked, all<br>the rest are blocked too.<br>• There is no real parallelism |
| KLT | • If a thread is blocked only that thread is<br>blocked.<br>• Real parallelism is possible | • Management operations<br>are less efficient<br>• Processor mode switch is<br>needed to change the<br>executing thread |
**1 / 10 / 100 relationship**
- ULT Thread creation: 1 time unit
- KLT Thread creation: 10 time units
- Process creation: 100 time units

# Process and thread scheduling

Scheduling is to share processor time between processes that can be executed
- Scheduling Levels (classically) :
	- **Short term**: assigns processor to ready processes
	- **Middle term**: includes process suspension in secondary memory. Reduces the **degree of multiprogramming**
	- **Long term**: decides which processes are admitted to the ready queue
- **Scheduler**: module that decides which process to move from ready to running (Short-term scheduler)
- **Dispatcher**: module that puts into execution the scheduled process

## 7 states process model

![[Pasted image 20240215151841.png]]

## Scheduling goals

**Metrics about scheduling algorithms performance**:

- **For processes (or threads)**
	- Turn-arround (or return) time (Tt)
	- Waiting time (Tw)
	- Response time (Tr)
- **For the system**
	- Processor use (C%)
	- Completed works rate (or Throughput) (P)

## Scheduling policies

- **Non-expulsive**
	- FCFS / FIFO (First Come, First Served) / (First In, First Out)
	- SJF (Shortest Time first)
- **Expulsive / preemptive** 
	- SRTF (Shortest Remaining Time First)
	- Round Robin (rotation shift)
- **Priorities**
	- Static
	- Dynamic

>[!Actual]
>Expulsive policy mix:
>Multilevel Queues with dynamic priorities + round robin

### FCFS scheduling policy or non-expulsive FIFO

*Ready* for execution processes are stored in a FIFO queue, so when a process changes its state to *Ready*, it goes to the end. A process leaves the CPU when:
- The process makes a *system call* and it gets *Blocked*
- The process ends
- The process *voluntarily* leaves the CPU
When the CPU is free the scheduler picks the first element in the queue
### SJF scheduling policy (Shortest Job First)

We choose the process with **shorter total duration**. Requires knowing the runtime before running the job. May cause long process starvation. It improves the average response time but increase the variance. Deprecated Policy. Designed for batch processing system before multiprogramming.
### Cyclic scheduling policy or Round Robin

The **clock device** produces an interrupt periodically. The interval between clock ticks can be modified. Different form CPU clock.
![[Pasted image 20240302125611.png]]

It **provides a fair sharing of processor time**. The system assigns a ***quantum***, or time slice, to the running process.
*Ready* for the execution processes are organized into a FIFO queue (as in FCFS). A process leaves the CPU when:
- The process makes a *system call* and as a result it changes to *Blocked*
- The process *ends*
- The process *exhausts its quantum*
When the CPU is free, the first process in the ready queue is chosen

![[Pasted image 20240302130116.png]]

### Priority scheduling policy

Each process is assigned a priority, that could be assigned by the user or by the system. The *ready queue* is sorted by priority, that could be static or dynamic.

**Static priority:**
- **Static: fixed during the lifetime of the process**
- Easy to implement
- Introduces little overhead on the system
- It doesn't adapt to changes in the environment
- May cause *starvation*.

**Dynamic priority**: priority varies during the process lifetime
- More difficult to implement
- Introduces more overhead on the system
- Avoid ***starvation***

>[!Examples]
>1.
>Priority aging:
>An initial priority is assigned and increases as time passes without running. When running, it returns to the initial priority
>
>2.
>It increases the priority when the process performs I/O operations and it decreases it when the quantum is exhausted

This policy is combined with others.

### Scheduling policy for real-time systems

Processes have a deadline that must be known by the scheduler. They must end executing before this deadline. There're two types of real time systems:
- Soft real-time systems. Only guarantee critical processes will have preference over non-critical processes
- Hard real-time. A process must be executed before its deadline
The system must minimize the *latency*. There're  specific policies: priority based, rate-monotonic (RMS), earliest-deadline-first...

### POSIX scheduling policy

It applies to Processes and Threads. Priority level between 0 and 31. **It chooses the highest priority thread (lower numeric value)**. 
Available policies (via *sched_setscheduler* system call):
- FIFO (SCHED FIFO)
- Round Robin (SCHED RR)
- Other (SCHED OTHER)
All of them exists in the system simultaneously: **Each process chooses the policy,** so we have all the policies at the same time.

### Windows NT scheduling policy

It's a cyclic scheduling with priorities and expulsion. It has 32 scheduling levels (0 to 31) organized as:
- 16 levels with **real-time priorities (16-31)**. Fixed priority, FIFO
- 15 levels with **varying priorities (1-15)**. They vary according to the thread behavior. Round Robin (Decremented if the thread runs out of time and incremented by performing an I/O operation)
- **0 level for system**
- Process and Threads have base priority

## Multiprocessor scheduling

Running the OS on multiprocessors:

- **Asymmetric multiprocessing**
	- A processor dedicated to running the OS
	- It can be slow but the OS is simpler
	- OS operations are not concurrent

- **Symmetric Multiprocessing**
	- The OS runs on all processors are needed
	- Concurrency issues inside the OS services
	- OS code is more complex
	- More efficient execution

**Scheduling criteria:**
**Processor affinity:** Tendency to assign the same processor to a process for maximizing the cache information. It can be:
- Soft: the scheduling is going to try to keep the process in the same processor
- Hard/Strict: possibility to indicate the processor or group where some processes can be executed (for critical processes)
**Load balancing:** keep the load of all processor similar

**Two possibilities to implement the read-to-run queue**
- **Unique queue for all processors**
	- We have load balancing by default
	- Single queue needs *protected access*, implies *bottleneck*

- **One queue per processor**
	- The previous bottleneck disappears
	- Load Rebalancing is not automatic:
		- Push migration: the OS checks periodically the load of every processor, moving processes among processors to balance them
		- Pull migration: when a processor is idle, it takes processes from the queue of other processor

**Thread scheduling policies**:
1. Not taken into account the relationships between same process' threads
2. It takes into account the relationships between threads
	- Shared time
		- Applications are multiplexed in time 
		- Time is assigned to each application (set of threads) in a processor. All threads are running on the same processor
		- It takes advantage of the processor affinity
	- Shared space
		- Applications are multiplexed in space and time
		- Application's threads are distributed among groups of processors
		- Applications are also multiplexed in the time

Both types can use shared or local queues





# TODO 

>[!TODO]
>- [x] Scheduling policies
>- [x] FCFS scheduling policy or non-expulsive FIFO
>- [x] SJF scheluding policy (Shortest Job First)
>- [x] Cyclic scheduling policy or Round Robin
>- [x] Priority scheduling policy
>- [x] Scheduling policy for real-time systems
>- [x] POSIX scheduling policy
>- [x] Windows NT scheduling policy
>- [x] Multiprocessor scheduling


