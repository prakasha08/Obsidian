## 🧩 Devices in Networking (Hub, Switch, Repeater, Router)

|Device|OSI Layer|Function|
|---|---|---|
|**Hub**|Layer 1 - Physical|Broadcasts data to all devices connected to it|
|**Switch**|Layer 2 - Data Link|Sends data only to the device it's meant for, using MAC addresses|
|**Router**|Layer 3 - Network|Routes data between different networks using IP addresses|
|**Repeater**|Layer 1 - Physical|Regenerates weak signals to extend the distance of transmission|

---

### 📦 1. **Hub**

- **Layer:** Physical (Layer 1)
    
- **Function:** Dumb device – just **repeats signals to all ports**.
    
- **Use:** Small local networks for simple setups.
    
- **Drawback:** Causes **collisions**, no filtering or intelligence.
    

🧠 Analogy: Like shouting a message in a room; everyone hears it, even if it’s not for them.

---

### 🧠 2. **Switch**

- **Layer:** Data Link (Layer 2)
    
- **Function:** Uses **MAC addresses** to forward data only to the destination port.
    
- **Use:** LANs (Local Area Networks), replacing hubs in modern networks.
    
- **Advantage:** Reduces collisions, supports full-duplex communication.
    

🧠 Analogy: Like a receptionist forwarding a phone call directly to the correct extension.

---

### 🌐 3. **Router**

- **Layer:** Network (Layer 3)
    
- **Function:** Uses **IP addresses** to forward packets between **different networks**.
    
- **Use:** Connects LANs to WANs or the internet.
    
- **Features:** NAT, firewall, DHCP, routing protocols (like RIP, OSPF, BGP).
    

🧠 Analogy: Like a GPS navigator, deciding the best route to reach another city.

---

### 🔁 4. **Repeater**

- **Layer:** Physical (Layer 1)
    
- **Function:** Amplifies or regenerates weak signals.
    
- **Use:** Extend the length of the network (like long cables).
    
- **Limitation:** Doesn’t understand data; just repeats signals.
    

🧠 Analogy: Like a speaker in a long hallway repeating what someone says so others can hear it clearly.

---

## 🚦 Routing (in Routers)

### 🔍 What is Routing?

Routing is the **process of selecting a path** for traffic in a network, or between networks.

### 🧠 How It Works:

- Routers look at the **destination IP address**.
    
- Use a **routing table** to decide where to send the packet next.
    
- May involve **static routes** (manually set) or **dynamic routes** (using protocols like OSPF, RIP).
    

### 📚 Routing Table Example:

|Destination Network|Next Hop|Interface|
|---|---|---|
|192.168.1.0/24|Direct|eth0|
|10.0.0.0/8|192.168.1.1|eth1|

---

### 🔄 Types of Routing:

|Type|Description|
|---|---|
|**Static Routing**|Manually configured by an admin. Stable, but not flexible.|
|**Dynamic Routing**|Routers learn paths via protocols (OSPF, RIP, BGP). Auto-updates paths.|
|**Default Routing**|Used when the destination isn't found in the routing table. Like a fallback route.|

---

## 🧩 Fragmentation (in Routers and Hosts)

### 🔍 What is Fragmentation?

When a data packet is **too large for the next network segment’s MTU (Maximum Transmission Unit)**, it is **split into smaller fragments**.

### 🔧 Why Fragmentation Happens:

- Different networks support different **maximum frame sizes**.
    
- IP packets larger than MTU need to be **broken down** to pass through.
    

### 📚 How It Works:

1. The IP layer checks the **MTU** of the outgoing link.
    
2. If packet size > MTU, the packet is fragmented.
    
3. Each fragment is given:
    
    - A portion of the original data
        
    - Same **Identification number**
        
    - **Offset** field to help reassembly
        
    - **More Fragments (MF)** bit
        

### 📦 Reassembly:

- Happens at the **destination host** (not routers).
    
- All fragments are collected and reassembled based on the offset and ID.
    

---

### ⚠️ Fragmentation Issues:

- Increased **overhead**
    
- Higher chance of **packet loss**
    
- Not efficient – modern networks prefer **Path MTU Discovery** (to avoid fragmentation)
    

---

## ✅ Quick Summary Table

| Concept       | OSI Layer          | Key Purpose                  |
| ------------- | ------------------ | ---------------------------- |
| Hub           | Layer 1            | Broadcast signals            |
| Switch        | Layer 2            | Send to specific MAC address |
| Router        | Layer 3            | Route based on IP            |
| Repeater      | Layer 1            | Boost weak signals           |
| Routing       | Layer 3            | Path selection using IP      |
| Fragmentation | Layer 3 (IP Layer) | Break big packets to fit MTU |