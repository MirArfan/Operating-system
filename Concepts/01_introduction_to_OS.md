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

## 🧠 Types of Operating System (OS)


### 1. 🗂️ Batch Operating System

#### 👉 Definition 
In a **Batch Operating System**, similar jobs are collected together and executed in batches, without user interaction during execution.

#### 📝 
**Batch Operating System** এ একই ধরনের কাজগুলো (jobs) একত্র করে **batch আকারে execute** করা হয়।  
ব্যবহারকারী সরাসরি কম্পিউটারের সাথে যোগাযোগ করে না — সব কাজ একসাথে queue তে জমা হয়, তারপর একের পর এক চলে।

#### ⚙️ Working Principle
- User submits jobs to an operator.  
- Operator groups similar jobs.  
- OS executes them sequentially (one batch after another).

#### ✅ Advantages
- CPU utilization is high.  
- Ideal for long and repetitive jobs.

#### ❌ Disadvantages
- No user interaction during execution.  
- Debugging errors is difficult.

#### 📘 Examples
Payroll system, Bank cheque processing, Billing systems.

---

### 2. 💻 Multiprogramming Operating System

#### 👉 Definition (English)
A **Multiprogramming OS** allows multiple programs to reside in main memory at the same time, and the CPU switches between them to keep itself busy.

#### 📝 
**Multiprogramming OS** এ একাধিক প্রোগ্রাম একসাথে **main memory** তে লোড থাকে।  
CPU কোনো প্রোগ্রাম **I/O এর জন্য অপেক্ষা করলে**, অন্য প্রোগ্রাম চালায় — ফলে CPU কখনো idle থাকে না।

#### ⚙️ Working Principle
- Multiple programs are kept in memory.  
- When one waits for I/O, CPU executes another.  
- Increases CPU utilization.

#### ✅ Advantages
- Efficient use of CPU.  
- Faster execution compared to Batch OS.

#### ❌ Disadvantages
- Complex memory management.  
- Difficult to handle errors.

#### 📘 Examples
IBM OS/360, UNIX (early versions).

---

### 3. ⏱️ Real-Time Operating System (RTOS)

#### 👉 Definition 
A **Real-Time OS** processes data immediately and responds within a specific time limit.

#### 📝 
**Real-Time OS** এমন একটি Operating System যা কোনো event ঘটার সাথে সাথেই **fixed time limit** এর মধ্যে response দেয়।  
এটা সাধারণত **critical systems** এ ব্যবহার হয় (যেমন flight control, medical system)।

#### ⚙️ Types
- **Hard Real-Time OS:** Strict time constraint (e.g., Flight control).  
- **Soft Real-Time OS:** Slight delay acceptable (e.g., Multimedia system).

#### ✅ Advantages
- Predictable and consistent response.  
- High reliability.

#### ❌ Disadvantages
- Complex system design.  
- Limited multitasking ability.

#### 📘 Examples
RTLinux, QNX, VxWorks.

---

### 4. 🌐 Distributed Operating System

#### 👉 Definition 
A **Distributed OS** manages a group of independent computers (nodes) connected via a network and makes them appear as a single system to users.

#### 📝 
**Distributed OS** অনেকগুলো কম্পিউটারকে (nodes) network এর মাধ্যমে সংযুক্ত করে এমনভাবে resource share করে  
যেন পুরো সিস্টেমটিকে **একটাই বড় কম্পিউটার** মনে হয়।

#### ⚙️ Working Principle
- Each node runs part of the OS.  
- Communication via message passing.  
- Provides shared access to files, printers, etc.

#### ✅ Advantages
- Load balancing.  
- Fault tolerance (one node fails, others work).

#### ❌ Disadvantages
- Complex design & maintenance.  
- Security management is harder.

#### 📘 Examples
Amoeba, LOCUS, Chorus, Inferno.

---

### 5. 🔌 Embedded Operating System

#### 👉 Definition 
An **Embedded OS** is designed to operate on small devices with limited hardware resources, often dedicated to specific functions.

#### 📝 
**Embedded OS** ছোট এবং নির্দিষ্ট কাজের জন্য ব্যবহৃত ডিভাইসের জন্য তৈরি হয়, যেমন —  
washing machine, ATM, smart watch, router ইত্যাদি।

#### ⚙️ Characteristics
- Lightweight and fast.  
- Works with limited memory and CPU.  
- Real-time performance.

#### ✅ Advantages
- Reliable and efficient.  
- Uses minimal resources.

#### ❌ Disadvantages
- Hard to upgrade or modify.  
- Limited user interface.

#### 📘 Examples
Windows CE, Embedded Linux, VxWorks, Android Things.

---

