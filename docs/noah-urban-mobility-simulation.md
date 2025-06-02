# SEN410 Assignment – Smart Urban Mobility and Infrastructure Simulation Project

## Author: Noah Samuel Ojima-ojo

## Branch: `noah-simulation-version`

## Date: June 2, 2025

---

## **a. Proposed Hybrid Simulation Architecture**

To model the complexity of smart urban mobility in Abuja's Central Business District, I propose a **hybrid simulation architecture** that integrates:

### 1. **Agent-Based Modelling (ABM)**

**Tool**: NetLogo
**Subsystem**:

* Pedestrian movement in crowded zones
* Dynamic vehicle behavior (e.g., driver decisions)

**Justification**: ABM is ideal for modeling heterogeneous, autonomous agents such as pedestrians, vehicles, and emergency responders. It allows for localized decisions and emergent behavior, which is critical for modeling human-centric systems.

---

### 2. **Discrete Event Simulation (DES)**

**Tool**: SimPy
**Subsystem**:

* Emergency response coordination
* Traffic light management and timed system interactions

**Justification**: DES excels at modeling systems where state changes occur at discrete points in time, such as ambulance dispatch events or signal changes. It ensures event scheduling and efficient queue processing in time-sensitive operations.

---

### 3. **Microscopic Traffic Simulation (e.g., Network/Flow Simulation)**

**Tool**: SUMO (Simulation of Urban Mobility)
**Subsystem**:

* Traffic dynamics and vehicle routing
* Infrastructure load assessment (e.g., road congestion, bridge stress)

**Justification**: SUMO allows for detailed modeling of traffic flow using real road networks, simulating thousands of vehicles with lane-changing and routing algorithms. It supports importing OSM data for accurate geographic layouts.

---

### Optional Integration

**Digital Twins + AI-based Decision-Making**

* Real-time adaptive traffic light control
* Predictive rerouting based on congestion using reinforcement learning
* Infrastructure wear prediction using ML models

---

## **b. Steps for Modelling, Implementation, and Validation**

### **1. Problem Specification**

* Define objectives and KPIs (e.g., average commute time, pedestrian safety index).
* Identify agents, events, and system boundaries.

### **2. System Decomposition and Paradigm Mapping**

* **Pedestrians/Vehicles** → NetLogo (ABM)
* **Traffic lights/Dispatch** → SimPy (DES)
* **Road Network/Flow** → SUMO (Network Simulation)

### **3. Model Design**

* Create individual models for each subsystem.
* Design APIs or data exchange mechanisms between models.

  * Example: SUMO exports vehicle density → SimPy triggers emergency response logic.

### **4. Toolchain Integration**

* Use `TraCI` (Traffic Control Interface) to connect Python (SimPy) with SUMO.
* Use NetLogo’s `BehaviorSpace` for scenario testing and exporting pedestrian flow data to SUMO.

### **5. Implementation**

* Use modular programming with Python for core control and communication logic.
* Store infrastructure and agent data in JSON/XML formats for interoperability.

### **6. Validation and Calibration**

* Compare simulated data with real data from FRSC, Abuja Smart City Project, or Google Mobility Reports.
* Use statistical tests to validate pedestrian and traffic flow patterns.

### **7. Visualization and Reporting**

* Use NetLogo GUI for pedestrian simulation, SUMO-GUI for traffic.
* Export logs and results for analysis using Pandas/Matplotlib.

---

## **c. Challenges in Model Fidelity and Scalability**

### **1. Challenge: Model Fidelity (Accuracy of Real-World Representation)**

**Problem**: Simplified assumptions (e.g., uniform pedestrian speed) may deviate from real behavior.
**Mitigation**:

* Incorporate real-world data (e.g., sensor data, traffic counts).
* Calibrate agent behavior using parameter tuning techniques (e.g., genetic algorithms).
* Use hybrid verification (face validation + statistical analysis).

---

### **2. Challenge: Scalability (Handling Complex, Large-scale Simulations)**

**Problem**: High computational cost when simulating thousands of vehicles, pedestrians, and events in real-time.
**Mitigation**:

* Use event-based abstraction for less critical zones.
* Implement parallel processing where possible (e.g., SUMO supports multi-threading).
* Use level-of-detail modeling: aggregate distant agents into flow rates rather than simulating each.

---

## **Summary of Tools Used**

| Tool        | Purpose                                    |
| ----------- | ------------------------------------------ |
| **NetLogo** | Pedestrian ABM modeling                    |
| **SimPy**   | Event-driven emergency & traffic control   |
| **SUMO**    | Microscopic traffic and routing simulation |
| **Python**  | Control, data exchange, analysis           |
| **TraCI**   | Interface between SUMO and Python          |

---

## **Summary of Design**

This hybrid architecture allows realistic simulation of human, vehicular, and infrastructure behaviors using appropriate paradigms. Each tool is specialized and connected through lightweight data exchange interfaces, enabling scalability and fidelity.

---

