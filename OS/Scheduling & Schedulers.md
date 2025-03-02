### **In Operating Systems (Preemptive Scheduling)**

- **Preemptive scheduling** is when the operating system can **interrupt a running process** and switch to another process with higher priority.
- Example: A running application (low priority) gets interrupted by an incoming call (high priority).

🔹 **Example of Preemptive Scheduling Algorithms:**

- Round Robin (RR)
- Priority Scheduling
- Shortest Remaining Time First (SRTF)
### **In Operating Systems (Non-Preemptive Scheduling)**

- **Non-preemptive scheduling** means once a process starts executing, it **cannot be interrupted** until it finishes or voluntarily enters a waiting state.
- The CPU **only switches** to another process when the current process is **done**.

🔹 **Examples of Non-Preemptive Scheduling Algorithms:**

- **First Come, First Served (FCFS)** → The first process that arrives runs until it completes.
- **Shortest Job First (SJF) (Non-preemptive version)** → The shortest job runs first and completes before the next one starts.
- **Priority Scheduling (Non-preemptive)** → The highest priority process starts and runs to completion.
  
  ### **Schedulers in Operating Systems**

Schedulers are system components responsible for managing process execution by selecting which processes should run at a given time. They help optimize CPU utilization and ensure fair execution of tasks.

There are **three types of schedulers** in an OS:

---

### **Non-Preemptive vs Preemptive Scheduling**

|Feature|Non-Preemptive|Preemptive|
|---|---|---|
|CPU Reallocation|No, once assigned, process runs until completion or voluntarily releases|Yes, CPU can be taken away by scheduler|
|Context Switching|Less frequent, since CPU is not forcefully taken away|More frequent, as processes may be interrupted|
|Efficiency|Works well in batch systems|Works well in time-sharing & real-time systems|
|Starvation Risk|Can occur in SJF & Priority Scheduling|Reduced due to fairness in execution|
|Implementation Complexity|Easier to implement|More complex due to frequent process switching|
## **1️⃣ Long-Term Scheduler (Job Scheduler)**

### **Role:**

- Controls the **degree of multiprogramming** (i.e., how many processes exist in memory).
- Decides which processes from the **job pool (secondary storage)** should be loaded into **main memory** for execution.
- Runs **infrequently**, as process creation is not very frequent.

### **State Transition:**

- Moves processes from **New** → **Ready** state.

### **Example Scenario:**

- A user submits a batch job (e.g., a print request or data analysis task).
- The long-term scheduler decides **when** to move this job from secondary storage (like disk) into main memory.
- Once moved, the process is placed in the **Ready** queue for execution.

---

## **2️⃣ Short-Term Scheduler (CPU Scheduler)**

### **Role:**

- Decides **which process from the Ready state** gets CPU time next.
- Runs **very frequently** (milliseconds) because process switching occurs rapidly.
- Works based on scheduling algorithms like **Round Robin, Priority Scheduling, Shortest Job Next, etc.**

### **State Transition:**

- Moves processes from **Ready** → **Run** state.

### **Example Scenario:**

- Multiple processes are in the Ready queue.
- The short-term scheduler selects one process to run based on priority or scheduling policy.
- Once the process completes or reaches a time limit, the scheduler picks the next process.

---

## **3️⃣ Medium-Term Scheduler (Swapper)**

### **Role:**

- Controls **swapping** of processes between main memory and secondary storage.
- Used in systems that support **suspension** to improve performance.
- Runs **occasionally**, when memory usage is high.

### **State Transition:**

- Moves processes between **Ready/Wait** ↔ **Suspend Ready/Suspend Wait**.

### **Example Scenario:**

- If too many processes are in memory, the **medium-term scheduler** moves some to disk (Suspend Ready or Suspend Wait) to free up space.
- When needed, it brings back processes from Suspend Ready to Ready.

---

### **📌 Comparison Table of Schedulers**

|**Scheduler**|**Function**|**State Transition**|**Frequency**|
|---|---|---|---|
|**Long-Term Scheduler**|Loads processes into memory|New → Ready|Infrequent|
|**Short-Term Scheduler**|Selects process for CPU execution|Ready → Run|Very Frequent (ms)|
|**Medium-Term Scheduler**|Swaps processes between RAM and disk|Ready/Wait ↔ Suspend Ready/Suspend Wait|Occasional|

