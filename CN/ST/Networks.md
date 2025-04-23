## 🔗 Types of Computer Networks

Computer networks are categorized based on their geographical span and design. The five major types are:

1. **Local Area Network (LAN)**
    
2. **Metropolitan Area Network (MAN)**
    
3. **Wide Area Network (WAN)**
    
4. **Wireless Networks**
    
5. **Internetwork (Internet)**
    
![[Pasted image 20250423175854.png]]
---

### 1. 🖥️ Local Area Network (LAN)
![[Pasted image 20250423175902.png]]
**Definition:**  
A LAN connects computers within a limited area such as an office, building, or campus.

**Topologies Used:** Star, Ring, Bus, Tree

#### ✅ Characteristics:

- Private network not subject to government control.
    
- High data transfer speeds.
    
- Common access methods: Ethernet, Token Ring.
    
- Covers a small, restricted area.
    

#### 💡 Applications:

- File and resource sharing (printers, storage).
    
- Centralized data and software usage via servers.
    
- Local communication between computers.
    

#### 👍 Advantages:

- **Resource Sharing** reduces hardware costs.
    
- **Centralized Data** enhances security and accessibility.
    
- **Software Sharing** minimizes licensing costs.
    
- **Internet Sharing** through a single connection.
    

#### 👎 Disadvantages:

- **High Initial Cost** of setup and installation.
    
- **Limited Coverage** to small geographical areas.
    
- **Privacy and Security Risks** if not well-managed.
    
- **Requires Maintenance** by a network administrator.
    

---

### 2. 🏙️ Metropolitan Area Network (MAN)

**Definition:**  
A MAN spans a city or large campus and can connect multiple LANs.
![[Pasted image 20250423175908.png]]
#### ✅ Characteristics:

- Covers areas up to 50 km.
    
- Uses high-speed media like optical fibers.
    
- Usually operated by public or private entities.
    

#### 👍 Advantages:

- **High-Speed Communication** over a wide area.
    
- **Supports Multiple LANs**, useful for large organizations.
    
- **Bi-Directional Data Flow** through dual bus systems.
    

#### 👎 Disadvantages:

- **Higher Cabling Costs** for long-distance connections.
    
- **Security Risks** due to wider accessibility.
    

---

### 3. 🌍 Wide Area Network (WAN)
![[Pasted image 20250423175914.png]]
**Definition:**  
A WAN connects computers across large distances, such as countries or continents.

**Mediums Used:** Satellite, PSTN, public telephone networks

#### ✅ Characteristics:

- Covers large geographical areas.
    
- Utilizes routers and public networks.
    
- Lower speed compared to LAN/MAN.
    

#### 👍 Advantages:

- **Connects Distant Locations** for global businesses.
    
- **Shares Centralized Resources** like servers and internet lines.
    
- **Supports Multimedia Communication** (email with attachments, etc.).
    

#### 👎 Disadvantages:

- **Expensive to Set Up and Maintain**
    
- **Security Challenges** like hacking and data theft.
    
- **Slower Data Transfer Speeds**
    
- **Requires Constant Monitoring** by IT staff.
    

---

### 4. 📶 Wireless Networks
![[Pasted image 20250423175935.png]]
**Definition:**  
Networks using radio signals for data transmission, eliminating physical cables.

#### 📂 Categories:

1. **System Interconnection** – Short-range (e.g., Bluetooth for devices like keyboards, printers).
    
2. **Wireless LANs (WLANs)** – Used in homes and offices; standard: IEEE 802.11.
    
3. **Wireless WANs (WWANs)** – Used for mobile communication (cell phones).
    

#### 📜 Generations of Wireless WAN:

- **1G:** Analog voice only
    
- **2G:** Digital voice
    
- **3G+:** Digital voice and data (multimedia)
    

---

### 5. 🌐 Inter Network (Internet)
![[Pasted image 20250423175927.png]]
**Definition:**  
The Internet is a global system that interconnects multiple networks (LANs, WANs, etc.) via routers, gateways, and bridges.

#### 🔧 Components:

- **Routers:** Direct data packets between networks.
    
- **Gateways:** Connect networks with different protocols.
    
- **Bridges:** Connect and filter traffic between LAN segments.
  

### ✅ **Connection-Oriented vs. Connectionless Services**

|Feature|Connection-Oriented Service|Connectionless Service|
|---|---|---|
|**Process**|1. Connection established2. Data transferred3. Connection released|No setup needed; data sent directly|
|**Reliability**|High — ensures delivery and retransmits if needed|Lower — no guarantee of delivery|
|**Example Protocol**|TCP (Transmission Control Protocol)|UDP (User Datagram Protocol)|
|**Authentication**|Required|Not required|
|**Data Stream**|Stream-based|Message-based|
|**Delivery Order**|Maintains message order|Messages may arrive out of order|
|**Use Case Analogy**|Telephone call (conversation setup)|Postal mail (drop and go)|

---

### 📡 **Service Primitives**

Primitives are the basic operations (functions/system calls) that define how communication services are accessed by user programs.

#### 🔁 **Connection-Oriented Service Primitives**

|Primitive|Purpose|
|---|---|
|`LISTEN`|Waits for an incoming connection (used by server)|
|`CONNECT`|Client initiates connection to server|
|`RECEIVE`|Waits for and receives messages|
|`SEND`|Sends data to the connected peer|
|`DISCONNECT`|Terminates the established connection|

#### 📦 **Connectionless Service Primitives**

|Primitive|Purpose|
|---|---|
|`UNIDATA`|Sends a packet of data (no connection)|
|`FACILITY`|Inquires about network performance|
|`REPORT`|Reports delivery stats and diagnostics|

---

### 🔄 **Relationship Between Services and Protocols**

|Concept|Description|
|---|---|
|**Services**|Define _what_ operations are available to the upper layers (e.g., SEND, RECEIVE)|
|**Protocols**|Define _how_ the data is formatted and transferred between peer entities|

- **Services** act like **menus** in a restaurant — what you can order.
    
- **Protocols** are like **recipes** — how the ordered food is prepared and served.
    

---

### 🔎 Visual Concept (Optional for Notes)

```
Application Layer
    ↑  (Uses Services)
Transport Layer
    ↑  (Implements using Protocols)
Network Layer
```

---

![[Pasted image 20250423181003.png|300]]