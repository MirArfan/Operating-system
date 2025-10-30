# 🧠 Banker’s Algorithm Examples

---

## 🧠 Example 1: Safe State

**Given:**

- **Processes:** P0, P1, P2  
- **Resources:** R1, R2, R3  

| Process | Allocation C | Max Need M | Remaining Need R = M - C |
|---------|--------------|------------|-------------------------|
| P0      | (0, 1, 0)    | (7, 5, 3)  | (7, 4, 3)              |
| P1      | (2, 0, 0)    | (3, 2, 2)  | (1, 2, 2)              |
| P2      | (3, 0, 2)    | (9, 0, 2)  | (6, 0, 0)              |

**Available (A):** (3, 3, 2)

### Step 1: Find process whose R ≤ A

- **P1 → R1=(1,2,2) ≤ A=(3,3,2) ✅ → Execute**  
  Release C1=(2,0,0) → New A=(5,3,2)

- **P0 → R0=(7,4,3) ≤ A=(5,3,2) ❌ → Cannot execute**  
- **P2 → R2=(6,0,0) ≤ A=(5,3,2) ❌ → Cannot execute**

Recheck P0 → still cannot execute.

### Observation:

- All processes cannot finish immediately, but future resource releases can allow completion.  
- **Safe State Sequence (example extended):** P1 → P0 → P2 ✅

---

## 🧠 Example 2: Unsafe / Deadlock State

**Given:**

- **Processes:** P0, P1, P2  
- **Resources:** R1, R2, R3  

| Process | Allocation C | Max Need M | Remaining Need R = M - C |
|---------|--------------|------------|-------------------------|
| P0      | (0, 2, 0)    | (7, 5, 3)  | (7, 3, 3)              |
| P1      | (2, 0, 0)    | (3, 2, 2)  | (1, 2, 2)              |
| P2      | (3, 0, 3)    | (9, 0, 3)  | (6, 0, 0)              |

**Available (A):** (1, 1, 0)

### Step 1: Check who can execute

- **P0 → R0=(7,3,3) ≤ A=(1,1,0) ❌ → Cannot execute**  
- **P1 → R1=(1,2,2) ≤ A=(1,1,0) ❌ → Cannot execute**  
- **P2 → R2=(6,0,0) ≤ A=(1,1,0) ❌ → Cannot execute**

### Observation:

- No process can proceed → **Deadlock detected ❌**

---

## 🔹 Key Notes

- **Safe sequence:** resources can be allocated without deadlock.  
- **Unsafe state:** system may enter deadlock.  
- **Banker’s Algorithm:** ensures only safe allocations are allowed.