---

### **🚀 Summary**

- **Long-Term Scheduler**: Controls how many processes enter memory.
- **Short-Term Scheduler**: Decides which process gets CPU next.
- **Medium-Term Scheduler**: Swaps processes in and out of memory to optimize performance.

Would you like a detailed explanation of scheduling **algorithms** as well? 😊

# **Process Scheduling Parameters in Operating Systems**

When scheduling processes in an operating system, we use several parameters to measure performance and efficiency. Below are the key terms used in process scheduling:
## **🔹 Key Parameters of a Process**

|**Parameter**|**Meaning**|
|---|---|
|**AT (Arrival Time)**|The time when a process arrives in the ready queue.|
|**BT (Burst Time)**|The total time required by a process to execute on the CPU.|
|**CT (Completion Time)**|The time when a process finishes execution.|
|**TAT (Turnaround Time)**|The total time a process spends in the system (TAT = CT - AT).|
|**WT (Waiting Time)**|The time a process spends waiting in the ready queue (WT = TAT - BT).|
|**RT (Response Time)**|The time from when a process arrives until it gets CPU for the first time (RT = First CPU execution time - AT).|

---

## **🔹 Understanding with an Example**

### **🔸 Given Processes:**

|Process|AT (Arrival Time)|BT (Burst Time)|
|---|---|---|
|P1|0 ms|5 ms|
|P2|2 ms|3 ms|
|P3|4 ms|2 ms|

**👉 Assume we use FCFS (First-Come, First-Served) Scheduling.**

### **🔸 Gantt Chart Representation**

plaintext

CopyEdit

`| P1 | P1 | P1 | P1 | P1 | P2 | P2 | P2 | P3 | P3 | 0    1    2    3    4    5    6    7    8    9    10`

---

### **🔸 Calculating Completion Time (CT)**

|Process|AT|BT|CT (Completion Time)|
|---|---|---|---|
|P1|0|5|5|
|P2|2|3|8|
|P3|4|2|10|

---

### **🔸 Calculating Turnaround Time (TAT)**

**Formula:**

TAT=CT−ATTAT = CT - ATTAT=CT−AT

|Process|CT|AT|**TAT (CT - AT)**|
|---|---|---|---|
|P1|5|0|5 - 0 = 5|
|P2|8|2|8 - 2 = 6|
|P3|10|4|10 - 4 = 6|

---

### **🔸 Calculating Waiting Time (WT)**

**Formula:**

WT=TAT−BTWT = TAT - BTWT=TAT−BT

|Process|TAT|BT|**WT (TAT - BT)**|
|---|---|---|---|
|P1|5|5|5 - 5 = 0|
|P2|6|3|6 - 3 = 3|
|P3|6|2|6 - 2 = 4|

---

### **🔸 Calculating Response Time (RT)**

**Formula:**

RT=FirstCPUExecutionTime−ATRT = First CPU Execution Time - ATRT=FirstCPUExecutionTime−AT

|Process|First Execution|AT|**RT (First CPU - AT)**|
|---|---|---|---|
|P1|0|0|0 - 0 = 0|
|P2|5|2|5 - 2 = 3|
|P3|8|4|8 - 4 = 4|

---

## **🔹 Final Table Summary**

|Process|AT|BT|CT|TAT (CT-AT)|WT (TAT-BT)|RT (First CPU - AT)|
|---|---|---|---|---|---|---|
|P1|0|5|5|5|0|0|
|P2|2|3|8|6|3|3|
|P3|4|2|10|6|4|4|

---

## **🔹 Key Observations**

1. **Turnaround Time (TAT)** measures how long a process spends in the system (execution + waiting).
2. **Waiting Time (WT)** shows how long a process waited in the ready queue before execution.
3. **Response Time (RT)** is crucial in interactive systems, as it tells how quickly a process starts after arrival.
4. **Completion Time (CT)** depends on the scheduling algorithm used.
# **Non-Preemptive Scheduling Algorithms**