### 🧾 Summary Table

| Type of OS | Key Feature | Example |
|-------------|-------------|----------|
| Batch OS | Executes jobs in batches | Payroll System |
| Multiprogramming OS | Multiple programs in memory | IBM OS/360 |
| Real-Time OS | Immediate response | RTLinux |
| Distributed OS | Connected systems act as one | Amoeba |
| Embedded OS | Runs on small devices | Android Things |

---




# 🗂️ Batch Operating System (ব্যাচ অপারেটিং সিস্টেম)

## 🧩 Definition (সংজ্ঞা)

**English:**  
A **Batch Operating System** is one of the earliest types of OS, where similar jobs are grouped together into batches and executed one after another without any user interaction during execution.

**বাংলায়:**  
Batch Operating System হলো প্রাচীনতম OS গুলোর একটি,  
যেখানে একই ধরনের কাজ (jobs) একত্র করে batch আকারে একসাথে চালানো হয়।  
প্রোগ্রাম চলার সময় ব্যবহারকারীর সরাসরি কোনো ইনপুট বা ইন্টারঅ্যাকশন থাকে না।

---

## ⚙️ How It Works (কাজ করার প্রক্রিয়া)

**English (Steps):**
1. Users prepare their jobs (programs + data) and submit them to an operator.  
2. The operator collects similar types of jobs and forms a batch.  
3. The batch is then loaded into the system and executed sequentially (one after another).  
4. Once one job finishes, the next one in the batch begins.

**বাংলায় ধাপে ধাপে:**
1. ব্যবহারকারী তাদের কাজ (program + data) তৈরি করে অপারেটরকে দেয়।  
2. অপারেটর একই ধরনের কাজগুলো একত্র করে একটি batch বানায়।  
3. ব্যাচটি সিস্টেমে লোড হয় এবং একটির পর একটি কাজ চলে।  
4. একটি কাজ শেষ হলে পরের কাজটি শুরু হয়।

---

## 🧮 Example Scenario

| Job  | Task                | Arrival | Execution Order |
|------|---------------------|----------|-----------------|
| Job1 | Payroll calculation | 0        | 1st             |
| Job2 | Salary report       | 1        | 2nd             |
| Job3 | Tax calculation     | 2        | 3rd             |

🧠 All jobs are executed **one after another**, without waiting for user input.

---

## 📈 Performance Metric (দক্ষতার পরিমাপ)

Batch systems are measured by **Throughput**,  
➡️ i.e., how many jobs are completed in a given period of time.  

**বাংলায়:**  
নির্দিষ্ট সময়ের মধ্যে কতগুলো কাজ শেষ হচ্ছে — এটিই **থ্রুপুট (Throughput)**।

---

## ✅ Advantages (সুবিধা)

- 🧮 **High throughput:** অনেক কাজ একসাথে করা যায়।  
- ⚙️ **Automatic execution:** ব্যবহারকারীর উপস্থিতি ছাড়াই কাজ চলে।  
- 🔁 **Good for repetitive jobs:** যেমন payroll, billing, data processing।  
- 🧠 **Efficient resource utilization:** CPU idle থাকে না।

---

## ❌ Disadvantages (অসুবিধা)

- 🚫 **No real-time interaction:** কাজ শুরু হলে পরিবর্তন করা যায় না।  
- 🪲 **Debugging is difficult:** Error ধরা কঠিন কারণ কাজ একসাথে চলে।  
- 🕓 **High turnaround time:** সব কাজ শেষ না হওয়া পর্যন্ত output পাওয়া যায় না।  
- ⚖️ **No priority:** আগে দেওয়া কাজ আগে চলে, সময় অনুযায়ী নয়।

---

### 🧰 Use Cases (ব্যবহার ক্ষেত্র)

| Use Case | Example |
|-----------|----------|
| Payroll Processing | Employee salary calculation |
| Data Processing | Banking data, statistics |
| Report Generation | Monthly or yearly reports |

---

### 🖥️ Examples of Batch Operating Systems

- IBM’s Mainframe OS (e.g., **IBM z/OS**)  
- **Early UNIX systems**  
- **Microsoft DOS** (when used in batch scripts)

---

### 💬 In Interview (How to Explain)

**English:**  
🗣️ "A Batch Operating System is one of the earliest OS types where similar jobs are grouped into batches and executed sequentially without user interaction. It’s mainly used for large data processing tasks like payroll, billing, or reports. Its main advantage is high throughput, but it lacks interactivity and has high turnaround time."

