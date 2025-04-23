## 💻 What is a Computer Network?

A **computer network** is a group of connected devices (like computers, printers, etc.) that can **communicate** and **share resources** such as data, software, and hardware.

- The connected devices are called **nodes**.
    
- A **node** can send or receive data (e.g., a computer, printer).
    
- The connection lines are called **communication channels**.
    
- The **Internet** is the best example of a computer network.
    

---

## ✅ Main Requirements of a Good Network:

1. **Performance** – How fast the network responds.
    
2. **Reliability** – How often the network fails.
    
3. **Scalability** – Can the network grow easily?
    

---

## 📈 Performance of a Network:

- **Transit Time**: Time taken for data to travel from one device to another.
    
- **Response Time**: Time between sending a request and getting a reply.
    
- Also depends on:
    
    - Software efficiency
        
    - Number of users
        
    - Hardware capability
        

---

## 🔒 Reliability of a Network:

- Measures how **often** it fails.
    
- To improve: Use better devices, cables, software, etc.
    

---

## 🔐 Security of a Network:

- Protects **data** from unauthorized access.
    
- Data can be hacked while traveling, so **security is very important**.
    

---

## 🌟 Features of a Good Network:

1. **Communication** – Emails, chats, video calls, etc.
    
2. **Resource Sharing** – Share printers, scanners, etc.
    
3. **File Sharing** – Authorized users can share files and data.
    

---

## 🔄 Basic Communication Model (How data moves):

1. **Source** – The device that creates the data (e.g., a computer).
    
2. **Transmitter** – Converts the data into signals (e.g., a modem).
    
3. **Transmission System** – The path the signal travels (wires or wireless).
    
4. **Receiver** – Gets the signal and converts it back to data.
    
5. **Destination** – The device that receives and uses the data.
    

---

## 📡 What is Data Communication?

**Data communication** is the transfer of data between two devices using a medium (like a wire or Wi-Fi).

- Data is sent as **0s and 1s (binary)**.
    
- It needs a **communication system** (like modems, routers).
    

### Types of Data Communication:

1. **Local** – Devices are close (same room/building).
    
2. **Remote** – Devices are far away (different cities/countries).
    

### Features of Good Data Communication:

- **Delivery**: Goes to the correct device.
    
- **Timeliness**: Arrives on time.
    
- **Accuracy**: No errors in data.
    

---

## 📦 Components of Data Communication:

1. **Message** – The information being sent.
    
2. **Sender** – The person/device sending it.
    
3. **Receiver** – The person/device getting it.
    
4. **Medium** – The path used (like cables, Wi-Fi).
    
5. **Protocol** – Set of rules to manage communication.

### 🔌 **Uses of Computer Networks (CN) in Simple Terms:**

1. **Sharing Files and Data 📁**  
    Computers in a network can send and receive files like documents, photos, videos, etc., easily.
    
2. **Sharing Hardware 🖨️**  
    Devices like printers, scanners, and hard drives can be shared among multiple computers, saving money.
    
3. **Communication 💬**  
    People can chat, email, or video call using services over the network — fast and easy communication.
    
4. **Accessing the Internet 🌐**  
    Networks connect computers to the internet, allowing browsing, streaming, downloading, and more.
    
5. **Centralized Data Storage 💾**  
    Data can be stored in one central place (like a server), so it's easy to access and manage.
    
6. **Remote Access 🏠➡️🏢**  
    You can access files and computers from different locations — very helpful for remote work or learning.
    
7. **Backup and Security 🔐**  
    Networks can automatically back up data and apply security rules like firewalls and antivirus across all connected computers.

## 🔗 Line Configuration in Computer Networks

A **network** connects devices (like computers, printers) through **connection links**. There are **two ways** to connect devices:

1. **Point-to-Point Connection**
    
2. **Multipoint Connection**
    

---

### 1. 📞 **Point-to-Point Connection**

![[Pasted image 20250422233112.png]]![[Pasted image 20250422233115.png]]
- **Definition**: A **direct link** between two devices.
    
- **Examples**:
    
    - A computer connected to another computer using a **telephone line**.
        
    - A **remote control** communicating with a **television** to change channels.
        
- **Types of Links**:
    
    - **Wire links** (e.g., Ethernet cables).
        
    - **Microwave links**.
        
    - **Satellite links**.
        

---

