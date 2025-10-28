# ⚙️ CPU Scheduling (CPU শিডিউলিং)

### 🧠 What is CPU Scheduling?


**CPU Scheduling** is the process of deciding **which process** will use the CPU at a particular time.  
Since multiple processes are ready to execute but only **one** CPU is available, the OS must decide which one to run first.

**CPU Scheduling helps achieve:**  
- Maximum CPU utilization  
- Minimum waiting time  
- Fairness among processes  
- Faster response time  


CPU Scheduling হলো সেই প্রক্রিয়া যেখানে অপারেটিং সিস্টেম ঠিক করে কোন প্রসেসটি CPU ব্যবহার করবে এবং কখন করবে।  
কারণ একসাথে অনেক প্রসেস ready থাকে, কিন্তু CPU একটিই।

**এই scheduling-এর উদ্দেশ্য:**  
- CPU-কে সবসময় ব্যস্ত রাখা  
- Waiting time কমানো  
- সব প্রসেসকে ন্যায্য সুযোগ দেওয়া  
- দ্রুত প্রতিক্রিয়া (response time) পাওয়া  

<br>

### 🧩 Types of CPU Scheduling (শিডিউলিং-এর ধরন)

CPU scheduling দুইভাবে ভাগ করা হয়:  

1. **Preemptive Scheduling**  
2. **Non-Preemptive Scheduling**



### ⚔️ 1️⃣ Preemptive Scheduling


In **Preemptive Scheduling**, the CPU can **switch** from one process to another even before the process finishes.  
It’s used for **real-time or interactive** systems where quick response is needed.

**Example:** Round Robin, Shortest Remaining Time First (SRTF), Priority (preemptive)


Preemptive Scheduling-এ CPU কোনো প্রসেস শেষ না হলেও সেটিকে থামিয়ে অন্য প্রসেসে সুইচ করতে পারে।  
এটা মূলত ব্যবহার হয় রিয়েল-টাইম বা ইন্টার‌্যাকটিভ সিস্টেমে, যেখানে দ্রুত প্রতিক্রিয়া দরকার।  

**উদাহরণ:** Round Robin, SRTF, Preemptive Priority

---

### 🧱 2️⃣ Non-Preemptive Scheduling

#### 🔹 English:
In **Non-Preemptive Scheduling**, once a process starts executing, it runs **until completion or it voluntarily releases the CPU.**

**Example:** FCFS (First Come First Serve), SJF (Shortest Job First), Priority (non-preemptive)


Non-Preemptive Scheduling-এ কোনো প্রসেস একবার CPU পেলে,  
তা নিজে শেষ না হওয়া পর্যন্ত CPU অন্য কাউকে দেওয়া হয় না।  

**উদাহরণ:** FCFS, SJF, Non-Preemptive Priority

---

### ⚙️ Common CPU Scheduling Algorithms (জনপ্রিয় অ্যালগরিদমগুলো)

| Algorithm | Type | Description (English) | Description (Bangla) |
|-----------|------|----------------------|---------------------|
| FCFS (First Come First Serve) | Non-Preemptive | The process that comes first gets the CPU first. | যে প্রসেস আগে আসে, সে আগে CPU পায়। |
| SJF (Shortest Job First) | Non-Preemptive | The process with the shortest burst time executes first. | যে প্রসেসের সময় সবচেয়ে কম লাগে, সেটা আগে চলে। |
| SRTF (Shortest Remaining Time First) | Preemptive | The process with the least remaining time executes first. | যার বাকি সময় সবচেয়ে কম, সেটাকে আগে CPU দেওয়া হয়। |
| Priority Scheduling | Both | Each process is assigned a priority; highest priority runs first. | প্রতিটি প্রসেসের একটা প্রাধান্য থাকে, বেশি প্রাধান্য পেলে আগে চলে। |
| Round Robin (RR) | Preemptive | Each process gets CPU for a fixed time slice (quantum). | প্রতিটি প্রসেস নির্দিষ্ট সময় (quantum) CPU ব্যবহার করে। |

---


### ⏱️ CPU Scheduling Terms

| Term | English Meaning | Formula / Note |
|------|----------------|----------------|
| Arrival Time (AT) | The time at which a process enters the ready queue.  | Input to scheduling algorithm |
| Burst Time (BT) | The total CPU time required by a process for execution. |  CPU execution time |
| Completion Time (CT) | The time at which a process finishes execution. | CT = Finish time |
| Turnaround Time (TAT) | Total time spent by a process from arrival to completion. | TAT = CT - AT |
| Waiting Time (WT) | Total time a process spends waiting in the ready queue.  | WT = TAT - BT |
| Response Time (RT) | Time from process arrival to first execution on CPU.  | RT = First CPU allocation - AT |



### 🧠 Shortcut / Mnemonic to Remember:

- **Arrival Time** → কখন ready queue-এ আসে  
- **Burst Time** → CPU-তে কত সময় লাগে  
- **Completion Time** → শেষ হয় কখন  
- **Turnaround Time** → শুরু থেকে শেষ পর্যন্ত সময় = CT - AT  
- **Waiting Time** → TAT থেকে CPU সময় বাদ দিলে → TAT - BT  
- **Response Time** → Arrival থেকে প্রথম CPU পাওয়া পর্যন্ত সময়