**বাংলায়:**  
“Batch Operating System হলো এমন একটি সিস্টেম যেখানে একই ধরনের কাজগুলো একত্র করে একসাথে চালানো হয়, ব্যবহারকারীর সরাসরি কোনো ভূমিকা থাকে না। এটা সাধারণত বড় ডেটা প্রক্রিয়াকরণের জন্য ব্যবহৃত হয়, যেমন পেরোল বা রিপোর্ট তৈরি।”

---

# 🖥️ Multiprogramming & Multitasking Operating Systems

---

## ⚙️ Multiprogramming Operating System

### 🔸 English Explanation:
A **Multiprogramming Operating System** allows multiple programs to be loaded into memory at the same time.  
However, only **one program uses the CPU at a time** — when one program is waiting for I/O operations (like reading from disk), the CPU switches to another program.

✅ **Goal:** To increase CPU utilization and reduce idle time.

🧩 **Example:** UNIX, Linux, Windows NT, etc.

---

### 🔹 Bangla Explanation:
**Multiprogramming OS** এমন একটি সিস্টেম যেখানে একাধিক প্রোগ্রাম মেমরিতে একসাথে রাখা যায়।  
তবে একই সময়ে CPU কেবলমাত্র একটি প্রোগ্রামকে এক্সিকিউট করে।  
যখন একটি প্রোগ্রাম **I/O এর জন্য অপেক্ষা করে**, CPU তখন অন্য প্রোগ্রাম চালু করে।

🎯 **লক্ষ্য:** CPU যেন ফাঁকা না থাকে, অর্থাৎ **CPU utilization বাড়ানো।**

📘 **উদাহরণ:** UNIX, Linux, Windows NT

---

## ⚙️ Multitasking Operating System

### 🔸 English Explanation:
A **Multitasking Operating System** allows multiple tasks (or processes) to be executed apparently at the same time by **switching rapidly** between them.  
Each task gets a small **time slice** of CPU — this switching happens so fast that the user feels all tasks are running simultaneously.

✅ **Goal:** To improve user responsiveness and make efficient use of CPU time.

🧩 **Example:** Windows, macOS, Linux

---

### 🔹 Bangla Explanation:
**Multitasking OS** এমন একটি সিস্টেম যেখানে একাধিক কাজ একই সময়ে চলতে থাকে মনে হয়,  
কারণ CPU খুব দ্রুত এক কাজ থেকে অন্য কাজে **switch** করে।  
প্রতিটি কাজের জন্য CPU থেকে একটি ছোট **time slice** বরাদ্দ করা হয়।

🎯 **লক্ষ্য:** ব্যবহারকারীর জন্য দ্রুত প্রতিক্রিয়া (response) নিশ্চিত করা এবং CPU সময়ের সঠিক ব্যবহার করা।

📘 **উদাহরণ:** Windows, macOS, Linux

---

## ⚖️ Difference Between Multiprogramming and Multitasking

| **Feature** | **Multiprogramming** | **Multitasking** |
|--------------|----------------------|------------------|
| **Definition** | Multiple programs in memory, CPU executes one at a time | Multiple tasks executed apparently simultaneously |
| **CPU Sharing** | CPU switches when one job waits for I/O | CPU switches rapidly between active tasks |
| **Objective** | Increase CPU utilization | Improve user responsiveness |
| **User Interaction** | No direct user interaction | User interacts directly |
| **Examples** | UNIX, Windows NT | Windows, macOS, Linux |

---

💬 **In Short:**  
➡️ Multiprogramming focuses on **CPU utilization**,  
➡️ Multitasking focuses on **user responsiveness**.

---
# ⚙️ Benefits, Challenges & Use Cases of Multiprogramming and Multitasking Operating Systems

---

## 🟢 Benefits (সুবিধাসমূহ)

### 💠 Higher CPU Utilisation (উচ্চ CPU ব্যবহারের হার)
Multiprogramming বা Multitasking OS CPU-কে একাধিক কাজের মধ্যে দ্রুত switch করতে দেয়।  
এর ফলে CPU কখনো ফাঁকা থাকে না, **idle time কমে যায়** এবং **throughput বাড়ে**।

---

### ⚡ Improved Responsiveness (দ্রুত প্রতিক্রিয়া)
একাধিক কাজ একসাথে চলার কারণে ব্যবহারকারীর জন্য সিস্টেম অনেক **responsive** মনে হয়।  
যেমন — **গান শোনা, ফাইল ডাউনলোড, ওয়ার্ড প্রসেসিং** একসাথে করা যায়।

---

### 🧱 Fault Isolation (ত্রুটি পৃথকীকরণ)
প্রতিটি প্রোগ্রাম বা টাস্ক আলাদা memory space এ চলে।  
ফলে একটি প্রোগ্রাম **ক্র্যাশ করলেও অন্যগুলো প্রভাবিত হয় না**, এবং **system stability** বজায় থাকে।