### 2. 📡 **Multipoint Connection** (also called **Multidrop Configuration**)
![[Pasted image 20250422233057.png]]
- **Definition**: **Multiple devices share** a single connection link.
    
- **Two Types of Multipoint Connections**:
    
    - **Spatially Shared**: Many devices use the link **simultaneously** (e.g., Wi-Fi where multiple devices share the same frequency).
        
    - **Time Shared (Temporal)**: Devices take turns using the link (e.g., a network where devices use the link one after another in a set time slot).


## 🖥️ **Types of Computer Network Topologies**

Network topology is the arrangement or layout of devices (nodes) and the links that connect them. Let’s explore different topologies.

---

### 1. **Bus Topology**
![[Pasted image 20250422234712.png|400]]
- **Description**: All devices share a **single communication line** (bus).
    
- **Types**:
    
    - **Linear Bus**: Exactly two endpoints.
        
- **Features**:
    
    - **Unidirectional** data transmission.
        
    - Simple and cost-effective.
        
- **Advantages**:
    
    - **Low cost** and **simple setup**.
        
    - **Easy to expand**.
        
- **Disadvantages**:
    
    - If the cable fails, **entire network fails**.
        
    - Performance drops with **high traffic** or more devices.
        

---

### 2. **Ring Topology**
![[Pasted image 20250422234701.png|400]]

- **Description**: Devices are connected in a **ring**, each device connected to two others.
    
- **Features**:
    
    - Data moves in a **unidirectional** or **bidirectional** (Dual Ring) manner.
        
    - Uses **repeaters** to prevent data loss, especially in large networks.
        
- **Advantages**:
    
    - **Consistent performance** despite traffic.
        
    - **Cheap to install**.
        
- **Disadvantages**:
    
    - **Troubleshooting is tough**.
        
    - Failure of one device can disrupt the entire network.
        

---

### 3. **Star Topology**
![[Pasted image 20250422234648.png|400]]
- **Description**: Every device connects to a **central hub**.
    
- **Features**:
    
    - Hub acts as a **data repeater**.
        
    - Can use **twisted pair, fiber optics**, or **coaxial cables**.
        
- **Advantages**:
    
    - **Easy to troubleshoot** and **expand**.
        
    - Only the **failed node** is affected.
        
- **Disadvantages**:
    
    - High installation cost.
        
    - Hub failure **stops the entire network**.
        

---

### 4. **Mesh Topology**
![[Pasted image 20250422234635.png|400]]
- **Description**: Every device is directly connected to all other devices (fully connected).
    
- **Transmission Methods**:
    
    - **Routing**: Directs data using logic to find the shortest path.
        
    - **Flooding**: Sends data to all nodes, no routing needed.
        
- **Types**:
    
    - **Full Mesh**: Every device is connected.
        
    - **Partial Mesh**: Some devices are connected directly, others are connected to two or three.
        
- **Advantages**:
    
    - **Robust** and **secure**.
        
    - Faults can be easily identified.
        
- **Disadvantages**:
    
    - **High cabling cost**.
        
    - **Complex to set up**.
        

---

### 5. **Tree Topology** (Hierarchical Topology)
![[Pasted image 20250422234623.png|400]]
- **Description**: Devices form a hierarchy, with a **root node** at the top.
    
- **Features**:
    
    - Combines characteristics of **star** and **bus topologies**.
        
- **Advantages**:
    
    - **Easy expansion** and **management**.
        
    - **Easy error detection**.
        
- **Disadvantages**:
    
    - **Heavily cabled**.
        
    - **Costly** to implement.
        

---

### 6. **Hybrid Topology**
![[Pasted image 20250422234417.png|400]]

- **Description**: Combines two or more topologies (e.g., Ring + Star).
    
- **Features**:
    
    - Inherits advantages and disadvantages from all combined topologies.
        
- **Advantages**:
    
    - **Scalable** and **reliable**.
        
    - **Easy error detection** and **troubleshooting**.
        
- **Disadvantages**:
    
    - **Complex design**.
        
    - **Expensive** to set up.
        

---

Each topology has its own set of strengths and weaknesses, making it suitable for different environments and network requirements. The choice of topology largely depends on the **size of the network**, **budget**, and the **maintenance capabilities**.

### **Different Types of Transmission Modes in Computer Networks**

Transmission modes define how data flows between devices in a network. There are three primary transmission modes: **Simplex**, **Half Duplex**, and **Full Duplex**. Each mode determines the direction of data flow between sender and receiver.

