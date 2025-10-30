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




# ⚠️ Deadlock in Operating Systems (ডেডলক)

---

## 🧠 Definition (সংজ্ঞা)

### 🗣️ English:
A **Deadlock** occurs in a multiprogramming or concurrent system when two or more processes are blocked forever, each waiting for resources held by the others.

### 🇧🇩 বাংলা:
ডেডলক হলো এমন অবস্থা যেখানে একাধিক প্রসেস একে অপরের resource-এর জন্য অপেক্ষা করতে করতে চিরকাল blocked থাকে।

---

## 🔄 Necessary Conditions (ডেডলক হওয়ার শর্ত)

Deadlock ঘটতে হলে চারটি শর্ত একসাথে থাকতে হবে:

| Condition         | English Explanation                          | বাংলা ব্যাখ্যা                                |
|------------------|--------------------------------------------|---------------------------------------------|
| Mutual Exclusion  | Only one process can use a resource at a time | একটি resource একসাথে কেবল একটি প্রসেস ব্যবহার করতে পারে |
| Hold and Wait     | Process holds resources while waiting for others | প্রসেস কিছু resource ধরে রেখে অন্য resource-এর জন্য অপেক্ষা করে |
| No Preemption     | Resources cannot be forcibly taken          | প্রসেস থেকে জোরপূর্বক resource নেওয়া যায় না |
| Circular Wait     | Processes wait in a circular chain          | প্রসেসগুলো একে অপরের জন্য চক্রাকারে অপেক্ষা করে |

> ⚠️ এই চারটি শর্ত একসাথে থাকলে Deadlock ঘটতে পারে।

---

## 🧩 Deadlock Prevention Methods (ডেডলক প্রতিরোধ)

Deadlock prevention মূলত এই চারটি শর্তের কোনো একটি ভাঙার চেষ্টা:

1️⃣ **Mutual Exclusion Prevention**  
- **English:** Make resources sharable wherever possible.  
- **বাংলা:** যেগুলো ভাগ করা যায়, share করো যাতে exclusive access দরকার না হয়।

2️⃣ **Hold and Wait Prevention**  
- **English:** Require processes to request all needed resources at once.  
- **বাংলা:** প্রসেসকে একসাথে সব প্রয়োজনীয় resource চাওয়াতে হবে।

3️⃣ **No Preemption**  
- **English:** Allow OS to preempt resources if needed.  
- **বাংলা:** প্রয়োজন হলে OS resource জোরপূর্বক নিতে পারবে।

4️⃣ **Circular Wait Prevention**  
- **English:** Impose an ordering on resource requests.  
- **বাংলা:** Resource request-এর একটি ক্রম নির্ধারণ করো।

---

### Example Table

| Technique            | How it works                     | বাংলা ব্যাখ্যা                  |
|---------------------|---------------------------------|--------------------------------|
| One-Shot Allocation  | Allocate all resources at once   | সব resource একসাথে বরাদ্দ করা হয় |
| Preemptive Allocation| Take resources from processes temporarily | Resource জোরপূর্বক নেওয়া হয় প্রয়োজনে |

---

## 🧩 Deadlock Detection & Recovery (ডেডলক সনাক্ত ও পুনরুদ্ধার)

- **Detection:** OS periodically checks for deadlock using Resource Allocation Graphs.  
- **Recovery:** Break deadlock by terminating one or more processes or preempting resources.

### Example: Dining Philosophers Problem
- 5 philosophers sitting around a table, need 2 forks to eat.  
- Deadlock occurs if each philosopher picks up the fork to their left → no one can eat.

---

## 🔑 Key Points (মূল বিষয়)

- **Deadlock** = system halt in concurrent/multiprogramming systems.  
- **Prevention** = avoid necessary conditions.  
- **Detection + Recovery** = allow deadlock but resolve it.  
- Multiprogramming & multitasking systems must handle deadlocks carefully.

---

## 🔄 Deadlock Representation Diagram

Process A -> Resource 1 -> Process B -> Resource 2 -> Process C -> Resource 3 -> Process A

bash
Copy code

### বাংলা:
প্রসেসগুলো resource-এর জন্য **circular wait**-এ থাকে → deadlock।

---