---

### ⚙️ Efficient Use of Hardware (হার্ডওয়্যারের দক্ষ ব্যবহার)
একাধিক প্রোগ্রাম একসাথে হার্ডওয়্যার শেয়ার করে।  
এতে **hardware utilization বাড়ে** এবং কম খরচে **scalable performance** পাওয়া যায়।

---

## 🔴 Challenges and Limitations (চ্যালেঞ্জ ও সীমাবদ্ধতা)

### ⚔️ Resource Contention (রিসোর্স প্রতিযোগিতা)
একাধিক প্রোগ্রাম একই সময়ে CPU, Memory বা I/O device ব্যবহার করতে চাইলে  
**resource starvation** হতে পারে — কোনো প্রোগ্রাম প্রয়োজনীয় রিসোর্স না পেয়ে অপেক্ষা করে।

---

### 🧮 Overhead of Context Switching (Context Switch এর অতিরিক্ত খরচ)
বারবার task পরিবর্তনের সময় CPU registers ও state save/restore করতে হয়।  
এই **context switching** যদি ঘন ঘন হয়, তাহলে **system performance কমে যায়**।

---

### 🔄 Complex Synchronisation (জটিল সিঙ্ক্রোনাইজেশন)
একাধিক প্রোগ্রাম একসাথে shared data ব্যবহার করলে  
**data inconsistency**, **race condition**, বা **deadlock** হতে পারে।

---

### 📈 Scalability Challenges (বড় সিস্টেমে সমস্যা)
হাজার হাজার concurrent task manage করা কঠিন।  
সিস্টেম বড় হলে **performance, reliability, scalability** বজায় রাখা জটিল হয়ে পড়ে।

---

## 🔁 Context Switching (কনটেক্সট সুইচিং)

### 🧩 Definition:
**Context Switching** হলো এমন একটি প্রক্রিয়া যেখানে CPU বর্তমান task-এর state save করে এবং পরবর্তী task-এর state restore করে,  
যাতে CPU একই সময়ে একাধিক কাজ efficiently পরিচালনা করতে পারে।

---

### 🔹 Details:
- এটি CPU registers, memory pointers ইত্যাদি সংরক্ষণ ও পুনরুদ্ধার করে।  
- **Multitasking OS** context switching-এর মাধ্যমে একাধিক task একসাথে চালাতে পারে।  
- ব্যবহারকারীর কাছে মনে হয় যেন সব কাজ **একসাথে চলছে**।

---

## 💼 Use Cases (ব্যবহারের ক্ষেত্র)

| **Use Case** | **Description (বিবরণ)** |
|---------------|--------------------------|
| **User Applications** | একজন ব্যবহারকারী একসাথে গান শুনতে, ডকুমেন্ট লিখতে, এবং ফাইল ডাউনলোড করতে পারেন — OS এই সব কাজকে সুন্দরভাবে manage করে। |
| **Servers (সার্ভার সিস্টেম)** | একটি Web Server একই সময়ে একাধিক ইউজারের request হ্যান্ডেল করতে পারে — Multitasking এর জন্য প্রতিটি ইউজার সময়মতো response পায়। |
| **Background Processes** | যেমন: সিস্টেম আপডেট বা ব্যাকআপ কাজ ব্যাকগ্রাউন্ডে চলতে থাকে, আর ব্যবহারকারী অন্য অ্যাপ্লিকেশন চালাতে পারেন নির্বিঘ্নে। |

---

🧠 **In Short:**  
➡️ Multiprogramming এবং Multitasking OS এর মূল লক্ষ্য — **CPU utilization বৃদ্ধি, দ্রুত প্রতিক্রিয়া, এবং efficient multitasking নিশ্চিত করা।**

---


# ⚙️ Kernel Mode and User Mode (কার্নেল মোড ও ইউজার মোড)

---

## 🧠 Introduction (পরিচিতি)

### 🗣️ English:
In an operating system, **modes** define the level of access that programs or processes have to system resources.  
There are mainly **two modes of operation — Kernel Mode and User Mode**.  
These modes help the OS maintain **security, stability, and process isolation**.

### 🇧🇩 বাংলা:
Operating System-এ “Mode” নির্ধারণ করে একটি প্রোগ্রাম বা প্রসেস সিস্টেম রিসোর্সে কতটুকু অধিকার (access) পাবে।  
দুই ধরনের মোড থাকে — **Kernel Mode** এবং **User Mode**।  
এই দুটি মোড সিস্টেমের **নিরাপত্তা (security)**, **স্থিতিশীলতা (stability)** এবং **process isolation** নিশ্চিত করে।

