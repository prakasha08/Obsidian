### 🔌 **Bounded (Wired) Transmission Media Overview**

Bounded media provide a **guided path** for signal transmission. Signals are contained within the medium's physical boundaries.

---

### 1. 🌀 **Twisted Pair Cable (TPC)**

#### 🔸 **General Features:**

- Frequency: 0–3.5 kHz
    
- Attenuation: 0.2 dB/km @1 kHz
    
- Delay: 50 µs/km
    
- Repeater spacing: 2 km
    
- Two insulated copper wires twisted to reduce noise
    

#### 🔹 Types of Twisted Pair:

1. **Unshielded Twisted Pair (UTP)**
    
    - Most common, flexible, cheap
        
    - Connectors: RJ-11 (2-pair), RJ-45 (4-pair)
        
    - 📈 _Used in LANs like Ethernet_
        
    - **Pros**: Easy to install, flexible, cheap
        
    - **Cons**: Lower bandwidth, less interference protection
        
2. **Shielded Twisted Pair (STP)**
    
    - Includes metal foil/braid for shielding
        
    - **Pros**: Less crosstalk, higher capacity, supports analog/digital
        
    - **Cons**: Expensive, harder to manufacture, heavier
        

#### 🔹 Applications:

- Telephone lines
    
- DSL broadband
    
- Ethernet LANs (10Base-T, 100Base-T)
    

---

### 2. 🧵 **Coaxial Cable**

#### 🔸 **Structure:**

- Central copper conductor
    
- Insulation layer
    
- Metallic shield (foil/braid)
    
- Outer plastic jacket
    

#### 🔹 Types:

- **Baseband** (Digital, 50-ohm, short distance, e.g. Ethernet)
    
- **Broadband** (Analog, multiple signals, e.g. Cable TV)
    

#### 🔹 RG Standards:

- RG-7/11 → Thick Ethernet
    
- RG-58 → Thin Ethernet
    
- RG-59 → Cable TV
    
- RG-62 → ARCNET
    

#### 🔹 Connectors:

- **BNC** (Bayonet Neill-Concelman)
    
    - BNC Connector, BNC T, BNC Terminator
        

#### 🔹 Pros:

- Higher bandwidth than TPC
    
- Better shielding and noise immunity
    
- Long distance, high-speed
    

#### 🔹 Cons:

- Expensive, hard to install
    
- Failure in one cable affects whole network
    
- Ground loop issues
    

#### 🔹 Applications:

- Analog telephone networks (10,000 voice signals)
    
- Cable TV (RG-59)
    
- Early Ethernet LANs (10Base-2)

- broadband internet


---

### 3. 🌐 **Fiber Optic Cable**

#### 🔸 **Working Principle:**

- Transmits data as **light pulses**
    
- Core (glass/plastic) + Cladding (less dense) → Total Internal Reflection
    

#### 🔹 Modes of Propagation:

1. **Multimode:**
    
    - **Step-index**: Uniform core density → more distortion
        
    - **Graded-index**: Gradual density decrease → less distortion
        
2. **Single-mode:**
    
    - Smaller core, highly focused light
        
    - Lower density → near-horizontal beam reflection
        
    - Supports higher bandwidth over long distances
        

#### 🔹 Pros:

- **Extremely high bandwidth**
    
- Immune to electromagnetic interference
    
- Light, small diameter, secure
    

#### 🔹 Cons:

- Expensive
    
- Fragile
    
- Requires skilled installation
    

#### 🔹 Applications:

- Backbone of internet infrastructure
    
- Long-distance telecommunications
    
- High-speed data networks (FTTH, WANs)

|Feature|Twisted Pair|Coaxial Cable|Optical Fiber|
|---|---|---|---|
|Speed|Up to 1 Gbps (UTP Cat6)|Up to 10 Gbps|More than 100 Gbps|
|Noise Resistance|Low (UTP), Medium (STP)|High|Very High|
|Installation|Easy|Moderate|Difficult|
|Security|Moderate|Good|Excellent|
|Cost|Low|Medium|High|
## 📡 Unbounded or Wireless Transmission Medium

**Definition:**  
Unbounded transmission mediums transmit electromagnetic waves **without physical conductors**. This is known as **wireless communication**, where signals travel through free space and can be received by any suitable device.

---

## 🔄 Propagation Modes

Unguided signals travel in three main ways:

1. **Ground Propagation:**
    
    - Low-frequency signals hug the Earth’s surface
        
    - Follow Earth's curvature
        
2. **Sky Propagation:**
    
    - Higher-frequency signals bounce off the ionosphere
        
    - Enable long-distance communication
        
3. **Line-of-Sight Propagation:**
    
    - Very high-frequency signals travel straight from antenna to antenna
        
    - Requires clear sight between antennas
        

---

## 📶 Types of Wireless Transmission Media

### 1. **Radio Waves**

- **Frequency Range:** 3 KHz to 1 GHz
    
- **Characteristics:**
    
    - **Omnidirectional**: Broadcasts in all directions
        
    - **Can penetrate walls** (both an advantage and disadvantage)
        
- **Antenna:** Omnidirectional
    
- **Applications:**
    
    - AM/FM radio, TV, cordless phones, paging
        

---

### 2. **Microwaves**

- **Frequency Range:** 1 GHz to 300 GHz
    
- **Characteristics:**
    
    - **Unidirectional**: Needs aligned antennas
        
    - **Line-of-sight propagation**
        
    - **Cannot penetrate walls**
        
    - Supports **high data rates**
        
- **Antennas:**
    
    - **Parabolic Dish**: Focuses signal to a point
        
    - **Horn Antenna**: Deflects signal outward like a scoop
        
- **Applications:**
    
    - Cellular phones, Satellite networks, Wireless LANs
        

#### 2.1 **Terrestrial Microwave**

- Uses **repeaters** to increase range
    
- Common in long-distance **telephone systems**
    

#### 2.2 **Satellite Microwave**

- **Geo-synchronous orbit** (~36,000 km above Earth)
    
- Antennas fixed on Earth due to satellite's fixed position
    
- **Pros:** Wide visibility, echo for error-checking
    
- **Cons:** Expensive to manufacture & launch, weather-dependent
    

---

### 3. **Infrared Waves**

- **Frequency Range:** 300 GHz to 400 THz
    
- **Characteristics:**
    
    - Cannot penetrate walls
        
    - Limited to **short-range** communication
        
    - Interference-free between rooms
        
- **Applications:**
    
    - Remote controls
        
    - Short-range device communication (PCs, keyboards, printers)
        
    - Standardized by **IrDA (Infrared Data Association)**
        

---

## 📊 Comparison Table