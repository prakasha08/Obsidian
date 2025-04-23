# 🧠 Network Layer – OSI Model Layer 3

- **Main job**: Responsible for **end-to-end delivery** of individual **packets**.
    
- **Scope**: From source host to destination host, possibly across **multiple networks** (internetworking).
    
- Think: “How does the packet travel across different routers/networks to reach the final destination?”
    

---

## 🧱 Key Responsibilities of Network Layer

### 1. **Logical Addressing**

- Each device on a network is given a **logical address (IP Address)**.
    
- Physical (MAC) addresses are **local to a network segment**, but IP addresses are **global** and help in **routing** between networks.
    

📌 Example:  
Source IP: `192.168.1.5` → Destination IP: `172.217.0.46` (Google server)

---

### 2. **Routing** 🧭

- **Routers** use **routing tables** to determine the best path.
    
- Path selection can be **static** (fixed) or **dynamic** (based on conditions like network congestion).
    
- Uses **routing protocols**: RIP, OSPF, BGP.
    

📌 Routing Example:

text

CopyEdit

`PC A (192.168.1.10)  ↓ Router 1 (gateway for A)  ↓ (decides path) Router 2 (intermediate hop)  ↓ Router 3 (connected to target)  ↓ PC B (10.0.0.25)`

---

### 3. **Fragmentation & Reassembly** 🧩

- If a packet is **too big** for the next network (exceeds MTU), it's **fragmented**.
    
- Fragments are:
    
    - Labeled with an **Identification number**
        
    - Marked with **Fragment Offset** and **More Fragments (MF)** flag
        
- **Reassembly** happens **only at the destination**.
    

📌 Real-life case:

- MTU = 1500 bytes
    
- IP packet = 4000 bytes → split into 3 fragments
    

---

### 4. **Connection Services**

- Though IP is **connectionless**, higher-level features might include:
    
    - **Flow control**: Manage rate of data flow (rare in network layer; mostly done in transport layer)
        
    - **Error control**: Not handled well in IP layer – left to TCP (Transport Layer)
        
    - **Packet sequence control**: Used to reassemble out-of-order fragments
        

---

### 5. **Congestion Control** 🚦

- If too many packets are sent into the network → **congestion** (packets lost/delayed)
    
- Causes: Too much traffic, slow routers, insufficient buffer
    
- Methods to handle:
    
    - **Rate limiting**: Restricting number of packets sent
        
    - **Load balancing**: Distributing traffic across multiple paths
        

---

### 6. **Quality of Service (QoS)** 🎯

QoS defines **how well the network delivers**:

- **Delay** (latency)
    
- **Throughput**
    
- **Packet loss**
    
- **Jitter** (variation in delay)
    

Used in:

- **Streaming**, **VoIP**, **real-time apps**
    

---

### 7. **Source-to-Destination Delivery**

Visual Example:

![[Pasted image 20250423230832.png|400]]

`A (192.168.1.10)  ↓ Router B (analyzes destination)  ↓ Router E (next hop as per B’s routing table)  ↓ F (final destination 10.0.0.1)`

At each router:

- It reads the **destination IP**
    
- Chooses the **next hop**
    
- Forwards the packet to the next router
    

---

## 🚫 Limitations / Design Issues in Network Layer

|Issue|Explanation|
|---|---|
|**Flow Control**|Generally absent at network layer; handled at transport layer.|
|**Error Control**|IP does **not ensure** delivery – no retransmission on error.|
|**Congestion**|More packets → bottlenecks, delay, drop.|
|**Protocol mismatch**|Different networks may use different packet sizes or addressing schemes.|
|**Security**|Basic IP layer lacks security (can be added using IPSec).|

---

## 🔁 Services Offered by Network Layer

|Service|Description|
|---|---|
|**Guaranteed delivery**|Provided in connection-oriented protocols, like X.25 (not in IP)|
|**Bounded delay**|Important for real-time apps; hard to guarantee in IP|
|**In-order delivery**|Only possible if fragmentation & reassembly are managed|
|**Security**|Achieved using protocols like IPsec|

