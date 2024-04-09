
# The File Management System

## Definition

Responsible for the management and organization of files. Manages secondary memory and the file system structure over it. 

## Functions

- **System API**: Receive calls for the File Manager
- **File** management: Locate disk blocks containing files data. Connects logical file image with disk physical image
- **Directory** management: **Locate files** in the directories hierarchy and provides ways of logical **file naming**
- Managing disk free space: **Find free blocks** to allocate new files or free blocks when deleting a file
- Managing disk **block cache** memory
- Provide protection: **access control** to files
- **Connect with I/O management system** to indicate the operation to be performed on the physical disk blocks

# Files

## Basic concept

>[!Definition]
>Abstraction created and managed by the OS to store data in a persistent way. Data collection with a name

**Types:** In the past, there were several different types (Sequences and/or trees of records, direct files, ...). Today, it's a sequence of bytes (In most OS)

## Access Methods

It's how the OS access data in Files

- **Sequential**:
	- Information is processed in a sequential order
	- The basic operations are reading and writing the next position
- **Direct** (by address) (is also a sequential file):
	- Direct access to any logical record
	- Records can be of any type 
	- The most frequently used by the current OS
- **Indexed** (by key) (not in current systems)
	- Files are sequences of records. Every record has a key field
	- A single record can be accessed using the key
	- Indexed and random access files support this kind of access method

## File Characteristics

- **Name**
- **Unique identifier
- **File Type
- **Map file
- **Protection
- **Size
- **Date and Time
- **Control information
- **Owner

The OS saves this information in a **file descriptor**

## Structure and storage

The disk is divided into blocks (physical device block)![[Pasted image 20240404152025.png]]

The files are divided into blocks (logical file blocks). 
Allocation possibilities:
- **Contiguous allocation** (all file blocks are stored in consecutive disk blocks)
- **Non-contiguous allocation** (the file blocks are not stored consecutively on disk). We need a structure that relates logical-physical blocks
### Contiguous Allocation

OS must keep in the file descriptor of every file the **Initial block address** and the **number of blocks of the file**.
If the file needs to grow its size and there's not enough free space after the blocks allocated for the file, it cannot grow and therefore, it should be moved to other blocks
It can provoke disk fragmentation. Compact operation should be performed periodically.
It's only used in devices where files are written only once and are not modified (CD-ROM)

### Non-contiguous Allocation

The blocks belonging to a file do not need to be in contiguous blocks. Disk fragmentation is not a problem form a logical point of view, but it can be a problem for the performance of I/O operations.
To locate the blocks that belong to each file a list with the number of the blocks must be used. This list can be implemented in different ways:
- Using the same data blocks to include a pointer to the next block
- Using a File Allocation Table (FAT)
- Using a table of indexes
- Using a balanced tree of indexes

#### Allocation with linked list in the data blocks

In each data block there's a pointer to the next data block. The file descriptor stores the address of the first block of the file. You have to go through all the previous blocks to get the one you want. The pointer occupies space and it is included in the file

![[Pasted image 20240404153857.png]]

#### Allocation with FAT (File Allocation Table)

The OS manages a table, stored in the disk, with one entry per disk block. The file descriptor stores the address of the first block of the file.
In each FAT entry we store the next physical block. In the last block of a file a EndOfFile mark is stored. To implement a direct access the OS needs to go through the FAT.
Widely used in removable devices because a lot cheap circuity is available.

![[Pasted image 20240404154304.png]]

#### Indexed allocation

Saves all the file block numbers in one contiguous structure called index block, that is a disk block itself. In the i-th table entry there is a physical block number.
There are two types of disk blocks
- Data
- Index (for the index table)

Number of entries in an indexed block:
- Block size / number of bytes of the index
- E.g. = 4K block / 4 Bytes = 1024 entries

![[Pasted image 20240404154651.png]]

>[!Example (Unix File Systems: System V, FFS, ext2 ...)]
>Each file has a table of 13 entries in the i-node. The first 10 entries contain the **first 10** indexes to the first 10 data blocks. 
>
>**Entry 10** contains an index to an index block. This block contains indexes to the following file data blocks
>
>**Entry 11** contains a double indirection: an index to an index block containing block indexes to block indexes that contain fila data blocks
>
>**Entry 12** contains a triple indirection: an index to an index block containing block indexes to block indexes to block indexes that contain data blocks
>

![[Pasted image 20240404155324.png]]

#### Balanced tree indexed allocation