---
# ⚙️ Kernel in Operating System (কার্নেল কী)

---

## 🧠 Definition (সংজ্ঞা)

### 🗣️ English:
The **Kernel** is the core component of an Operating System that acts as a bridge between hardware and software.  
It manages system resources like CPU, memory, and input/output devices, and ensures that applications can run smoothly without directly accessing hardware.

### 🇧🇩 বাংলা:
**Kernel** হলো Operating System-এর মূল অংশ, যা **হার্ডওয়্যার ও সফটওয়্যারের মাঝে সেতুবন্ধন** হিসেবে কাজ করে।  
এটি CPU, মেমরি, ইনপুট/আউটপুট ডিভাইসসহ সমস্ত সিস্টেম রিসোর্স নিয়ন্ত্রণ করে,  
এবং ইউজার প্রোগ্রামগুলো যেন সরাসরি হার্ডওয়্যার স্পর্শ না করে তবুও কাজ করতে পারে — তা নিশ্চিত করে।

---

## 🧩 Functions of Kernel (Kernel-এর প্রধান কাজ)

| Function | English Explanation | বাংলা ব্যাখ্যা |
|----------|-------------------|----------------|
| Process Management | Manages creation, scheduling, and termination of processes. | প্রসেস তৈরি, সময় নির্ধারণ (scheduling), ও বন্ধ করার কাজ করে। |
| Memory Management | Allocates and deallocates memory space for programs. | প্রোগ্রামের জন্য মেমরি বরাদ্দ ও মুক্ত করার দায়িত্বে থাকে। |
| Device Management | Controls communication between devices and software through device drivers. | ডিভাইস ড্রাইভার ব্যবহার করে সফটওয়্যার ও হার্ডওয়্যারের যোগাযোগ নিয়ন্ত্রণ করে। |
| File Management | Handles file storage, retrieval, and access permissions. | ফাইল সংরক্ষণ, পড়া, লেখা এবং পারমিশন নিয়ন্ত্রণ করে। |
| System Call Handling | Provides an interface for user applications to request OS services. | ইউজার প্রোগ্রামকে OS সার্ভিস ব্যবহার করার পথ দেয় (system call এর মাধ্যমে)। |

---

## ⚙️ How Kernel Works (Kernel কীভাবে কাজ করে)

### 🗣️ English:
When a user program needs hardware access (like reading a file or printing), it cannot do so directly.  
It sends a **system call** to the kernel.  
The kernel performs that action using device drivers, returns the result to the user program, and continues execution.

### 🇧🇩 বাংলা:
যখন কোনো ইউজার প্রোগ্রাম হার্ডওয়্যার অ্যাক্সেস করতে চায় (যেমন ফাইল পড়া বা প্রিন্ট করা),  
সেটি সরাসরি করতে পারে না।  
তখন এটি **system call** এর মাধ্যমে Kernel-কে অনুরোধ করে।  
Kernel কাজটি ডিভাইস ড্রাইভার ব্যবহার করে সম্পন্ন করে, তারপর ফলাফল ইউজার প্রোগ্রামকে দেয়।

### 💡 Example:

```
User Program → System Call → Kernel → Hardware → Kernel → Result → User Program
```

---

## 🧩 Types of Kernel (Kernel-এর প্রকারভেদ)

| Type | Description (English) | বাংলা ব্যাখ্যা |
|------|----------------------|----------------|
| Monolithic Kernel | Entire OS (device drivers, memory management, etc.) runs in one big kernel space. | সব OS অংশ (ড্রাইভার, মেমরি ম্যানেজমেন্ট ইত্যাদি) একই বড় জায়গায় চলে, দ্রুত কিন্তু জটিল। |
| Microkernel | Only essential parts run in kernel space; others run in user space. | শুধু প্রয়োজনীয় অংশ কার্নেলে থাকে, বাকিগুলো ইউজার স্পেসে চলে — নিরাপদ কিন্তু তুলনামূলক ধীর। |
| Hybrid Kernel | Combination of Monolithic and Microkernel. | Monolithic ও Microkernel দুইয়ের সুবিধা মিলিয়ে তৈরি। (যেমন Windows NT, macOS) |
| Nanokernel | Extremely small kernel with minimal functionality. | খুব ছোট আকারের কার্নেল, শুধু মৌলিক ফিচার থাকে। |
| Exokernel | Gives applications direct control over hardware. | অ্যাপ্লিকেশনগুলোকে সরাসরি হার্ডওয়্যার অ্যাক্সেস দেয় (research বা high-performance system-এ ব্যবহৃত)। |

---

## 🧠 Examples of Kernel in Real Systems