---

## 📚 Summary Table

|Feature|Handled by Network Layer?|
|---|---|
|Logical addressing|✅|
|Routing|✅|
|Fragmentation|✅|
|Flow Control|❌|
|Error Control|❌|
|Congestion Handling|Partially|
|Packet Ordering|Partially|
|Security|Limited (via extensions like IPsec)|
# 🌐 **Network Layer in Computer Networks (CN)**

---

### ✅ **Definition:**

The **Network Layer** is the **third layer** in the **OSI (Open Systems Interconnection) model**.  
It is responsible for **delivering data from source to destination** across multiple networks. It determines the **best path** for data packets to travel.

📍 In simple terms:  
🔹 “The Network Layer decides _where_ the data should go and _how_ to get there.”

---

### 🔹 **Main Functions of the Network Layer:**

1. ### **Routing:**
    
    - Determines the **best route** for the data to travel from sender to receiver.
        
    - Uses routing algorithms and routing tables.
        
    - Involves routers that forward packets based on IP addresses.
        
2. ### **Logical Addressing (IP Addressing):**
    
    - Assigns **unique addresses** (IP addresses) to devices on a network.
        
    - Helps in identifying the **source and destination** of data packets.
        
    - Example: IPv4 (like 192.168.1.1), IPv6.
        
3. ### **Packet Forwarding:**
    
    - Moves packets **from one network to another** using routers.
        
    - Involves examining the destination IP address and deciding the next hop.
        
4. ### **Fragmentation and Reassembly:**
    
    - Breaks large packets into smaller ones (fragmentation) to match the size supported by the network.
        
    - Reassembles the packets at the destination.
        
5. ### **Error Handling and Diagnostics (Limited):**
    
    - Basic error reporting (e.g., destination unreachable).
        
    - Uses tools like ICMP (Internet Control Message Protocol).
        

---

### 🔹 **Key Devices at Network Layer:**

- **Router:** Core device that operates at this layer, forwards packets based on IP addresses.
    
- **Layer 3 Switches:** Used in advanced LAN routing.
    

---

### 🔹 **Protocols Used at Network Layer:**

| Protocol                                      | Description                                                                                                                                                                                                                                                                             |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **IP (Internet Protocol)**                    | Main protocol for addressing and routing.                                                                                                                                                                                                                                               |
| **ICMP (Internet Control Message Protocol)**  | Used for error messages and diagnostics (e.g., ping(A ping (Packet Internet or Inter-Network Groper) is **a basic Internet program that allows a user to test and verify if a particular destination IP address exists and can accept requests in computer network administration**.)). |
| **IGMP (Internet Group Management Protocol)** | Manages group memberships for multicast communication.                                                                                                                                                                                                                                  |
| **IPsec**                                     | Provides security for IP packets (encryption and authentication).                                                                                                                                                                                                                       |

---

### 🔹 **Services Provided by Network Layer:**

- **Connectionless service:** Each packet travels independently (e.g., IP).
    
- **Connection-oriented service:** Guarantees delivery in sequence (less common in the network layer, more at the transport layer).
    

---

### 🔹 **Examples of Network Layer Activities:**

- Sending a message from one city to another over the internet.
    
- Using a router at home to access a website hosted in another country.
    
- Devices in different networks communicating with each other using IP addresses.
    

---

### 🔹 **Comparison with Other OSI Layers:**

|Layer|Function|Example Device/Protocol|
|---|---|---|
|**Transport Layer**|Reliable delivery of data between apps|TCP, UDP|
|**Network Layer**|Routing and addressing across networks|IP, ICMP, Router|
|**Data Link Layer**|Communication within the same network|MAC Address, Switch, Ethernet|

---

### ✅ **Summary (For Quick Revision):**

- **Layer Number:** 3rd Layer of OSI model.
    
- **Main Role:** Routing, addressing, and delivering data across networks.
    
- **Key Concepts:** IP Address, Routing, Packet Forwarding, Fragmentation.
    
- **Devices Used:** Routers, Layer 3 Switches.
    
