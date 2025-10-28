## 🧠 Introduction to Operating System (OS)

 
An **Operating System (OS)** is a system software that acts as an interface between the user and the computer hardware.  
It manages the hardware resources, runs applications, and provides an environment where users can execute programs easily and efficiently.  
>In simple words, it’s the **bridge between the user and the machine**.  

**Examples:** Windows, Linux, macOS, Android, iOS.


**Operating System (OS)** হলো এমন এক ধরনের **system software**, যা **user** এবং **computer hardware**-এর মধ্যে মধ্যস্থতা (interface) করে।  
এটি কম্পিউটারের হার্ডওয়্যার রিসোর্স পরিচালনা করে, প্রোগ্রাম চালায়, এবং ব্যবহারকারীর জন্য একটি সহজ ও কার্যকর পরিবেশ তৈরি করে।  

<br>

### ⚙️ Main Functions of Operating System  

| 🧩 Function | 🧾 Description (English) |  বাংলা অর্থ |
|-------------|---------------------------|----------------|
| **Process Management** | Manages running programs and allocates CPU time. | প্রোগ্রাম চালানো ও CPU-র সময় বণ্টন নিয়ন্ত্রণ করে। |
| **Memory Management** | Keeps track of memory usage and allocates memory to processes. | মেমরি কে ব্যবহার করছে তা ট্র্যাক করে এবং প্রয়োজনমতো ভাগ করে দেয়। |
| **File Management** | Handles creation, deletion, and access of files. | ফাইল তৈরি, মুছে ফেলা ও অ্যাক্সেস করা নিয়ন্ত্রণ করে। |
| **I/O Management** | Controls input/output devices like keyboard, mouse, printer, etc. | ইনপুট ও আউটপুট ডিভাইসগুলোর কার্যক্রম পরিচালনা করে। |
| **Security & Protection** | Prevents unauthorized access and ensures data safety. | অননুমোদিত প্রবেশ রোধ করে এবং ডেটার নিরাপত্তা নিশ্চিত করে। |
| **Error Handling** | Detects and recovers from system errors. | সিস্টেমে কোনো ত্রুটি হলে তা শনাক্ত করে এবং সমাধান দেয়। |



### 🎯 Why Do We Need an Operating System?

Without an OS, users would have to manually control every hardware operation —  
like memory management, input/output, and file operations — which is **complex and time-consuming**.  
The **Operating System** simplifies this by managing everything automatically.

**In short:**  
>  **OS = Resource Manager + User Interface + Control System**



### ✅ What is a Program?
A program is a set of instructions written in a programming language that defines a specific task or functionality

It is a passive entity, meaning it’s just code stored in memory (it doesn’t perform any task until executed).

এটি নিষ্ক্রিয় (passive) অবস্থায় থাকে — অর্থাৎ শুধু মেমরিতে কোড হিসেবে সংরক্ষিত থাকে, কাজ শুরু করে না যতক্ষণ না এক্সিকিউট করা হয়।

**Example**: A C++ file like main.cpp or a Python file like app.py


### ✅ What is Process
A **process** is a program in execution. It is an active entity that uses CPU and memory to perform a task.  
Each process has its own **memory space**, **program counter**, and **resources**.  


**Process** হলো একটি **চলমান প্রোগ্রাম** — অর্থাৎ যখন কোনো প্রোগ্রাম CPU তে চলতে থাকে, তখন সেটিই process নামে পরিচিত।  


> Each process runs independently.

**Example**: Opening two Chrome windows = two processes of Chrome.

### ✅ What is Thread

A **thread**, on the other hand, is the smallest unit of a process that can be scheduled and executed.  
Multiple threads within the same process share the same memory and resources, but execute independently.

**Thread** হলো process-এর সবচেয়ে ছোট কাজের একক।  
একটি process-এর মধ্যে একাধিক thread থাকতে পারে, এবং তারা একই মেমরি ভাগ করে নেয় কিন্তু স্বাধীনভাবে কাজ করে।


**Example**: A web browser — one thread loads the page, another downloads files, another renders UI.