Represents a file structure using balanced trees. Each block contains data pointers to children. The i-node is the root of the tree. Each node can have data and links to other nodes. The search key is the logical number of the block
Used in NTFS, where just the i-node and the leaf nodes contain data, intermediate nodes contain indexes. Direct access by address can be very fast

![[Pasted image 20240404155652.png]]

### Free blocks management

Theo OS has to manage the disk blocks that are free, to be able to assign them when necessary. Some possibilities
- Use a Bit map, with an entry per disk block
- In FAT based systems the same FAT entries can be used to know if  block is free or not
- Use a linked list with the numbers of free blocks

# Directories

## Concept and Structure

User's point of view $\rightarrow$ **Files container**
OS's point of view $\rightarrow$ Object **linking** the file's symbolic name to the OS internal descriptor

**Structure:**
- One or two levels
- Tree
	- Root and internal nodes are Directories and leafs are Files
- Acyclic graph
	- Useful for sharing directories among different users
	- You create links to shared files
## Name and Operations

**Name**
The full file name includes the path from the root to the file and the filename.
Getting the name:
- Absolute Name $\rightarrow$ From the root
- Relative Name $\rightarrow$ From some other subdirectory

**Generic Operations on Directories**
- Create
- Delete
- Open
- Close
- Read
- Change current directory
- Rename
- Move
- Link
## Structure and Storage

**Structure and storage of directories**

- In contiguous files: file attributes, first block number and size
- In FAT files: attributes, first block number and size
- In indexed files: file descriptor identifier
	- Unix SV:
		- file name and i-node number. Attributes are in the i-node.
		- i-nodes can be of files or directories
	- Windows NTFS:
		- File name and some attributes in the directory
		- Root descriptor number (entry of the MFT)(root of the balanced tree)

# The File System

## General Layout of the Disk

Discs are divided into one or more partitions or volumes
- **Partition:** the portion of disc that gives it its own identity and can be manipulated by the OS as an independent entity. (Some OS allow building extended partitions that span multiple disks)
- **File System:** How to organize information on disk in a format understood by the operating system
- For the File Systems definition, the OS provides commands like *format* or *mkfs*
- A block is the minimal **transfer unit** (1 or more sectors)
- A File System (partition) is divided into logical **blocks numbered** form 0 to the maximum in the File System. Currently you can define a **cluster** size (set of blocks that are managed as a logical unit of storage)
- Files are also divided into blocks (of equal size) logically numbered from 0 to the file's maximum
- **Each logical file block is assigned to a logical file system block**
- Block size is relevant as regards
	- **Disk Usage.** Each file has a whole number of blocks
	- **Access speed** (seek and block transfer) 

**Information typically stored on a disk block**

- **Booting information**
	- Allows the boot process of a computer to load a program (usually, but not necessarily, an operating system) stored on the same storage device
- **Metadata about the File System**
	- File System description
		- Block size, maximum number of files, etc
		- Data blocks usage statistics
		- File descriptors
- **Data blocks**
	- Contain data files

## Some examples:

![[Pasted image 20240409153342.png]]

![[Pasted image 20240409153402.png]]

![[Pasted image 20240409153421.png]]

![[Pasted image 20240409153437.png]]

![[Pasted image 20240409153456.png]]

![[Pasted image 20240409153513.png]]

## Structure

Problem of the previous file systems:
- The metadata is grouped at the beginning of the disc
- The search time is greater because the blocks are scattered through the disk
- If metadata is corrupted, the system becomes useless

To solve this problems, other file systems appear
- FFS (Fast File System) and BSD Unix
- EXT2 (extended file system) for Linux

![[Pasted image 20240409153841.png]]

## File System with Journaling

Developed to solve the problem of recovering the FS consistency if any errors occur. In FFS or ext2 file systems we add one extra record for each block group
The system logs all write operations sequentially in a log file (log or journal) (so that it can undo operations) and then write them in the file data blocks
- If rollback it reverses the operations written on the log
- If commit it forgets the log
Operations on data are stored in sequence in this record

# Backup and recovery

Importance of security to prevent data loss problems
- Incidental damage
- Intentional damage
- Errors

**Solutions:**
- Backups
- Redundant storage

## Backups

Total backup $\rightarrow$ Periodically Copy Files yo Other Devices
Incremental backup $\rightarrow$ Only data that has been modified since the last backup is copied

Disadvantages $\rightarrow$ They can take long time, and can force to stop the normal service of the system

## RAID Devices

RAID (*Redundant Array of Independent Disk*) devices use several disks to improve performance and security
It's a technique that uses several disks to work as an only one