- **Protocols:** IP, ICMP, IGMP, IPsec.

## 🌐 **Network Layer Protocols – In Detail**

---

### 🔹 1. **IP (Internet Protocol)**

#### ✅ **Purpose:**

The **Internet Protocol (IP)** is the **primary protocol** used to **identify devices** and **route data** from source to destination across multiple networks.

#### 📦 **How IP Works:**

- Each device on a network has an **IP address** (like your home has an address).
    
- Data is broken into **packets**.
    
- Each packet contains:
    
    - **Source IP Address** (sender)
        
    - **Destination IP Address** (receiver)
        
- Routers use these IP addresses to **forward** the packets to the right path.
    

#### 📘 **Types of IP:**

- **IPv4:** 32-bit address (e.g., 192.168.0.1)
    
- **IPv6:** 128-bit address (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334) – used as IPv4 becomes limited.
    

#### 🚚 **Data Flow using IP:**

nginx

CopyEdit

`Application → Transport Layer → IP adds address info → Routed → Destination`

---

### 🔹 2. **ICMP (Internet Control Message Protocol)**

#### ✅ **Purpose:**

Used for **error reporting** and **diagnostic functions**.

#### 📘 **Common Uses:**

- `ping`: Checks if a host is reachable.
    
- `traceroute`: Finds the path data takes to reach a host.
    

#### ⚙️ **How ICMP Works:**

- If a packet **can’t reach its destination** (e.g., no route), the router sends back an **ICMP error message** to the sender.
    
- Does **not carry application data**, only control messages.
    

#### 🛠️ **Example:**

If your laptop tries to reach a server that’s down:

css

CopyEdit

`Laptop sends IP packet → Router can’t deliver → ICMP “Destination Unreachable” sent back to laptop`

---

### 🔹 3. **IGMP (Internet Group Management Protocol)**

#### ✅ **Purpose:**

Used for **multicast communication**, where data is sent from one source to **multiple receivers** (like live streaming).

#### 📘 **Key Concepts:**

- Devices **join or leave** multicast groups using IGMP.
    
- Used mainly by routers and hosts to manage group membership.
    

#### 🛰️ **How IGMP Works:**

1. A host wants to receive a live video stream (multicast).
    
2. It sends an IGMP message to the router to **join the group**.
    
3. The router keeps track and forwards multicast packets only to group members.
    

---

### 🔹 4. **IPsec (Internet Protocol Security)**

#### ✅ **Purpose:**

Used to **secure IP communications** by **encrypting** and **authenticating** packets at the network layer.

#### 🔐 **Security Features:**

- **Authentication:** Confirms that the packet is from a legitimate source.
    
- **Encryption:** Ensures that no one can read the data in transit.
    
- **Integrity:** Verifies that the packet has not been altered.
    

#### 🧩 **How IPsec Works:**

- Works in two modes:
    
    - **Transport Mode:** Encrypts only the **data portion** of IP packet.
        
    - **Tunnel Mode:** Encrypts the **entire packet**.
        
- Often used in **VPNs (Virtual Private Networks)** to securely connect two networks or users over the internet.
    

---

### 📌 **Summary Table of Network Layer Protocols:**

|Protocol|Purpose|Data Handling|Use Case|
|---|---|---|---|
|**IP**|Routing and addressing|Encapsulates data into packets|Internet data delivery|
|**ICMP**|Error reporting and diagnostics|Sends control messages|Ping, Traceroute|
|**IGMP**|Manages multicast group memberships|Allows multicast group join/leave|Live video streams, IPTV|
|**IPsec**|Secure IP communication|Encrypts/authenticates IP packets|VPN, secure data transmission|

---

### ✅ **How Data is Transferred in the Network Layer:**

markdown

CopyEdit

`1. Application data → Transport layer (e.g., TCP/UDP) 2. Transport layer adds source/destination ports 3. Network layer (IP) adds source/destination IPs 4. Optional: ICMP for errors, IGMP for multicast, IPsec for security 5. Data is packetized and sent through routers 6. Reaches the destination host, where layers unwrap the data`