---

### 1. **Simplex Mode**
![[Pasted image 20250422234943.png|400]]
- **Description**: In **Simplex Mode**, data is transmitted in **only one direction**. It is **unidirectional communication**, meaning the sender can send data, but the receiver cannot send any response back to the sender.
    
- **Example**:
    
    - **Loudspeakers**: Sound is broadcasted in one direction from a source.
        
    - **Television Broadcasting**: TV stations send signals to viewers, but viewers can’t send a signal back to the station.
        
    - **Keyboard to Computer**: Keyboard sends keystrokes to the computer but does not receive any data in return.
        
- **Key Points**:
    
    - One-way communication.
        
    - No feedback or acknowledgment from the receiver.
        

---

### 2. **Half-Duplex Mode**

![[Pasted image 20250422234957.png|400]]
- **Description**: In **Half-Duplex Mode**, data can flow in **both directions**, but **not at the same time**. Devices take turns to send and receive data, meaning one device transmits while the other receives, and vice versa.
    
- **Example**:
    
    - **Walkie-Talkie**: One person speaks, and the other listens. Then they switch roles to communicate in both directions, but never at the same time.
        
    - **LAN with Half-Duplex Technology**: One workstation sends data while others may listen, but only one device can transmit at a time.
        
- **Key Points**:
    
    - **Bidirectional communication**, but **not simultaneous**.
        
    - Devices alternate between sending and receiving.
        

---

### 3. **Full-Duplex Mode**

- **Description**: In **Full-Duplex Mode**, data can be transmitted **simultaneously** in both directions. This allows for continuous two-way communication without the need to take turns.
    
- **Example**:
	    ![[Pasted image 20250422235039.png|400]]
    - **Telephone Networks**: Both parties can talk and listen at the same time.
        
    - **Modern Network Connections**: Devices like routers and computers communicate in both directions at once without interruption.
        
- **Key Points**:
    
    - **Simultaneous two-way communication**.
        
    - **Two separate channels** may be used—one for sending data and another for receiving.
    - ![[Pasted image 20250422235017.png|400]]
        
    - More efficient for real-time communication.
        

---

### Summary of Transmission Modes:

|Mode|Direction of Data Flow|Example|
|---|---|---|
|**Simplex**|One-way|Loudspeakers, TV Broadcasting|
|**Half-Duplex**|Two-way, but not simultaneous|Walkie-talkies, LANs with half-duplex|
|**Full-Duplex**|Two-way, simultaneous|Telephones, modern network connections|

Each transmission mode is chosen based on the specific needs of the network and the type of communication required. Simplex is used when only one-way communication is needed, Half-Duplex is suited for systems where both directions of communication are required, but not at the same time, and Full-Duplex is best for real-time, two-way communication.

### **Different Types of Transmission Mediums**
![[Pasted image 20250423000550.png|600]]
In computer networks and telecommunications, transmission mediums are the physical paths through which data is sent from one device to another. Data is represented using signals, and these signals can travel through a variety of mediums, either wired (bounded) or wireless (unbounded). The choice of transmission medium affects the speed, distance, cost, and reliability of the communication.

---

### **1. Wired or Bounded Transmission Mediums**

Wired transmission mediums use physical cables or conductors to carry signals. These cables are used in local and wide-area networks, and are typically more secure and faster than wireless mediums, though they may be more expensive and complex to install.

#### **a. Twisted Pair Cable**

- **Description**: Consists of pairs of insulated copper wires twisted together. These are the most commonly used cables in networking.
    
- **Types**:
    
    - **Unshielded Twisted Pair (UTP)**: Common in Ethernet networks, UTP is widely used but is vulnerable to electromagnetic interference (EMI).
        
    - **Shielded Twisted Pair (STP)**: Includes a shield around the copper wires to reduce EMI, making it suitable for environments with high interference.
        
- **Speed & Distance**: UTP supports speeds up to **10 Gbps** over short distances (up to 100 meters for Cat6a cables).
    
- **Applications**: **Local Area Networks (LANs)**, telecommunication networks.
    

#### **b. Coaxial Cable**

- **Description**: Composed of a single copper conductor at the center, surrounded by insulation, a metallic shield, and an outer insulating layer.
    
- **Speed & Distance**: Supports speeds up to **10 Gbps** and can cover distances of up to **500 meters**.
    
