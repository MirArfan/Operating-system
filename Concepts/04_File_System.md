# 🧠 File System (ফাইল সিস্টেম)

---

## 🧩 Definition (সংজ্ঞা)

### English:
A File System is a method used by an operating system to store, organize, and manage files on storage devices like HDD, SSD, or USB drives.  
It provides a way for users and programs to read, write, and access data efficiently.

### বাংলা:
ফাইল সিস্টেম হলো Operating System-এর পদ্ধতি, যা স্টোরেজ ডিভাইসে ফাইল সংরক্ষণ, আয়োজন এবং পরিচালনা করে।  
এটি ব্যবহারকারীর এবং প্রোগ্রামের জন্য ডেটা পড়া, লেখা এবং অ্যাক্সেস করা সহজ করে।

---

## 🔹 Functions of a File System (ফাংশন)

| Function | English | বাংলা |
|----------|---------|-------|
| File Storage & Organization | Organize files into directories/folders | ফাইলকে ডিরেক্টরি/ফোল্ডারে সাজানো |
| Access Control | Determines who can read/write files | কে কোন ফাইল পড়বে বা লিখবে তা নির্ধারণ করা |
| Data Management | Block allocation, indexing, metadata | ফাইলের block allocation, indexing, metadata সংরক্ষণ |
| Space Management | Track free space, reduce fragmentation | Free space tracking ও fragmentation কমানো |

---

## 🔹 Components of a File System (ফাইল সিস্টেমের উপাদান)

| Component | English Description | বাংলা |
|-----------|------------------|-------|
| File | Basic unit of data storage, contains information | ফাইল হলো ডেটা সংরক্ষণের মৌলিক ইউনিট |
| Directory | Organizes files into a hierarchical structure | ডিরেক্টরি ফাইলগুলোকে আয়োজিত করে |
| Metadata | Data about data (size, type, permissions, timestamps) | ফাইলের বৈশিষ্ট্য সংরক্ষণ (সাইজ, টাইপ, পারমিশন, সময়) |
| File Control Block (FCB) | OS data structure storing metadata & pointers to data blocks | OS-এর ডেটা স্ট্রাকচার যা metadata এবং ডেটা block-এর pointer রাখে |
| Storage Space | Physical blocks/clusters where file data is stored | ফাইল ডেটা সংরক্ষিত থাকে physical block বা cluster-এ |
| File Allocation Table (FAT) / Inodes | Keeps track of which blocks belong to which file | কোন block কোন ফাইলের, তা ট্র্যাক করে |

---

## 🔹 File Access Methods (ফাইল অ্যাক্সেস পদ্ধতি)

| Method | English | বাংলা |
|--------|---------|-------|
| Sequential Access | Read/write file in order | ফাইল ধারাবাহিকভাবে পড়া/লিখা |
| Direct / Random Access | Access any part of file directly | কোনো অংশ সরাসরি অ্যাক্সেস করা |

---

## 🔑 Key Points (মূল বিষয়)

- File System = Data storage + Organization + Access + Security  
- Components = File, Directory, Metadata, FCB, Storage Space, FAT/Inodes  
- File Access = Sequential / Direct  
- Efficient file system reduces disk seek time & manages space


---

# 🧠 Types of File System (ফাইল সিস্টেমের ধরন)

---

## 🔹 1️⃣ FAT (File Allocation Table)

### English:
- Simple, widely used in older systems & removable media (USB, SD cards)  
- Keeps track of file locations using a table  
- Easy to implement but limited file size & inefficient for large disks  

### বাংলা:
- সহজ, পুরনো সিস্টেম ও রিমুভেবল মিডিয়ায় (USB, SD card) ব্যবহৃত  
- ফাইলের location একটি table দিয়ে ট্র্যাক করে  
- ইমপ্লিমেন্ট করা সহজ, কিন্তু বড় ড্রাইভে অকার্যকর এবং ফাইল সাইজ সীমিত  

---

## 🔹 2️⃣ NTFS (New Technology File System)

### English:
- Modern file system used by Windows OS  
- Supports large files, security, encryption, compression, and metadata  
- Efficient and reliable  

