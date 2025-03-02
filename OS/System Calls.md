### **System Calls - Explained Simply**

A **system call** is a request made by a program to the operating system (OS) to perform tasks that require access to hardware or memory.

Imagine you are playing a video game on your computer. If the game needs to save your progress, it must **ask the OS** to write data to the hard disk. The game cannot do this directly—it needs permission from the OS.

This "asking the OS" is done using **system calls**.

---

## **Modes in an Operating System**

To understand system calls, we must first understand the two modes in which a CPU operates:

### **1. Kernel Mode** 🛠️

- The CPU has **full control** over hardware and memory.
- The OS runs in kernel mode.
- If something goes wrong, the entire system may crash.

### **2. User Mode** 🧑‍💻

- Programs (like browsers, games, and editors) run in user mode.
- They **cannot directly access** memory or hardware.
- If a program crashes, only that program is affected, not the whole system.

🔹 **Switching between these modes happens using system calls.**

---

## **What is a System Call?**

A **system call** allows a user-mode program to **request services** from the OS, such as:  
✅ Creating or deleting files  
✅ Running a new process  
✅ Communicating over a network  
✅ Using a printer, keyboard, or mouse

### **How Does a System Call Work?**

1️⃣ A program in **user mode** makes a system call.  
2️⃣ The OS **switches to kernel mode** (this is called a **context switch**).  
3️⃣ The OS performs the requested action (like reading a file).  
4️⃣ The OS **switches back to user mode** and returns the result to the program.

📌 **Example**: When you open a file in Notepad, Notepad makes a **system call** to read the file from the disk.

---

## **Important System Calls in UNIX**

### **1. `fork()` - Creating a New Process**

🔹 `fork()` creates a **new process** by copying the existing process.  
🔹 The original process is called the **parent process**.  
🔹 The newly created process is called the **child process**.  
🔹 Both processes **start running from the next line after `fork()`**.

### **Example of `fork()`**

```c
#include <stdio.h>
#include <unistd.h>

void main() 
{
    int val;  
    val = fork();   // Creates a new process
    printf("%d", val);  // Print value returned by fork()
}
```

### **How It Works?**

- When `fork()` is called, a new process is created.
- **In the parent process**, `fork()` returns the child’s **Process ID (PID)**.
- **In the child process**, `fork()` returns `0`.

#### **Possible Output**

```
1234 0
```

(Here, `1234` is the process ID of the child process.)

🔹 Both the parent and child **continue execution from the same point**, but they have separate memory spaces.

---

### **2. `exec()` - Replacing a Process**

🔹 The `exec()` system call **replaces the current process** with a new process.  
🔹 Unlike `fork()`, it does **not create a new process**. Instead, it **replaces the current process entirely**.  
🔹 After `exec()`, the old process **does not exist anymore**.

### **Example of `exec()`**

```c
#include <stdio.h>
#include <unistd.h>

void main() 
{
    execl("/bin/ls", "ls", 0);  // Runs the "ls" command
    printf("This text won't be printed unless an error occurs.");
}
```

### **How It Works?**

- The `execl()` function replaces the current process with the **`ls` command** (which lists files in UNIX).
- The `printf()` line **will not be executed** because the process running the code is **replaced by `ls`**.
- If an error occurs in `execl()`, then `printf()` will run.

---

## **Key Differences Between `fork()` and `exec()`**

|Feature|`fork()`|`exec()`|
|---|---|---|
|Creates new process?|✅ Yes|❌ No|
|Copies parent process?|✅ Yes|❌ No (Replaces it)|
|Parent process continues?|✅ Yes|❌ No|
|Example|Running multiple programs|Running a new program in place of the old one|

---

## **Real-Life Analogy**

🔹 **`fork()` - Making a Photocopy**  
Imagine you have a document, and you **make a copy** of it. Now you have two documents, but they are independent.

🔹 **`exec()` - Replacing a Page**  
Imagine you have a document and you completely **replace its content** with something new. The original content is **gone forever**.

---

## **Conclusion**

- A **system call** allows user programs to request OS services.
- **`fork()` creates a new process**, while **`exec()` replaces a process**.
- The **OS switches between user mode and kernel mode** to process system calls safely.
- **System calls are essential for managing processes, memory, files, and devices.**

Would you like a diagram to illustrate this better? 😊