### **1️⃣ First-Come, First-Served (FCFS)**

📌 **Process that arrives first gets executed first.**  
📌 **No priority or burst time consideration.**

#### **Example:**

|Process|Arrival Time|Burst Time|
|---|---|---|
|P1|0 ms|5 ms|
|P2|1 ms|3 ms|
|P3|2 ms|8 ms|

📌 **Execution Order:** P1 → P2 → P3  
📌 **Disadvantage:** **Convoy effect** (short processes have to wait for long processes to finish).

---

### **2️⃣ Shortest Job First (SJF) (Non-Preemptive)**

📌 **The process with the shortest CPU burst time is executed first.**  
📌 **Reduces average waiting time but may cause starvation.**

#### **Example:**

|Process|Arrival Time|Burst Time|
|---|---|---|
|P1|0 ms|6 ms|
|P2|2 ms|8 ms|
|P3|4 ms|3 ms|
|P4|5 ms|4 ms|

📌 **Execution Order:** P1 → P3 → P4 → P2  
📌 **Disadvantage:** Long processes may starve if shorter ones keep arriving.

---

### **3️⃣ Priority Scheduling (Non-Preemptive)**

📌 **Processes are executed based on priority levels assigned.**  
📌 **Lower priority processes have to wait for higher-priority ones.**

#### **Example:**

|Process|Arrival Time|Burst Time|Priority (Lower is Higher)|
|---|---|---|---|
|P1|0 ms|5 ms|3|
|P2|1 ms|3 ms|1|
|P3|2 ms|8 ms|2|

📌 **Execution Order:** P2 → P3 → P1 (since P2 has the highest priority).  
📌 **Disadvantage:** Starvation (low-priority processes might never get executed).

---

### **4️⃣ Round Robin (RR) - Without Time Quantum (Not Ideal for RR)**

📌 **Generally, Round Robin is preemptive**, but if time quantum is large enough, it behaves like non-preemptive scheduling.

---

### **Longest Remaining Time First (LRTF) Scheduling**

#### **What is LRTF?**

- **LRTF (Longest Remaining Time First)** is a **preemptive** version of LJF.
- The process with the **longest remaining burst time** gets the CPU.
- If a new process arrives with a **longer** remaining burst time, it **preempts** the current process.

#### **How LRTF Works?**

1. **Sort** processes by burst time in descending order.
2. Start executing the process with the **longest remaining time**.
3. If a **new process arrives with a longer burst time**, **preempt** the current process.
4. Continue execution until all processes are completed.

#### **Example of LRTF**

|Process|Arrival Time (AT)|Burst Time (BT)|
|---|---|---|
|P1|0 ms|8 ms|
|P2|2 ms|6 ms|
|P3|3 ms|4 ms|
|P4|5 ms|2 ms|

##### **Execution Order:**

1. Start with **P1** at time **0** (BT = 8).
2. **P2** arrives at time **2** (BT = 6) → No preemption (P1 has more BT left).
3. **P3** arrives at time **3** (BT = 4) → No preemption.
4. **P4** arrives at time **5** (BT = 2) → No preemption.
5. **P1 finishes**, then **P2**, then **P3**, then **P4**.

🟢 **Final Execution Order:** `P1 → P2 → P3 → P4`

##### **Advantages of LRTF**

✅ Ensures **CPU time for larger processes**.  
✅ More **efficient CPU utilization** in batch processing.

##### **Disadvantages of LRTF**

❌ **More context switching** than LJF.  
❌ **Shorter jobs suffer** (Starvation issue).
## **🔹 Advantages & Disadvantages of Non-Preemptive Scheduling**

| **Advantages**                              | **Disadvantages**                                   |
| ------------------------------------------- | --------------------------------------------------- |
| Simple and easy to implement                | Not ideal for time-sharing or interactive systems   |
| Less overhead due to fewer context switches | Long processes may delay short ones (Convoy effect) |
| No risk of process starvation in FCFS       | Starvation can occur in SJF & Priority Scheduling   |
| Works well for batch processing             | Not responsive for real-time tasks                  |

# Preemptive Scheduling Algorithms**