- **Applications**: **Cable television networks**, early Ethernet networks (**10BASE2, 10BASE5**).
    

#### **c. Fiber Optic Cable**

- **Description**: Uses light pulses to transmit data through strands of glass or plastic fibers, which offers high-speed and long-distance communication.
    
- **Types**:
    
    - **Single-mode Fiber (SMF)**: A small core size for long-distance communication (up to **100 km**).
        
    - **Multi-mode Fiber (MMF)**: A larger core for shorter distances (up to **2 km**).
        
- **Speed & Distance**: Can support **very high speeds** (up to **100 Gbps**) over long distances.
    
- **Applications**: **Backbone networks**, **high-speed internet**, long-distance telecommunications.
    

---

### **2. Wireless or Unbounded Transmission Mediums**

Wireless transmission mediums use electromagnetic waves to carry data without the need for physical cables. Wireless technologies are crucial in providing mobile communication and remote access.

#### **a. Radio Waves**

- **Description**: Uses radio frequencies (RF) to transmit data wirelessly through the air.
    
- **Range**: Can vary from a few meters (Bluetooth) to several kilometers (Wi-Fi, cellular networks).
    
- **Applications**: **Wi-Fi**, **cellular networks (2G, 3G, 4G, 5G)**, **Bluetooth**.
    

#### **b. Microwaves**

- **Description**: High-frequency radio waves (1 GHz to 300 GHz) used for point-to-point communication.
    
- **Range**: Supports long-distance communication with line-of-sight transmission.
    
- **Applications**: **Satellite communication**, **point-to-point links**, **microwave ovens**.
    

#### **c. Infrared (IR)**

- **Description**: Uses infrared light to transmit data over short distances. Typically requires line-of-sight communication.
    
- **Range**: Limited to short distances (a few meters).
    
- **Applications**: **Remote controls**, short-range communication between devices (like infrared ports on laptops, printers).
    

#### **d. Satellite Communication**

- **Description**: Uses satellites in space to relay data between ground stations.
    
- **Range**: Provides global coverage and is ideal for long-distance and remote-area communication.
    
- **Applications**: **Global Positioning Systems (GPS)**, **satellite internet**, **television broadcasting**.
    

---

### **Factors to Consider When Selecting a Transmission Medium**

When selecting a transmission medium, several factors need to be taken into account to ensure the communication system meets the desired performance and cost requirements:

1. **Transmission Rate**: How fast data can be transmitted. Fiber optics provide the highest speeds, while wireless solutions may vary based on technology and range.
    
2. **Cost and Ease of Installation**: Wired mediums, like fiber optics, may be more expensive and complex to install, while wireless solutions are often easier to deploy in certain scenarios.
    
3. **Resistance to Environmental Conditions**: Some transmission mediums (like fiber optics) are more resistant to environmental factors (e.g., electromagnetic interference) than others, such as UTP cables.
    
4. **Distance**: The maximum distance over which data can be transmitted without significant signal degradation. For instance, fiber optics can carry data much further than copper cables.
    
5. **Security of the Network**: Wired connections are generally more secure than wireless ones, as it is harder to intercept data over physical cables than through the air.
    

---

### **Summary of Transmission Mediums**

|**Medium**|**Type**|**Speed**|**Distance**|**Applications**|
|---|---|---|---|---|
|**Twisted Pair Cable**|UTP, STP|Up to 10 Gbps|Up to 100m|LANs, telecommunication networks|
|**Coaxial Cable**|Copper + Shield|Up to 10 Gbps|Up to 500m|Cable TV, early Ethernet networks|
|**Fiber Optic Cable**|SMF, MMF|Up to 100 Gbps|Up to 100 km|Backbone networks, high-speed internet, telecom|
|**Radio Waves**|RF|Varies (Low to High)|Varies|Wi-Fi, cellular, Bluetooth|
|**Microwaves**|Point-to-point RF|High (up to 10 Gbps)|Long-distance|Satellite communication, microwave links|
|**Infrared (IR)**|Infrared Light|Low to Medium|Short (few meters)|Remote controls, short-range device comms|
|**Satellite Communication**|Satellite Links|Low to High|Global|GPS, satellite internet, TV broadcasting|

Each transmission medium has its strengths and weaknesses, and the right choice depends on factors like the required speed, distance, and environmental conditions.