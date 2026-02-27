**Operating System** : An Operating System is system software that manages computer hardware and software resources and provides services to applications. Act as an interface between user and hardware.

**_Functions of Operating System_**

- Memory management
- file management
- process management
- device management
- cpu scheduling

**_Types of operating system_**

- **_Batch Operating System_** : A Batch OS executes jobs in batches without user interaction. Similar jobs are grouped together and executed one by one. The user does not interact with the system during execution.

- **_Time-Sharing Operating System_** : A Time-Sharing OS allows multiple users to use the system simultaneously by sharing CPU time.
  - CPU time is divided into small time slices.
  - Each user gets a chance to execute their task quickly.

- **_Multitasking Operating System_** : A Multitasking OS allows multiple programs to run at the same time.
  - The OS switches CPU between programs rapidly.
  - Gives the illusion of parallel execution.

- **_Multiprocessing Operating System_** : A Multiprocessing OS uses multiple CPUs to execute processes simultaneously.
  - Improves performance and speed.
  - Multiple processors work together.

- **_Multithreading Operating System_** : A Multithreading OS allows multiple threads of a process to run concurrently.
  - Threads are smaller units of a process.
  - Improves efficiency and responsiveness.

- **_Distributed Operating System_** : A Distributed OS manages multiple computers and makes them work like a single system.
  - Resources are shared between multiple machines. User sees it as one system.

- **_Network Operating System_** : A Network OS manages and provides services to computers connected in a network.
  - Allows file sharing, printer sharing, user management.
    example: Windows Server, Linux Server

- **_Real-Time Operating System (RTOS)_**: A Real-Time OS processes data and gives response within a fixed time limit.

---

**Difference between program and process**
Program is a passive entity stored on disk, while process is an active entity executing in memory.

---

**Process and Thread** :

**_Process_** : A Process is a program in execution with its own separate memory space.

- Independent execution unit
- Has its own memory (heap, stack, data)
- Heavyweight

**_Thread_** : A Thread is a lightweight unit of execution inside a process that shares memory with other threads.

- Shares same memory with other threads of same process
- Lightweight
- Faster than process

---

**Process States**

1. New → Process is being created
2. Ready → Waiting for CPU
3. Running → Executing on CPU
4. Waiting (Blocked) → Waiting for I/O
5. Terminated → Finished execution

---

**CPU Scheduling**
CPU Scheduling is the process of selecting which process gets CPU next.
Common Algorithms: FCFS (First Come First Serve), SJF (Shortest Job First), Round Robin, Priority Scheduling.

---

**Context Switching**
Context switching is the process of saving the state of one process and loading the state of another process.

---

**Deadlock**
Deadlock is a situation where two or more processes wait forever for resources held by each other.

---

**Paging**
Paging is a memory management technique that divides memory into fixed-size pages.

- Page → fixed size block
- Frame → physical memory block

---

**Segmentation**
Segmentation divides memory into variable-size segments based on logical divisions.

**Mutex**
Mutex is a locking mechanism that allows only one thread to access a resource at a time.

**Semaphore**
Semaphore is a signaling mechanism that allows multiple threads to access a resource.

---

**Difference between mutex & semaphore**
| Mutex | Semaphore |
| --------------------- | ------------------------ |
| Only 1 thread allowed | Multiple threads allowed |
| Locking mechanism | Signaling mechanism |
| Ownership exists | No ownership |

---

**What is PCB (Process Control Block)**
PCB is a data structure used by OS to store process information. It helps the OS manage and perform context switching.

1. Process ID (PID)
2. Process State
3. Program Counter
4. CPU Registers
5. Memory Management Information
6. CPU Scheduling Information
7. I/O Status Information