| Operating System | Kernel Type |
|-----------------|------------|
| Linux | Monolithic Kernel |
| macOS | Hybrid Kernel |
| Windows | Hybrid Kernel |
| QNX | Microkernel |
| Minix | Microkernel |
| Android | Modified Linux Kernel |

---

## 🧩 Advantages of Having a Kernel

### 🗣️ English:
- Efficient resource management  
- Improved security and isolation  
- Better multitasking and process control  
- Smooth communication between hardware and software  

### 🇧🇩 বাংলা:
- রিসোর্স গুলো কার্যকরভাবে ব্যবহার হয়  
- সিস্টেম নিরাপত্তা ও আলাদা প্রক্রিয়া বজায় থাকে  
- একাধিক কাজ একসাথে করা সহজ হয়  
- হার্ডওয়্যার ও সফটওয়্যার-এর মধ্যে সঠিক যোগাযোগ নিশ্চিত হয়  

---

## ⚠️ If Kernel Fails (যদি Kernel ব্যর্থ হয়)

- If the kernel crashes → the **entire system stops working**  
- বাংলায়: Kernel ক্র্যাশ করলে পুরো সিস্টেম বন্ধ হয়ে যায়, তাই একে OS-এর **“হৃদয়”** বলা হয় ❤️


## 🧩 1. Kernel Mode (কার্নেল মোড)

### 🧠 English Explanation:
**Kernel Mode** is a **privileged mode** where the operating system has **full access** to all hardware and memory.  
All critical system operations — such as:

- Memory management  
- Process scheduling  
- Device control  

— happen in this mode.

If an error occurs in Kernel Mode, it can **crash the entire system** because it runs with high privileges.

### 🇧🇩 বাংলা ব্যাখ্যা:
**Kernel Mode** হলো একটি **উচ্চ-অধিকারসম্পন্ন (privileged)** মোড,  
যেখানে OS-এর সম্পূর্ণ হার্ডওয়্যার ও মেমরি অ্যাক্সেস থাকে।  
সব গুরুত্বপূর্ণ কাজ যেমন:

- মেমরি ম্যানেজমেন্ট  
- প্রসেস শিডিউলিং  
- ডিভাইস কন্ট্রোল  

এই মোডেই সম্পন্ন হয়।  
এই মোডে কোনো ত্রুটি ঘটলে **পুরো সিস্টেম ক্র্যাশ** করতে পারে, কারণ এটি উচ্চ পর্যায়ের এক্সেস নিয়ে কাজ করে।

### 💡 Example:
When the OS executes **system calls** (like `read()`, `write()`, or memory allocation),  
it switches to **Kernel Mode** to perform those actions.

---

## 👤 2. User Mode (ইউজার মোড)

### 🧠 English Explanation:
**User Mode** is a **restricted mode** where user applications run with **limited access** to system resources.  
Programs cannot directly interact with hardware or memory —  
they must **request services** from the OS via **system calls**.

If a program crashes in User Mode, it does **not affect the entire OS**, ensuring safety and stability.

### 🇧🇩 বাংলা ব্যাখ্যা:
**User Mode** হলো একটি **সীমিত ক্ষমতাসম্পন্ন (restricted)** মোড,  
যেখানে সাধারণ ইউজার প্রোগ্রাম চলে।  
এই মোডে প্রোগ্রাম **সরাসরি হার্ডওয়্যার বা মেমরি অ্যাক্সেস করতে পারে না**,  
বরং OS-এর কাছে **system call** এর মাধ্যমে অনুরোধ পাঠায়।

এর ফলে, কোনো ইউজার প্রোগ্রাম ক্র্যাশ করলে **পুরো সিস্টেমে প্রভাব পড়ে না**,  
অর্থাৎ সিস্টেম **নিরাপদ থাকে**।

### 💡 Example:
যখন তুমি কোনো অ্যাপ খুলে Word ডকুমেন্ট লেখো, সেটা **User Mode**-এ চলে।

---

## 🔄 Mode Switching (মোড পরিবর্তন)

### 🧠 English:
When a program in User Mode needs to perform a **system-level task** (like accessing a file or allocating memory),  
it uses a **System Call**, which temporarily switches the CPU from **User Mode → Kernel Mode**,  
executes the required operation, and then **switches back to User Mode**.

### 🇧🇩 বাংলা:
যখন কোনো ইউজার প্রোগ্রাম সিস্টেম-লেভেল কাজ করতে চায় (যেমন ফাইল পড়া, লেখা বা মেমরি বরাদ্দ),  
তখন CPU সাময়িকভাবে **User Mode → Kernel Mode**-এ যায়,  
কাজটি শেষ করে আবার **User Mode**-এ ফিরে আসে।

