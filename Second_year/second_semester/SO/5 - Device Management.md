
# Introduction

**Input-output devices communicate the CPU** with the user, the storage devices and other machines. The input-output managing system:
- Provides an API to facilitate the use  of input/output devices from user programs
- Optimizes their use, allowing them to be shared and improving their performance
- Makes uniform their use, independently of brands/models, virtualizing the devices
- Support hot reconfiguration of the devices

Wide diversity of I/O devices at the levels:
- Address mechanism (port-in, port-out instructions, memory mapped devices)
- Transfer units (block devices, character devices)
- Data representation code (ASCII, UTF-8)
- Transfer mode (controlled by the CPU, using DMA, ...)
- Speed
- "Conversation partner"

![[Pasted image 20240418144412.png]]

# Input / Output hardware

I/O devices consist of two parts:
- **Interface** with the rest of the system. Electronic part (controller), that "talks" to the OS
- **Working part**. It implements the functionality of the device. It can be only electronic or can include mechanical parts

## Hardware controller

![[Pasted image 20240418144729.png]]

OS can access data, address and control registers to:
- Send/receive data
- Send commands
- Read the state of the device

![[Pasted image 20240418144833.png]]

# OS-Device communication

![[Pasted image 20240418145020.png]]

![[Pasted image 20240418145045.png]]

# Input / Output software

## I/O routines

![[Pasted image 20240418150215.png]]


## I/O management modules


**Device-independent handler**
- Receives the request from the file system
- Analyzes the request and produces an IORB (Input Output Request Block)
	- IORB: A data structure with information about the request
		- type of operation
		- memory location
		- number of bytes to be transferred
		- device on which is performed
- Inserts the IORB in request queue associated with the device
- Sends the message to the device-dependent handler signaling a new request (Signal operation on a semaphore)

**Device-dependent handlers**
Server threads dedicated to:
- Wait for a request
- Translate request to controller language and send it to the controller
- Wait until the controller handles the request and finishes it 

**Interruption handler (I/O management routines)**
It works when the processor receives an interrupt from a device. It checks the cause of the interruption and sends massage to the device-dependent handler that caused the interruption to indicate that it can handle another request

## Other mechanisms implemented by the OS

**Buffering**
Mechanism to speed up I/O operations in block devices (typically disks). OS uses a memory area to store a copy of the last blocks accessed by the processes. If any process need to access again one of those blocks there's no need to read it from the disk

**Spooling** (*Simultaneous Peripheral Operations Om.Line*)
This mechanism allows that several processes access simultaneously with a device that cannot be shared (for instance, a printer).
The OS creates a virtual device. When a process needs to execute an output operation, the OS will write the output in the virtual device (a file). When the process "closes" the device, the OS send the file to the real device.

# Device Management Examples

## The clock

### Hardware