<br>

### 🔄 Program vs Process vs Thread

| Term | Description (English) | বাংলা অর্থ |
|------|------------------------|-------------|
| **Program** | A passive collection of instructions stored on disk. | ডিস্কে সংরক্ষিত নির্দেশনার একটি স্থির সেট। |
| **Process** | A program in execution (active state). | চলমান প্রোগ্রাম যা CPU ব্যবহার করে কাজ করে। |
| **Thread** | The smallest unit of execution within a process. | Process-এর ভিতরে কাজের সবচেয়ে ছোট ইউনিট। |



### 🧠 Example 
```c++
#include <iostream>
#include <thread>   // for std::thread

using namespace std;

// Function that will run as a thread
void task() {
    cout << "Thread is running!" << endl;
}

int main() {
    // Create a thread and run the 'task' function
    thread t1(task);

    // Wait for the thread to finish
    t1.join();

    cout << "Main process completed." << endl;

    return 0;
}

```

### Output:
```
Thread is running!
Main process completed.
```


### 🧩 Explanation

- std::thread হল C++11 এ introduce করা class, যা দিয়ে thread তৈরি করা হয়।
- thread t1(task); → task() ফাংশনটি নতুন থ্রেডে রান হবে।
- t1.join(); → main thread অপেক্ষা করবে যতক্ষণ না t1 শেষ হয়।
- শেষে "Main process completed." প্রিন্ট হবে।


### 🧩 Process States

A process goes through different states during its lifetime:

| State | Description |
|------|--------------|
| **New** | OProcess is being created. |
| **Ready** | Waiting to be assigned to CPU. |
| **Running** | Currently using CPU.|
| **Waiting/Blocked** | Waiting for I/O or event.|
| **Terminated** |Process has finished execution. |




### 🧭 Process State Diagram
```
        +-------+
        |  New  |
        +---+---+
            |
            v
        +---+---+
        | Ready |
        +---+---+
            |
            v
        +---+---+
        |Running|
        +---+---+
         ^   |
         |   v
   +-----+   +------+
   |Waiting|        |
   +------+         |
         \__________/
             ↓
        +----------+
        |Terminated|
        +----------+

```

### 🧩 Process vs Thread (Comparison Table)


Process এবং Thread কম্পিউটার সিস্টেমে গুরুত্বপূর্ণ ধারণা। নিচের table এ তাদের প্রধান পার্থক্য দেখানো হলো:

| Feature        | Process                                                    | Thread                                                   |
|----------------|------------------------------------------------------------|----------------------------------------------------------|
| **Definition** | A program in execution with its own memory and resources. | The smallest unit of a process that can run independently. |
| **Dependency** | Independent of other processes.                            | Depends on the parent process.                           |
| **Memory Usage** | Has separate memory space (high memory use).            | Shares memory with other threads (low memory use).       |
| **Communication** | Requires Inter-Process Communication (IPC).            | Communicates easily through shared memory.              |
| **Creation Time** | Takes more time to create.                               | Faster to create.                                        |
| **Crash Impact** | If one process crashes, it doesn’t affect others.       | If one thread crashes, it may affect the whole process. |
| **CPU Switching** | More overhead (context switching is costly).            | Less overhead (context switching is faster).            |
| **Example**    | Running two Chrome windows.                                | Two Chrome tabs loading pages simultaneously.           |

<br>

### 🧩 সহজভাবে বোঝার জন্য

- **Process**: সম্পূর্ণ একটি app instance  
  - উদাহরণ: Chrome এর দুটি আলাদা window খোলা।  
- **Thread**: সেই app এর sub-task  
  - উদাহরণ: Chrome এর প্রতিটা tab আলাদা thread এ চলে।  




### 🔹 Multithreading

**Multithreading** is the ability of a CPU or a single process to **execute multiple threads simultaneously**.

 It helps in performing multiple tasks at the same time, improving performance and responsiveness.

**Example**: In a browser — one thread handles UI, another plays video, another downloads files — all together.