### বাংলা:
- Windows OS-এর আধুনিক ফাইল সিস্টেম  
- বড় ফাইল, security, encryption, compression, metadata সমর্থন করে  
- দক্ষ এবং নির্ভরযোগ্য  

---

## 🔹 3️⃣ ext (Extended File System)

### English:
- Used in Linux systems (ext2, ext3, ext4)  
- Journaling support (ext3, ext4) → protects data against crash  
- Efficient for large files and multiple users  

### বাংলা:
- Linux সিস্টেমে ব্যবহৃত (ext2, ext3, ext4)  
- Journaling সমর্থন (ext3, ext4) → crash থেকে ডেটা রক্ষা করে  
- বড় ফাইল ও বহু ব্যবহারকারীর জন্য কার্যকর  

---

## 🔹 4️⃣ HFS / HFS+ (Hierarchical File System)

### English:
- Used in Mac OS  
- Supports file hierarchy, metadata, and journaling  

### বাংলা:
- Mac OS-এ ব্যবহৃত  
- ফাইল hierarchy, metadata, journaling সমর্থন করে  

---

## 🔹 5️⃣ ISO 9660 / UDF

### English:
- Used for CDs, DVDs, and optical media  
- Standardized to read/write across multiple platforms  

### বাংলা:
- CD, DVD এবং optical media-এর জন্য ব্যবহৃত  
- বিভিন্ন প্ল্যাটফর্মে read/write সমর্থন দেয়  

---

## 🔑 Key Points (মূল বিষয়)

- File System type নির্ভর করে OS এবং media type-এর উপর  
- FAT → simple, NTFS → modern Windows, ext → Linux, HFS+ → Mac, ISO/UDF → optical media  
- Efficient file system improves storage management, access speed, and reliability


---
# 🧠 File Allocation and Deallocation (ফাইল বরাদ্দ এবং মুক্তকরণ)

---

## 🧩 Definition (সংজ্ঞা)

### English:
- **File Allocation:** Process of assigning disk blocks to a file so that the data can be stored on storage devices.  
- **File Deallocation:** Process of releasing the blocks used by a file once it is deleted or no longer needed.  

### বাংলা:
- **File Allocation:** ফাইল সংরক্ষণের জন্য ডিস্ক ব্লক বরাদ্দ করার প্রক্রিয়া।  
- **File Deallocation:** ফাইল মুছে ফেলার পর বা আর প্রয়োজন না থাকলে বরাদ্দ করা ব্লক মুক্ত করার প্রক্রিয়া।  

---

## 🔹 File Allocation Methods (ফাইল বরাদ্দ পদ্ধতি)

| Method | English Description | বাংলা |
|--------|-------------------|------|
| Contiguous Allocation | File stored in consecutive blocks | ফাইল ধারাবাহিক ব্লকে সংরক্ষিত |
| Linked Allocation | File blocks linked as a chain | ব্লকগুলো চেইনের মতো সংযুক্ত |
| Indexed Allocation | An index block contains pointers to all file blocks | Index block এ সমস্ত ব্লকের pointer থাকে |

---

## 1️⃣ Contiguous Allocation (ধারাবাহিক বরাদ্দ)

### English:
- Blocks allocated sequentially on disk.  
- Fast access, simple to implement.  
- Problem: External fragmentation, need contiguous free space.  

### বাংলা:
- ব্লকগুলো ধারাবাহিকভাবে বরাদ্দ করা হয়।  
- দ্রুত অ্যাক্সেস, সহজ ইমপ্লিমেন্টেশন।  
- সমস্যা: External fragmentation, contiguous free space প্রয়োজন।  

---

## 2️⃣ Linked Allocation (লিঙ্কড বরাদ্দ)

### English:
- Each block contains pointer to next block.  
- No external fragmentation, easy to grow file.  
- Problem: Random access slower.  

### বাংলা:
- প্রতিটি ব্লকে পরের ব্লকের pointer থাকে।  
- External fragmentation নেই, ফাইল বড় করা সহজ।  
- সমস্যা: Random access ধীর।  