### ⚙️ Example:
```
User Program → (System Call) → Kernel Mode → Task Done → Back to User Mode
```
---

## 🧾 Comparison Table (তুলনামূলক সারণি)

| **Feature** | **Kernel Mode** | **User Mode** |
|--------------|-----------------|----------------|
| **Access Level** | Full access to system resources | Limited access |
| **Executed By** | Operating System | User Applications |
| **Direct Hardware Access** | ✅ Yes | ❌ No |
| **Privilege Level** | High | Low |
| **Error Impact** | Can crash the whole system | Affects only that program |
| **Examples** | Memory Management, Process Scheduling | Running Chrome, VS Code, Games |

---

## 🧠 Summary (সংক্ষিপ্ত সারাংশ)

- 🔹 **Kernel Mode** = System control, full access  
- 🔹 **User Mode** = User applications, limited access  
- 🔹 **Mode Switching** ensures both **performance** and **protection**

---


# ⚙️ System Calls (সিস্টেম কল)

---

## 🧠 Definition (সংজ্ঞা)

### 🗣️ English:
A **System Call** is an interface provided by the operating system that allows a user program to request services from the kernel.  
It acts as a bridge between **User Mode** and **Kernel Mode**, enabling programs to perform tasks that they cannot execute directly.

### 🇧🇩 বাংলা:
**System Call** হলো একটি বিশেষ ইন্টারফেস যা OS প্রদান করে, যাতে **User Program** Kernel থেকে প্রয়োজনীয় সার্ভিস নিতে পারে।  
এটি **User Mode ↔ Kernel Mode** এর মধ্যে সেতুবন্ধন হিসেবে কাজ করে,  
যার মাধ্যমে প্রোগ্রাম এমন কাজ করতে পারে যা সরাসরি করতে পারবে না।

---

## 🧩 How System Calls Work (কীভাবে কাজ করে)

1. A user program needs a service (e.g., read a file, write data, create a process).  
2. It executes a system call, which triggers a mode switch from **User Mode → Kernel Mode**.  
3. Kernel performs the requested operation using hardware and OS resources.  
4. Result or status is returned to the user program, CPU switches back to **User Mode**.

### 🇧🇩 ধাপে ধাপে:
1. কোনো প্রোগ্রাম সার্ভিস চায় (যেমন ফাইল পড়া বা লেখা, প্রসেস তৈরি করা)।  
2. প্রোগ্রাম **system call** করে, ফলে CPU **User Mode → Kernel Mode** এ চলে যায়।  
3. Kernel কাজটি সম্পন্ন করে।  
4. ফলাফল বা স্ট্যাটাস প্রোগ্রামে ফেরত যায়, CPU আবার **User Mode** এ ফিরে আসে।

### 💡 Diagram:
```
User Program → System Call → Kernel → Hardware/OS → Kernel → Result → User Program
```


---

## 🧩 Types of System Calls (সিস্টেম কলের ধরন)

| Type | English Explanation | বাংলা ব্যাখ্যা |
|------|-------------------|----------------|
| Process Control | Create, terminate, suspend, resume processes | প্রসেস তৈরি, বন্ধ করা, থামানো বা চালু করা |
| File Management | Open, read, write, close files | ফাইল খোলা, পড়া, লেখা, বন্ধ করা |
| Device Management | Request device, release device | ডিভাইস ব্যবহার চাওয়া বা মুক্ত করা |
| Information Maintenance | Get system time, get process info | সিস্টেম সময়, প্রসেসের তথ্য পাওয়া |
| Communication | Send/receive messages between processes | প্রসেসের মধ্যে তথ্য আদান-প্রদান |

---

## 🧠 Examples (উদাহরণ)

| Operation | English | বাংলা |
|-----------|---------|-------|
| File | open(), read(), write(), close() | ফাইল খোলা, পড়া, লেখা, বন্ধ করা |
| Process | fork(), exit(), wait() | নতুন প্রসেস তৈরি, প্রসেস বন্ধ, অপেক্ষা করা |
| Device | ioctl() | ডিভাইস নিয়ন্ত্রণ |
| Info | getpid(), time() | প্রসেস আইডি, সিস্টেম সময় |

---

## ✅ Advantages (সুবিধা)

- Provides safe access to hardware from user programs  
- Ensures security and isolation between processes  
- Enables efficient multitasking and process control  
- Standard interface across different OS platforms  

### 🇧🇩 বাংলা:
- ইউজার প্রোগ্রামের জন্য হার্ডওয়্যারে নিরাপদ অ্যাক্সেস প্রদান  
- প্রসেসগুলোর মধ্যে নিরাপত্তা ও আলাদা রাখে  
- একাধিক কাজ একসাথে করার সুবিধা দেয়  
- বিভিন্ন OS-এ **standard interface** প্রদান করে

