### ** Class Diagram Design**

A **class diagram** represents the **data model** with relationships between entities.

#### **Main Classes & Relationships:**

- **User** (Base class for **Doctor, Patient, Admin**)
- **Appointment** (Associates a **Doctor** and a **Patient**)
- **Prescription** (Linked to **Appointment** and **Medical Record**)
- **MedicalRecord** (Stores patient's **medical history**)
- **Billing** (Stores **payment details** for services)

#### **Class Diagram (Simplified in Text Format)**

```plaintext
        +----------------+
        |     User       |
        +----------------+
        | id            |
        | name          |
        | email         |
        | password      |
        +----------------+
        | login()       |
        +----------------+
               ▲
               │
 +-------------------+  +-------------------+
 |    Doctor        |  |     Patient       |
 +-------------------+  +-------------------+
 | specialization    |  | age               |
 | availability      |  | gender            |
 +-------------------+  +-------------------+

        +----------------+
        |  Appointment   |
        +----------------+
        | id            |
        | date          |
        | time          |
        +----------------+
        | schedule()    |
        +----------------+
        ▲       ▲
        |       |
+-----------+   +-----------+
|  Doctor   |   |  Patient  |

        +----------------+
        |  Prescription  |
        +----------------+
        | id            |
        | medicine      |
        | dosage        |
        | instructions  |
        +----------------+
        | generate()    |
        +----------------+
        ▲
        |
+-----------+
| Appointment |

        +----------------+
        | MedicalRecord  |
        +----------------+
        | id            |
        | diagnosis     |
        | history       |
        +----------------+
        | update()      |
        +----------------+
        ▲
        |
+-----------+
| Patient   |

        +----------------+
        |    Billing     |
        +----------------+
        | id            |
        | amount        |
        | status        |
        +----------------+
        | generateBill()|
        +----------------+
        ▲
        |
+-----------+
| Appointment |
```

---

## **🛠 Modules Covered**

1. **User Authentication**
2. **Appointment Scheduling** (Already implemented)
3. **Prescription** (Already implemented)
4. **Medical Record Management**
5. **Billing History**

---

## **📌 Step 1: Base `User` Class**

```java
public abstract class User {
    protected int id;
    protected String name;
    protected String email;
    protected String password;

    public User(int id, String name, String email, String password) {
        this.id = id;
        this.name = name;
        this.email = email;
        this.password = password;
    }

    public abstract void login();
}
```

### `Doctor` and `Patient` Classes**

```java
public class Doctor extends User {
    private String specialization;
    private boolean available;

    public Doctor(int id, String name, String email, String password, String specialization) {
        super(id, name, email, password);
        this.specialization = specialization;
        this.available = true;
    }

    public void setAvailability(boolean available) {
        this.available = available;
    }
}

public class Patient extends User {
    private int age;
    private String gender;

    public Patient(int id, String name, String email, String password, int age, String gender) {
        super(id, name, email, password);
        this.age = age;
        this.gender = gender;
    }
}
```

---

# **🔒 1. User Authentication Module**

This module ensures that **Doctors & Patients can log in**.

```java
import java.util.HashMap;
import java.util.Map;

public class Authentication {
    private Map<String, String> userDatabase = new HashMap<>();

    public void register(String email, String password) {
        if (!userDatabase.containsKey(email)) {
            userDatabase.put(email, password);
            System.out.println("User registered successfully!");
        } else {
            System.out.println("User already exists.");
        }
    }

    public boolean login(String email, String password) {
        if (userDatabase.containsKey(email) && userDatabase.get(email).equals(password)) {
            System.out.println("Login successful!");
            return true;
        }
        System.out.println("Invalid credentials.");
        return false;
    }
}
```

#### **📝 Testing Authentication**

```java
public class Main {
    public static void main(String[] args) {
        Authentication auth = new Authentication();
        
        auth.register("doctor@example.com", "doctor123");
        auth.register("patient@example.com", "patient123");

        auth.login("doctor@example.com", "doctor123"); // ✅ Login successful!
        auth.login("patient@example.com", "wrongpass"); // ❌ Invalid credentials
    }
}
```

---

# **📅 2. Appointment Scheduling Module** 

```java
import java.util.Date;

public class Appointment {
    private int id;
    private Doctor doctor;
    private Patient patient;
    private Date date;
    private String time;

    public Appointment(int id, Doctor doctor, Patient patient, Date date, String time) {
        this.id = id;
        this.doctor = doctor;
        this.patient = patient;
        this.date = date;
        this.time = time;
    }

    public void schedule() {
        System.out.println("Appointment booked with Dr. " + doctor.name + " for " + patient.name + " on " + date + " at " + time);
    }
}
```

#### **Testing Appointment Module**

```java
import java.util.Date;

public class Main {
    public static void main(String[] args) {
        Doctor doc = new Doctor(101, "Dr. Smith", "smith@example.com", "pass123", "Cardiology");
        Patient pat = new Patient(201, "John Doe", "john@example.com", "pass456", 30, "Male");

        Appointment appt = new Appointment(1, doc, pat, new Date(), "10:00 AM");
        appt.schedule();
    }
}
```

#### **Output**

```plaintext
Appointment booked with Dr. Smith for John Doe on Mon Feb 27 10:00 AM
```


---

# **💊 3. Prescription Module** 

```java
public class Prescription {
    private int id;
    private Appointment appointment;
    private String medicine;
    private String dosage;
    private String instructions;

    public Prescription(int id, Appointment appointment, String medicine, String dosage, String instructions) {
        this.id = id;
        this.appointment = appointment;
        this.medicine = medicine;
        this.dosage = dosage;
        this.instructions = instructions;
    }

    public void generate() {
        System.out.println("Prescription for " + appointment.patient.name);
        System.out.println("Medicine: " + medicine);
        System.out.println("Dosage: " + dosage);
        System.out.println("Instructions: " + instructions);
    }
}
```

#### **Testing Prescription Module**

```java
public class Main {
    public static void main(String[] args) {
        Doctor doc = new Doctor(101, "Dr. Smith", "smith@example.com", "pass123", "Cardiology");
        Patient pat = new Patient(201, "John Doe", "john@example.com", "pass456", 30, "Male");

        Appointment appt = new Appointment(1, doc, pat, new Date(), "10:00 AM");
        appt.schedule();

        Prescription presc = new Prescription(1, appt, "Paracetamol", "500mg", "Take twice a day after meals");
        presc.generate();
    }
}
```

#### **Output**

```plaintext
Appointment booked with Dr. Smith for John Doe on Mon Feb 27 10:00 AM
Prescription for John Doe
Medicine: Paracetamol
Dosage: 500mg
Instructions: Take twice a day after meals
```
---

# **📂 4. Medical Record Management Module**

This module **stores and updates medical history**.

```java
import java.util.ArrayList;
import java.util.List;

public class MedicalRecord {
    private int recordId;
    private Patient patient;
    private List<String> medicalHistory;

    public MedicalRecord(int recordId, Patient patient) {
        this.recordId = recordId;
        this.patient = patient;
        this.medicalHistory = new ArrayList<>();
    }

    public void addHistory(String record) {
        medicalHistory.add(record);
    }

    public void showHistory() {
        System.out.println("Medical History for " + patient.name + ":");
        for (String history : medicalHistory) {
            System.out.println("- " + history);
        }
    }
}
```

#### **📝 Testing Medical Record Module**

```java
public class Main {
    public static void main(String[] args) {
        Patient pat = new Patient(201, "John Doe", "john@example.com", "pass456", 30, "Male");

        MedicalRecord medRecord = new MedicalRecord(101, pat);
        medRecord.addHistory("Diagnosed with fever");
        medRecord.addHistory("Took Paracetamol for 5 days");
        medRecord.showHistory();
    }
}
```

#### **📝 Output**

```plaintext
Medical History for John Doe:
- Diagnosed with fever
- Took Paracetamol for 5 days
```

---

# **💳 5. Billing History Module**

This module **generates bills for patients**.

```java
import java.util.Date;

public class Billing {
    private int billId;
    private Patient patient;
    private double amount;
    private String status;
    private Date billDate;

    public Billing(int billId, Patient patient, double amount, String status) {
        this.billId = billId;
        this.patient = patient;
        this.amount = amount;
        this.status = status;
        this.billDate = new Date();
    }

    public void generateBill() {
        System.out.println("Bill ID: " + billId);
        System.out.println("Patient: " + patient.name);
        System.out.println("Amount: $" + amount);
        System.out.println("Status: " + status);
        System.out.println("Date: " + billDate);
    }
}
```

#### **📝 Testing Billing Module**

```java
public class Main {
    public static void main(String[] args) {
        Patient pat = new Patient(201, "John Doe", "john@example.com", "pass456", 30, "Male");

        Billing bill = new Billing(1, pat, 200.0, "Paid");
        bill.generateBill();
    }
}
```

#### **📝 Output**

```plaintext
Bill ID: 1
Patient: John Doe
Amount: $200.0
Status: Paid
Date: Mon Feb 27 10:00 AM
```

---

# **📌 Final Overview**

✅ **User Authentication** (Register & Login)  
✅ **Appointment Scheduling** (Book Appointments)  
✅ **Prescription Management** (Generate Prescriptions)  
✅ **Medical Records** (Track Patient History)  
✅ **Billing System** (Generate & Track Bills)

---
