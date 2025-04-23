
### 🔍 What is QoS?

Quality of Service (QoS) is the **ability to prioritize** certain applications, users, or data flows to **guarantee performance** in terms of reliability, delay, jitter, and bandwidth.

---

### 📌 Flow Characteristics

|Characteristic|Description|
|---|---|
|**Reliability**|Ensures packets are delivered correctly. Important for email, file transfers, etc.|
|**Delay**|Time taken for a packet to go from source to destination. Critical in video/audio calls.|
|**Jitter**|Variation in delay between packets. Lower jitter = smoother playback.|
|**Bandwidth**|Amount of data transmitted per time unit. Varies by application needs.|

---

### 🛠 How to Achieve QoS

#### 🔁 Jitter Buffer

- Temporarily stores incoming packets.
    
- Smooths packet arrival during congestion.
    

#### 🧩 Traffic Shaping (Packet Shaping)

- Controls congestion by **delaying low-priority packets**.
    
- Regulates network traffic flow.
    

---

### 📃 QoS in Service-Level Agreements (SLA)

Service providers often define QoS expectations in SLAs, guaranteeing certain performance metrics.

---

### 🧠 QoS Solutions

|Type|Description|
|---|---|
|**Stateless**|No session state maintained. Scalable, but less reliable.|
|**Stateful**|Keeps per-flow/session state. Powerful and reliable, but less scalable.|

---

### 📊 QoS Parameters

|Parameter|Description|
|---|---|
|**Packet Loss**|Packets dropped due to congestion. Causes quality issues in real-time apps.|
|**Jitter**|Delay variation caused by congestion, drift, etc.|
|**Latency**|Time taken by a packet to reach its destination. Should be minimal.|
|**Bandwidth**|Maximum data transferred per second. Higher is better.|
|**Mean Opinion Score (MOS)**|1–5 rating for audio quality (5 = best).|

---

### 🧩 QoS Implementation Models

#### 1. **Best Effort**

- No prioritization.
    
- No guarantee of delivery.
    
- Used when no QoS policies exist.
    

#### 2. **Integrated Services (IntServ)**

- **Reserves resources** per application flow.
    
- Requires **RSVP** and IntServ-capable routers.
    
- High accuracy, but **not scalable**.
    

#### 3. **Differentiated Services (DiffServ)**

- Classifies traffic and assigns **priority levels**.
    
- No need for resource reservation.
    
- **Highly scalable**, modern networks use this.
    

---

### ⚖️ IntServ vs. DiffServ

|Feature|Integrated Services (IntServ)|Differentiated Services (DiffServ)|
|---|---|---|
|Scope|End-to-end|Domain-based|
|Reservation|Required|Not required|
|Setup|Per-flow|Long-term|
|Scalability|Low|High|
|Also Called|IntServ|DiffServ|