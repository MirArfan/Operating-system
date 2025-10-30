# ⚙️ Operating System Algorithms

This folder contains **implementation + explanation** of key Operating System algorithms.

---

## 🧮 Categories

### 🕐 CPU Scheduling
- FCFS (First Come First Serve) ( ✅ done)
- SJF (Shortest Job First) ( ✅ done)
- SRT (Shortest Reaming Time) ( ✅ done)
- Round Robin (RR)  ( ✅ done)
- Priority Scheduling

### 💾 Page Replacement
- FIFO (First In First Out)
- LRU (Least Recently Used)
- Optimal Page Replacement

### 🔒 Deadlock
- Banker's Algorithm

### 💽 Disk Scheduling
- FCFS
- SSTF
- SCAN

---
```

os-notes/
│
├── README.md
│
├── notes/
│   ├── 01_intro_to_os.md
│   ├── 02_process_and_threads.md
│   ├── 03_cpu_scheduling.md
│   ├── 04_memory_management.md
│   ├── 05_file_system.md
│   ├── 06_deadlock.md
│   ├── 07_virtual_memory.md
│   └── 08_io_system.md
│
├── algorithms/
│   ├── cpu_scheduling/
│   │   ├── fcfs.cpp
│   │   ├── sjf.cpp
│   │   ├── round_robin.cpp
│   │   ├── priority_scheduling.cpp
│   │   └── explanation.md
│   │
│   ├── page_replacement/
│   │   ├── fifo.cpp
│   │   ├── lru.cpp
│   │   ├── optimal.cpp
│   │   └── explanation.md
│   │
│   ├── deadlock/
│   │   ├── bankers_algorithm.cpp
│   │   └── explanation.md
│   │
│   ├── disk_scheduling/
│   │   ├── fcfs.cpp
│   │   ├── sstf.cpp
│   │   ├── scan.cpp
│   │   └── explanation.md
│   │
│   └── README.md
│
├── diagrams/
│   ├── process_state_diagram.png
│   ├── scheduling_algo_chart.png
│   ├── paging_diagram.png
│   └── deadlock_graph.png
│
├── examples/
    ├── multithreading_example.cpp
    ├── memory_allocation_demo.c
    └── io_example.cpp

```