**Multithreading** হলো এমন একটি কৌশল যেখানে একটি process-এর ভেতরে একাধিক thread একসাথে কাজ করে।
 এতে performance ও responsiveness বৃদ্ধি পায় কারণ একই সময়ে একাধিক কাজ সম্পন্ন হয়।



### 🔹 Advantages of Multithreading

Multithreading allows multiple threads to run concurrently within a single process. Below are the main advantages:

| Advantage                | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Faster Execution**      | Multiple tasks run simultaneously, reducing total execution time.          |
| **Better Resource Utilization** | Threads share memory & resources efficiently.                           |
| **Responsiveness**        | Application remains responsive even if one thread is blocked.              |
| **Lower Overhead**        | Thread creation & context switching is lighter than process creation.      |


<br>

### 🔹 Example in C++ (Multithreading)
```c++
#include <iostream>
#include <thread>

using namespace std;

void task1() {
    cout << "Thread 1 is running!" << endl;
}

void task2() {
    cout << "Thread 2 is running!" << endl;
}

int main() {
    thread t1(task1);
    thread t2(task2);

    // Wait for threads to finish
    t1.join();
    t2.join();

    cout << "Main process completed." << endl;
    return 0;
}

```
Output:
```
Thread 1 is running!
Thread 2 is running!
Main process completed.
```

### 🔹 Key Points

- **Single Process, Multiple Threads**: এক process-এর মধ্যে অনেক thread থাকতে পারে।

- **Shared Memory**: Threads একই memory share করে।

- **Independent Execution**: প্রতিটি thread আলাদাভাবে কাজ করতে পারে।

- **Use Cases**: Web servers, GUI applications, real-time simulations, parallel computation।

<br>

### 🔹 Q&A

### 🔹What is multithreading?
> Running multiple threads of a process concurrently.

### 🔹Difference between multithreading and multiprocessing?
> Multithreading = multiple threads in same process, shared memory.
> Multiprocessing = multiple processes, separate memory.

### 🔹Advantages of multithreading?
> Faster execution, better resource utilization, responsive programs, lower overhead.



<br>


### ⚙️ What is Thrashing

**Thrashing** is a condition in an operating system where the system spends an excessive amount of time swapping pages between main memory (RAM) and secondary storage (like a hard disk) instead of performing useful work, leading to severe performance degradation.

When the system continuously moves data between **RAM** and **disk (swap space)** due to insufficient physical memory, the CPU becomes busy doing memory management instead of actual processing.

This makes the system **very slow** and **unresponsive**.


<br>

**Thrashing** হচ্ছে এমন একটি অবস্থা যেখানে কম্পিউটারের **RAM-এর জায়গা কম থাকার কারণে**  
Operating System বারবার ডেটা **RAM থেকে ডিস্কে (swap area)** পাঠায় এবং আবার ফিরিয়ে আনে।

🧩 **ফলাফল:**  
CPU প্রোগ্রাম চালানোর চেয়ে বেশি সময় ব্যয় করে **মেমরি ম্যানেজমেন্টে (page swapping)**,  
যার কারণে সিস্টেম খুব ধীরে চলে বা **হ্যাং** করে।



### 🧠 Example (Easy to Imagine)

ধরো, তোমার কম্পিউটারে **4 GB RAM** আছে।  
তুমি একসাথে **Chrome, VS Code, Photoshop, এবং একটা বড় গেম** চালাচ্ছো 🎮  

👉 তখন OS বারবার data load করছে —  
একটা প্রোগ্রামের data RAM-এ দিচ্ছে, অন্যটারটা ডিস্কে পাঠাচ্ছে।  
এই **swap in/out** চলতে থাকে বারবার —  
ফলে CPU শুধু data shuffle করতে ব্যস্ত, **আসল কাজ করতে পারছে না**।  

➡️ এই অবস্থাই **Thrashing**।

<br>

### 🩹 Solutions / Prevention

