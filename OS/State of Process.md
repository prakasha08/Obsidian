![[Pasted image 20250301203552.png]]
This image represents the **Process State Diagram**, which shows the different states a process can go through in an operating system. Let's break it down step by step:

---

## **📌 Key Components of the Diagram:**

1. **New:**
    
    - A process is created and enters the **New** state.
    - The OS prepares resources for it before execution.
2. **Ready:**
    
    - The process is ready for execution but waiting for the CPU.
    - The **Scheduler** selects a process from the Ready queue and dispatches it to run.
3. **Run:**
    
    - The process is currently executing on the CPU.
    - It can:
        - **Complete execution** → move to **Terminate** state.
        - **Request I/O** (input/output) → move to **Wait/Block** state.
        - **Be preempted** (if another process gets higher priority) → go back to **Ready** state.
4. **Wait / Block:**
    
    - The process is waiting for some event (e.g., I/O completion).
    - It **cannot execute until the event occurs**.
    - After the event is completed, the process moves back to **Ready**.
5. **Terminate:**
    
    - The process has finished execution and is removed from memory.

---

## **📌 Suspended States:**

The diagram also includes two **suspended** states, which occur when a process is moved out of main memory (RAM) into secondary storage (like a hard disk) to free up space.

1. **Suspend Ready:**
    
    - The process **was in Ready state but got suspended** due to memory constraints.
    - It can resume back to **Ready** when enough memory is available.
7. **Suspend Wait:**
    
    - The process **was in Wait/Block state but got suspended** to save memory.
    - It can resume back to **Wait/Block** when needed.

---

## **📌 Transitions Between States:**

- **New → Ready:** A process is admitted into the system.
- **Ready → Run:** The scheduler selects a process for execution.
- **Run → Terminate:** Process finishes execution.
- **Run → Wait/Block:** The process requests I/O and must wait.
- **Wait/Block → Ready:** The I/O operation completes.
- **Run → Ready:** Process is preempted by the OS (only in preemptive scheduling).
- **Ready → Suspend Ready:** The process is suspended to free memory.
- **Suspend Ready → Ready:** The process resumes when memory is available.
- **Wait/Block → Suspend Wait:** Process is waiting but is moved to secondary storage.
- **Suspend Wait → Wait/Block:** The process is brought back to memory when needed.

---

## **📌 Summary**

🔹 The **Process State Diagram** helps visualize how processes move through different states in an OS.  
🔹 In **non-preemptive scheduling**, a running process **cannot be interrupted**; it must complete or voluntarily move to another state.  
🔹 In **preemptive scheduling**, a process can be interrupted and moved back to **Ready** if a higher-priority process needs execution.

Would you like an example of how a process moves through these states? 😊