---

## ⚠️ Note (মনে রাখার বিষয়)

- User programs cannot access hardware directly → **System Call is mandatory**  
- Each system call triggers **mode switch**, which has small CPU overhead

### 🇧🇩 বাংলা:
- ইউজার প্রোগ্রাম সরাসরি হার্ডওয়্যারে অ্যাক্সেস করতে পারে না → তাই **System Call অপরিহার্য**  
- প্রতিটি system call **mode switch** করে, যার ফলে CPU-তে সামান্য অতিরিক্ত লোড হয়



# ⚙️ Process and Its States (প্রসেস ও এর অবস্থা)

---

## 🧠 Definition of Process (প্রসেসের সংজ্ঞা)

### 🗣️ English:
A **Process** is a program in execution. It is an active entity with a **program counter**, **CPU registers**, **memory**, and **state information**.  
Each process performs a specific task and goes through various states during its lifecycle.

### 🇧🇩 বাংলা:
**প্রসেস** হলো একটি কার্যকরী প্রোগ্রাম যা CPU-তে চলছে।  
প্রসেসের থাকে:

- Program Counter (পরবর্তী instruction কোথা থেকে execute হবে)  
- CPU Registers  
- Memory Allocation  
- State Information  

প্রসেস জীবদ্দশায় বিভিন্ন অবস্থা (states) এর মধ্য দিয়ে যায়।

---

## 🧩 Process States (প্রসেসের অবস্থা)

### 1️⃣ New (নতুন)
- **English:** The process is being created. OS allocates resources but it has not started execution yet.  
- **বাংলা:** প্রসেস তৈরি হচ্ছে। OS কিছু resource বরাদ্দ করে, তবে execution শুরু হয়নি।

### 2️⃣ Ready (প্রস্তুত)
- **English:** The process is loaded into main memory and is waiting for CPU. It is ready to run but CPU is not yet allocated.  
- **বাংলা:** প্রসেস মেমরিতে লোড হয়ে আছে এবং CPU পাওয়ার জন্য অপেক্ষা করছে। Execution শুরু হয়নি, তবে সব resource প্রস্তুত।

### 3️⃣ Running (চলছে)
- **English:** The CPU is currently executing the process instructions. Only one process per CPU runs at a time.  
- **বাংলা:** CPU বর্তমানে প্রসেসটি execute করছে। এক সময়ে এক CPU-তে কেবল একটি প্রসেস চলতে পারে।

### 4️⃣ Waiting / Blocked (অপেক্ষমাণ / ব্লকড)
- **English:** The process cannot continue until some event occurs, such as I/O completion or resource availability.  
- **বাংলা:** প্রসেসটি অপেক্ষা করছে কারণ কিছু event ঘটতে হবে (যেমন: I/O কাজ শেষ হওয়া বা resource পাওয়া)।

### 5️⃣ Terminated / Exit (শেষ / টার্মিনেট)
- **English:** The process has finished execution and is removed from memory. All allocated resources are released.  
- **বাংলা:** প্রসেস execution শেষ করেছে এবং মেমরি থেকে সরানো হয়েছে। বরাদ্দকৃত সমস্ত resource মুক্ত করা হয়।

---

## 🔄 Process State Diagram (প্রসেস স্টেট ডায়াগ্রাম)
sql
Copy code
    +---------+
    |  New    |
    +---------+
         |
         v
    +---------+
    | Ready   | <----+
    +---------+      |
         |           |
         v           |
    +---------+      |
    | Running |      |
    +---------+      |
     |    |          |
     |    v          |
     | Waiting       |
     +---------+     |
         |           |
         +-----------+
         |
         v
     Terminated
sql
Copy code

### 🇧🇩 বাংলা ব্যাখ্যা:
New → Ready → Running → Waiting → Ready (যদি আবার CPU চায়) → Terminated

---

## 🧩 Key Points (মূল বিষয়গুলো)

- A process is dynamic, unlike a program which is static.  
  **বাংলা:** প্রসেস dynamic, প্রোগ্রাম static।

- **Process Control Block (PCB)** contains all information about a process: PID, State, CPU registers, Memory pointers, I/O status.  
  **বাংলা:** PCB-এ থাকে প্রসেসের সব তথ্য: PID, State, CPU registers, Memory pointer, I/O status।

- Only one process per CPU runs at a time in Running state.  
  **বাংলা:** এক সময়ে কেবল একটি প্রসেস CPU-তে চলতে পারে।
  