| 🧰 Solution | 📝 Description |
|-------------|----------------|
| **Reduce the degree of multiprogramming** | Run fewer programs at a time. |
| **Add more RAM** | Increase physical memory to reduce swapping. |
| **Use better page replacement algorithms** | Example: **LRU (Least Recently Used)** algorithm helps reduce unnecessary swapping. |
| **Adjust system workload** | Distribute tasks or delay heavy programs to balance memory load. |



📚 **Summary:**  
Thrashing occurs when a system is overwhelmed by memory swapping.  
It slows performance drastically, but can be prevented by managing memory efficiently and keeping the system workload balanced.



<br>


### 📘 What is Paging?


**Paging** is a memory management technique used by the **Operating System** to store and manage processes in memory efficiently.  
In this system, both the **physical memory (RAM)** and **logical memory (process)** are divided into fixed-size blocks —  
- 👉 **Pages** (for process memory)  
- 👉 **Frames** (for physical memory)

When a process is executed, its pages are loaded into available frames in the physical memory.  

🎯 **Goal:** To avoid memory fragmentation and make memory allocation easier.


<br>

**Paging** হলো একটি **Memory Management Technique**,  
যেখানে প্রোগ্রাম (**Logical Memory**) এবং **RAM** (**Physical Memory**) —  
দুটোকেই সমান আকারের ছোট ছোট অংশে ভাগ করা হয়।  

- প্রোগ্রামের প্রতিটি অংশকে বলা হয় **Page**  
- RAM-এর প্রতিটি অংশকে বলা হয় **Frame**  

OS যখন কোনো প্রোগ্রাম রান করে, তখন ওই প্রোগ্রামের কিছু **page** নিয়ে **RAM**-এর **frame**-এ রাখে।  
এভাবে প্রোগ্রামটি ছোট ছোট টুকরায় RAM-এ লোড হয়।



### 🧩 Visualization (Diagram Style)

```
📦 Process (Logical Memory)
 ------------------------
 | Page 1 | Page 2 | Page 3 | Page 4 |
 ------------------------

💾 Physical Memory (RAM)
 ------------------------
 | Frame 5 | Frame 8 | Frame 2 | Frame 9 |
 ------------------------

➡️ Page 1 → Frame 5  
➡️ Page 2 → Frame 8  
➡️ Page 3 → Frame 2  
➡️ Page 4 → Frame 9
```
OS keeps a “page table” — that maps which page is in which frame

---

### 📘 What is a Page Fault?

A **Page Fault** occurs when a program tries to access a page that is **not currently in RAM**.  
Since that page is stored on the **disk (secondary storage)**, the **Operating System** must load it into RAM before continuing execution.  

🧩 **In short:**  
`Page Fault = Page not in memory → OS loads it from disk`


**Page Fault** ঘটে যখন কোনো প্রোগ্রাম এমন একটি **page** অ্যাক্সেস করতে চায় যা বর্তমানে **RAM**-এ নেই।  
তখন **Operating System** সেটি **secondary storage (যেমন Hard Disk)** থেকে এনে **RAM**-এ লোড করে।  
এতে কিছুটা সময় লাগে, কারণ **disk access** হলো **RAM**-এর চেয়ে অনেক ধীর।

<br>

### 🔁 Page Fault Handling Steps (ধাপে ধাপে কী ঘটে)

1. 🧠 **CPU** tries to access a page  
2. 🧾 **OS checks** — is that page in RAM?  
3. ❌ If not found → a **Page Fault** occurs  
4. ⏸️ **OS pauses** the process  
5. 💾 **OS loads** the required page from **Disk → RAM**  
6. 🗂️ **Page Table** gets updated  
7. ▶️ **Process resumes** execution  



### ⚡ Visualization

```
🧠 CPU → needs Page 4
📋 OS checks Page Table ❌ (not in RAM)
💾 Load Page 4 from Disk → RAM ✅
🔁 Update Page Table & Resume Execution
```

### 🚨 Relationship Between Paging, Page Fault & Thrashing