# 🏦 Banker’s Algorithm (ব্যাংকার অ্যালগরিদম)

---

## 🧠 Definition (সংজ্ঞা)

### 🗣️ English:
The **Banker’s Algorithm** is a deadlock avoidance algorithm that ensures a system never enters an unsafe state.  
It simulates resource allocation for processes and grants requests only if it leaves the system in a **safe state**.  
The algorithm is called “Banker’s” because it is similar to a bank giving loans: a bank grants loans only if it can ensure all customers can eventually get their maximum needs satisfied.

### 🇧🇩 বাংলা:
Banker’s Algorithm হলো একটি **deadlock avoidance technique**, যা নিশ্চিত করে যে system কখনো **unsafe state**-এ যাবে না।  
প্রতিটি resource request পরীক্ষা করা হয় এবং শুধুমাত্র তখনই অনুমোদন করা হয় যখন system **safe state**-এ থাকে।  
“Banker” নামটি এসেছে ব্যাংকের উদাহরণ থেকে: ব্যাংক ঋণ দেয় শুধুমাত্র যখন নিশ্চিত থাকে যে সব গ্রাহক তাদের সর্বোচ্চ প্রয়োজন পূর্ণ করতে পারবে।

---

## 🧩 Key Concepts (মূল ধারণা)

| Concept         | English Explanation                          | বাংলা ব্যাখ্যা                                      |
|-----------------|---------------------------------------------|---------------------------------------------------|
| Safe State      | A state where all processes can finish without deadlock | এমন অবস্থা যেখানে সমস্ত প্রসেস শেষ হতে পারে deadlock ছাড়া |
| Unsafe State    | A state where deadlock is possible, but not guaranteed | এমন অবস্থা যেখানে deadlock হতে পারে, তবে নিশ্চিত নয় |
| Need Matrix     | Need[i][j] = Max[i][j] – Allocation[i][j] | প্রতিটি process-এর শুধুমাত্র বাকি resource প্রয়োজন |

---

## 🧩 Steps of Banker’s Algorithm (অ্যালগরিদমের ধাপ)

1. Initialize **Available**, **Max**, **Allocation**, and **Need** matrices.  
2. Find a process whose **Need ≤ Available**.  
3. If found, **pretend to allocate resources**:  
Available = Available + Allocation[i]
Finish[i] = true

yaml
Copy code
4. Repeat step 2 for remaining processes.  
5. If all processes can finish → **Safe State**, else → **Unsafe State**.

---

## 🔹 Example (উদাহরণ)

**Given:**

- Processes: P0, P1, P2  
- Resources: A, B, C  
- Available: (3, 3, 2)  

**Max Matrix:**

|     | A | B | C |
|-----|---|---|---|
| P0  | 7 | 5 | 3 |
| P1  | 3 | 2 | 2 |
| P2  | 9 | 0 | 2 |

**Allocation Matrix:**

|     | A | B | C |
|-----|---|---|---|
| P0  | 0 | 1 | 0 |
| P1  | 2 | 0 | 0 |
| P2  | 3 | 0 | 2 |

**Need = Max – Allocation**

- Step 1: Check P1 → Need P1 = (1,2,2) ≤ Available (3,3,2) ✅  
Allocate → Available = Available + Allocation[P1] = (5,3,2)  
- Step 2: Check P0 → Need P0 = (7,4,3) > Available (5,3,2) ❌ Skip  
- Step 3: Check P2 → Need P2 = (6,0,0) > Available (5,3,2) ❌ Skip  
- Repeat after P1 finishes, update Available and continue  

**Safe Sequence:** P1 → P0 → P2

---

## ✅ Key Points (মূল বিষয়)

- Banker’s Algorithm **prevents deadlock** by checking safe state before allocation.  
- Requires knowledge of **maximum resource needs** of each process.  
- Mainly used in **offline resource allocation** where Max is known.  
- **Overhead is high** → not suitable for all systems, but very educational for OS concepts.

---

## 🔄 Summary Diagram
```

Process Request → Check Need ≤ Available? 
     | Yes
     v
Pretend Allocate → Check if all processes can finish
     | Safe State
     v
Grant Request
     | Unsafe State
     v
Request Denied


```