Let’s explore the **four major** preemptive scheduling algorithms with examples.

### **A. Shortest Remaining Time First (SRTF)**

🔹 The **process with the shortest remaining burst time** gets the CPU.  
🔹 If a new process arrives with a smaller burst time than the remaining time of the running process, the CPU **switches** to that new process.

📌 **Example:**

|Process|Arrival Time (AT)|Burst Time (BT)|
|---|---|---|
|P1|0 ms|8 ms|
|P2|1 ms|4 ms|
|P3|2 ms|2 ms|
|P4|3 ms|1 ms|

**Execution Order:**

- P1 starts at time **0**
- P2 arrives at time **1** (remaining time of P1 = 7, but P2 has BT = 4, so P2 takes CPU)
- P3 arrives at time **2** (P3 has BT = 2, so it **preempts** P2)
- P4 arrives at time **3** (P4 has BT = 1, so it preempts P3)
- After P4 finishes, P3 resumes, then P2, then P1.

🟢 **Final Execution Order:** `P1 → P2 → P3 → P4 → P3 → P2 → P1`

---

### **B. Round Robin (RR)**

🔹 Each process gets a fixed **time quantum** (e.g., 2ms).  
🔹 If a process doesn’t complete in that time, it moves to the back of the queue.  
🔹 Ensures **fair CPU time distribution** among processes.

📌 **Example:** (Time Quantum = 2ms)

|Process|Arrival Time (AT)|Burst Time (BT)|
|---|---|---|
|P1|0 ms|5 ms|
|P2|1 ms|3 ms|
|P3|2 ms|4 ms|

**Execution Order:**

1. `P1 (2ms) → P2 (2ms) → P3 (2ms)`
2. `P1 (remaining 3ms) → P2 (remaining 1ms) → P3 (remaining 2ms)`
3. `P1 (remaining 1ms) → P3 (remaining 2ms)`

🟢 **Final Execution Order:** `P1 → P2 → P3 → P1 → P2 → P3 → P1`
### **C. Priority Scheduling (Preemptive)**

🔹 The **highest priority process** gets the CPU.  
🔹 If a new process arrives with a **higher priority**, it preempts the current process.

📌 **Example:** (Lower priority number = Higher priority)

|Process|Arrival Time (AT)|Burst Time (BT)|Priority|
|---|---|---|---|
|P1|0 ms|4 ms|3|
|P2|1 ms|3 ms|1|
|P3|2 ms|2 ms|2|

**Execution Order:**

- P1 starts at time **0**
- P2 arrives at time **1** (Priority = 1, higher than P1's priority, so **P1 is preempted**)
- P2 runs to completion.
- P3 runs (Priority 2).
- P1 resumes and finishes.

🟢 **Final Execution Order:** `P1 → P2 → P3 → P1`
### **D. Longest Job First (LJF) Scheduling**

#### **What is LJF?**

- **LJF (Longest Job First)** is a **non-preemptive** scheduling algorithm.
- The process with the **longest burst time (BT)** is executed first.
- It is the opposite of **Shortest Job First (SJF)**, which executes the shortest burst first.

#### **How LJF Works?**

1. **Sort** the processes based on their burst times in **descending order**.
2. **Select** the process with the highest burst time first.
3. **Execute** the process until it completes.
4. **Repeat** for the next longest burst time process.

#### **Example of LJF**

|Process|Arrival Time (AT)|Burst Time (BT)|
|---|---|---|
|P1|0 ms|3 ms|
|P2|2 ms|6 ms|
|P3|4 ms|2 ms|
|P4|6 ms|8 ms|

##### **Execution Order:**

1. Sort by burst time: **P4 → P2 → P1 → P3**
2. Execute **P4 (8ms) → P2 (6ms) → P1 (3ms) → P3 (2ms)**.

🟢 **Final Execution Order:** `P4 → P2 → P1 → P3`

##### **Advantages of LJF**

✅ Maximizes CPU utilization for large processes.  
✅ Useful when long-running tasks are **more critical**.

##### **Disadvantages of LJF**

❌ **Starvation:** Short processes may suffer **long waiting times**.  
❌ **Not optimal** for interactive systems.