|  **Concept** |  **Description** |
|----------------|--------------------|
| **Paging** | Divides memory into pages and frames. |
| **Page Fault** | Happens when a page is not in RAM and must be fetched from disk. |
| **Thrashing** | Occurs when page faults happen too frequently, making the CPU busy swapping pages. |



### 🧩 In short:
**Too many page faults → Thrashing → System slowdown**



### 💡 Shortcut to Remember:
- 🧱 **Paging** → Divide memory  
- 🚫 **Page Fault** → Page missing in RAM  
- 🔁 **Thrashing** → Too many page faults




---


### 📘 What is Segmentation?

Segmentation is a **memory management technique** in which a program is divided into **variable-sized parts** called **segments**.  
Each segment represents a **logical unit** of the program — like functions, arrays, or data structures.  

Unlike paging (where all blocks are of equal size),  
👉 in segmentation, each segment has a **different size** depending on the program’s structure.

**Example:**  
A program may have —  
- Code segment  
- Data segment  
- Stack segment  
- Heap segment  



Segmentation হলো এমন একটি **মেমরি ম্যানেজমেন্ট টেকনিক**,  
যেখানে প্রোগ্রামকে **ভিন্ন ভিন্ন আকারের অংশে (segments)** ভাগ করা হয়।  
প্রতিটি segment হলো প্রোগ্রামের একটি **লজিক্যাল অংশ** — যেমন code, data, stack ইত্যাদি।  
👉 Paging-এর মতো সব অংশ সমান আকারের নয়,  
প্রতিটি segment-এর আকার প্রোগ্রামের প্রয়োজন অনুযায়ী ভিন্ন হয়।



### 🧩 Visualization (Diagram Style)

```
Program (Logical View)
-----------------------------------
| Code Segment | Data Segment | Stack Segment |
-----------------------------------

Physical Memory (RAM)
-----------------------------------
| Segment 2 | Segment 1 | Segment 3 |
-----------------------------------
```

>OS keeps a Segment Table, which stores each segment’s base address and length.


### ⚙️ Segment Table Example

| Segment | Base Address | Length |
|----------|--------------|--------|
| Code | 1000 | 600 |
| Data | 1600 | 400 |
| Stack | 2000 | 300 |

This tells the OS where each segment starts and how big it is.



### 🧠 Difference Between Paging and Segmentation

|  **Feature** |  **Paging** | **Segmentation** |
|----------------|---------------|---------------------|
| **Basic Idea** | Divides memory into fixed-size blocks (pages). | Divides memory into variable-size blocks (segments). |
| **Block Name** | Pages (process) and Frames (RAM). | Segments (logical parts). |
| **Size** | Fixed for all pages. | Variable, depends on the logical structure. |
| **Type of Division** | Physical memory-based division. | Logical program-based division. |
| **Fragmentation** | May cause internal fragmentation. | May cause external fragmentation. |
| **Address Mapping** | Uses Page Table. | Uses Segment Table. |
| **Example** | Page 1, Page 2, Page 3… | Code segment, Data segment, Stack segment… |
| **Used In** | Virtual memory systems. | Memory management in compilers and OS. |



### 🎯 Key Difference Summary

| **Paging** | **Segmentation** |
|-------------|------------------|
| Breaks memory into equal-sized pages. | Breaks program into logical parts (segments). |
| Concerned with **physical memory**. | Concerned with **program structure**. |
| Easier for **hardware management**. | Easier for **programmers to understand**. |


### 🧠 Example to Remember (Analogy)

### 📖 Think of a Book

| 🧩 **Concept** | 📘 **Explanation** |
|----------------|--------------------|
| **Paging** | Book is divided into equal-sized pages (fixed size). |
| **Segmentation** | Book is divided into chapters (different lengths, logically grouped). |



### 🧾 So,

👉 **Paging** = Fixed-size **physical** division  
👉 **Segmentation** = Variable-size **logical** division  


### ⚡ Shortcut to Remember

🧩 **Paging** → Fixed-size, *physical*  
🧠 **Segmentation** → Variable-size, *logical*












✅ **Next Topic:** [Process and Threads →](./02_process_and_threads.md)