---

## 3️⃣ Indexed Allocation (ইন্ডেক্সড বরাদ্দ)

### English:
- Special index block stores addresses of all blocks of a file.  
- Supports direct/random access.  
- Problem: Index block overhead for very large files.  

### বাংলা:
- Index block-এ ফাইলের সব ব্লকের ঠিকানা থাকে।  
- Direct/random access সম্ভব।  
- সমস্যা: বড় ফাইলের জন্য index block overhead বেশি।  

---

## 🔹 File Deallocation (ফাইল মুক্তকরণ)

### English:
- On deletion, all blocks are marked free in the file system.  
- Updates FAT / index table accordingly.  

### বাংলা:
- ফাইল মুছে ফেলার সময়, সব ব্লক free হিসেবে চিহ্নিত হয়।  
- FAT বা index table update করা হয়।  

---

## 🔑 Key Points (মূল বিষয়)

- File Allocation determines how a file is stored on disk  
- Main methods: Contiguous, Linked, Indexed  
- Allocation affects access speed, fragmentation, and file growth  
- Deallocation ensures efficient space reuse
---


# 🧠 Fragmentation (ফ্র্যাগমেন্টেশন)

---

## 🧩 Definition (সংজ্ঞা)

### English:
Fragmentation occurs when free memory or disk space is broken into small, non-contiguous blocks, making it difficult to allocate large continuous memory or storage for processes or files.

### বাংলা:
ফ্র্যাগমেন্টেশন ঘটে যখন ফ্রি মেমোরি বা ডিস্ক স্পেস ছোট, অ-ধারাবাহিক ব্লকে ভাগ হয়ে যায়, যার ফলে বড় ধারাবাহিক মেমোরি বা ডিস্ক ব্লক বরাদ্দ করা কঠিন হয়ে যায়।

---

## 🔹 Types of Fragmentation (ফ্র্যাগমেন্টেশনের ধরন)

| Type | English | বাংলা |
|------|--------|------|
| External Fragmentation | Free memory is split into small non-contiguous blocks, can’t satisfy large allocation request | ফ্রি মেমোরি ছোট ছোট, ধারাবাহিক নয় এমন ব্লকে ভাগ হয়ে যায়, বড় বরাদ্দ দেওয়া সম্ভব হয় না |
| Internal Fragmentation | Allocated block is slightly larger than requested, wasting some space | বরাদ্দকৃত ব্লক অনুরোধের চেয়ে বড় হলে কিছু অংশ ফাঁকা থাকে, যা নষ্ট হয় |

---

## 1️⃣ External Fragmentation (এক্সটার্নাল)

### English:
- Happens in contiguous memory allocation.  
- Memory gets scattered, leaving small unusable gaps.  
- Solved by compaction or using paging/segmentation.  

### বাংলা:
- ধারাবাহিক মেমোরি বরাদ্দে ঘটে।  
- মেমোরি বিখণ্ডিত হয়ে যায়, ছোট ছোট ব্যবহার অযোগ্য গ্যাপ তৈরি হয়।  
- সমাধান: compaction বা paging/segmentation ব্যবহার।  

---

## 2️⃣ Internal Fragmentation (ইন্টার্নাল)

### English:
- Happens when allocated memory block > requested memory.  
- Wasted space inside the allocated block.  
- Common in fixed-size partitioning.  

### বাংলা:
- বরাদ্দকৃত মেমোরি ব্লক > অনুরোধকৃত মেমোরি হলে ঘটে।  
- বরাদ্দ ব্লকের ভিতরে কিছু স্থান নষ্ট হয়।  
- সাধারণত fixed-size partitioning-এ দেখা যায়।  

---

## 🔹 Key Points (মূল বিষয়)

- Fragmentation reduces memory/disk utilization efficiency  
- **External:** non-contiguous free blocks  
- **Internal:** wasted space inside allocated blocks  

### Solutions:
- **Paging / Segmentation:** avoids external fragmentation  
- **Compaction:** merge free memory blocks  
- **Variable block sizes:** reduces internal fragmentation


---
