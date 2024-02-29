
# Review of Concurrent Programming concepts

- **Concurrency**: Simultaneous execution of tasks
- **Parallelism $\rightarrow$ real concurrency**: Process execution performed on different cores
- **Apparent concurrency**: Concurrency simulated. Process exists simultaneously and their execution time is interleaved. A model with a single processor

## Types of concurrent processes

**Independent**
- Run without requiring the assistance or cooperation of other processes
- Processes executed independently of one another
**Cooperating**:
- Designed to work together in an activity
- Must be able to communicate and interact among them

## Interaction among processes

**Share or compete** for access to a resource
They **communicate or synchronize** to achieve a common goal
![[Pasted image 20240222151312.png]]

## Concurrency problems

- **Race Conditions**: The final result of the execution of several concurrent processes depends on the execution order
- **Deadlock**: permanent blockade of several processes competing for resources or that need to synchronize with each other

### Race conditions 

```C
void partial_addition(int from, until){
	for(i = from; i <= until; i++){
		res = total; // get the valuke of total
		res+=i; // calculate the new value for total
		total=res; // update the value of total
	}
}

int main(){
	pthread_create(&tid[0], NULL, partial_addition,(void *) a1);
	pthread_create(&tid[1], NULL, partial_addition,(void *) a2);
	pthread_join(tid[0],NULL);
	pthread_join(tid[1],NULL);
	
	printf("The final sum is: %d\n", total);
}
```

![[Pasted image 20240222151858.png]]
Processor can be switched in between any two instructions. The final result is not predictable

**Solution:** Execution the critical section in **mutual exclusion**

**Critical section:** Fragment of code that accesses to shared resources, when it's essential to have **exclusive** access to resources

## Synchronization Mechanisms

![[Pasted image 20240222152222.png]]
First attempts to solve mutual exclusion problem were done without special tools. Dekker's algorithm, Peterson's, Lamport's are solutions that implied busy waiting. We need some special tools.
# OS role in concurrency management

## Concurrency inside the OS

The OS itself is a concurrent program. If an interrupt occurs when the OS is executing , perhaps some OS data are leaved in an inconsistent state. One solution is to disable interrupts when the OS is executing code, making the whole OS a critical section, but this solution is not optimal
The solution is to implement the OS as a *re-entrant kernel*. Therefore, the OS can be execution concurrently several execution paths

**How is synchronization included in a program?**
- Using language libraries/constructions
- Using OS calls to use primitive synchronization systems
**In the end, the OS is the one responsible for providing mechanisms for**
- Synchronization
- Communication

![[Pasted image 20240222153201.png]]

# Synchronization mechanisms

## Semaphores

Structure with three atomic operations defined: *Initialization*, *P* and **V**

>[!Note]
>Also used **wait(s)** and **signal(s)** instead of P(s) and V(s) respectively
>**No busy waiting.** The OS manages a queue of blocked processes

All operations are atomic:
```pseudocode
wait(s) {
	s = s -1;
	if(s < 0)
		block on s;
}

signal(s){
	s = s + 1;
	if (s <= 0)
		block on s
}
```

The OS implements these operations and offers them as a service

**Utility**:

- **Solution to the critical section on mutual exclusion** (*Initializing S to 1*)
- **Limiting the number of processes or threads concurrently accessing a critical section** (control units of a resource being used simultaneously) (*Initializing S to the number of resources*)
- **Synchronization**
![[Pasted image 20240222154222.png]]

## Mutex

Similar to a semaphore initialized with a value 1. It's only used from mutual exclusion on critical sections.
Operations:
- Lock()
- Unlock()

```pseudocode
lock(m);
	<critical section>
unlock(m);
```

## Conditional variables

Synchronization variable associated with a mutex, used when in a critical section we need to wait for some other condition. It blocks the thread until the condition is met.
- When is blocked then the mutex is released
- When the condition becomes TRUE the sleeping are awaken (they compete again for the mutex)

Operations:
- Lock(), unlock() for the mutex
- c_wait(\<variable>, \<mutex>)
- c_signal(\<variable>)

```pseudocode
lock(m);
	<critical section>
	while condition == FALSE {
		c_wait(c, m);
	}
	<rest of critical section>
unlock(m);


lock(m);
	<critical section>
	condition = TRUE;
	c_signal(c);
unlock(m);
```

## Signals

**Sending signals between processes**:
- A process may get locked (sleep) until it receives a signal (**pause** call)
- A process can awake another sending a signal (**kill** call)

**Considerations about signals**:
- A process may receive signals even if it not is waiting for them (are asynchronous)
- Signals are not queued.
- Signals may cause race conditions
# Communication mechanisms

![[Pasted image 20240222160929.png]]

## Files

They can be used for data sharing by several processes. They're easy to use. The communication is based on read and write operations.
They can communicate a potentially unlimited number of processes
**Drawback**:  They're inefficient, being slow operations

## Pipes

They're used in POSIX both as communication and synchronization mechanism. You use the same calls as with files to read and write. Both operations are atomic. 
They're a FIFO file. If a process tries to read from an empty pipe, the OS sleeps the process until the data is available.
Same the other way back, is you try to write on a full pipe, the process will sleep until there is room.
They can be used by multiple processes, either reading or writing

## Messages 

- To communicate processes on different machines
- Processes send and receive messages to communicate and synchronize
- Sockets is an implementation widely used
It uses two basic operations: 
- *send*(destination, message)
- *receive*(source, message)

Types of Communication:
- **Synchronous** (blocking sending and receiving): sender sleeps until the recipient receives the message. The receiver sleeps is the message has not arrived
- **Synchronous intermediate** (non-blocking sending and blocking receiving) the sender does not sleep but the receiver is blocked until it receives the message
- **Asynchronous** (non-blocking send and receive): Nobody waits

**Communication modes**:
- **Direct communication**: Message sending to the process
- **Indirect communication**: Messages sending to an intermediate structure form which the process takes it up
	- Messages queues or mailboxes
	- Ports

>[!Message queues]
>The source and destination identifies an intermediate entity: a mailbox. There may be multiple senders and multiple receivers

>[!Ports]
>Specific case of a mailbox, where there's only one receiver, there may be multiple senders. The port typically belongs to the receiving process

![[Pasted image 20240229175737.png]]

## Shared memory

It's used to communicate processes within the same machine. The OS allows multiple processes to access the same memory via specific system calls for shared memory creation.
Processes can use this memory area to leave date that must be accessible by all. All threads in the same process share memory without OS intervention
# Deadlock

>[!Definition]
>Permanent blockade of several processes competing for resources or that need ro synchronize with each other

Deadlock is an anomaly that occurs when a process is waiting for an event that **cannot** happen.
![[Pasted image 20240229203117.png]]

- **Exclusive** use of resources shared by multiple processes. There're usually sets of processes or threads involved
- Not to be confused with *starvation* or *indefinite postponement*, that occurs due to poor allocation **policy**

## Examples

**With just one process:**
This process is waiting for an event that will not happen (*sleep until 12:00 January 1, 2000*)

**With two processes:**
Process 1:
```pseudocode
Request 80 KB
...
Request 60 KB
...
Release 140 KB
```

Process 2:
```pseudocode
Request 70 KB
...
Request 80 KB
...
Release 150 KB
```

Both of them will be blocked if the first request of each process has been attended

## Treatment

4 strategies:
- Prevention, by negating one of the four conditions
- Dynamic avoidance by careful resource allocation
- Detection and recovery
- Ignore the problem

>[!Important]
>Read chapter 6 of the textbook for more info

