# SEN410 Assignment – Smart Urban Mobility and Infrastructure Simulation Design

**Author:** [Your Full Name]  
**Course:** SEN410 – Modelling and Computer Simulation  
**Project Title:** Smart Urban Mobility and Infrastructure Simulation for Abuja CBD  
**Date:** 2025-06-01

---

## (a) Proposed Hybrid Simulation Architecture

To effectively simulate a smart urban mobility system in Abuja’s Central Business District, I propose a **hybrid simulation architecture** combining three paradigms:

1. **Agent-Based Modelling (ABM)**  
   - **Use Case:** Pedestrian movement & traffic behavior  
   - **Tool:** NetLogo  
   - **Justification:** ABM is ideal for modeling autonomous entities (vehicles, pedestrians) with individual goals and interactions. It captures complex behaviors such as jaywalking, lane-switching, and reactive vehicle rerouting.

2. **Discrete Event Simulation (DES)**  
   - **Use Case:** Emergency response coordination and infrastructure event handling  
   - **Tool:** SimPy  
   - **Justification:** DES models systems as a sequence of discrete events. It is well-suited for simulating emergency dispatches, ambulance routing, traffic signal changes, and event-driven system dynamics under peak hour constraints.

3. **Network Simulation**  
   - **Use Case:** Traffic dynamics, real-time routing, and infrastructure load  
   - **Tool:** SUMO (Simulation of Urban MObility)  
   - **Justification:** SUMO enables microscopic traffic simulation, road network modeling, and vehicle routing. It supports realistic simulations using real-world maps and integrates well with digital twin frameworks for decision-making.

> **Integration Rationale:**  
> - ABM (NetLogo) handles behavioral and stochastic elements.  
> - DES (SimPy) manages queuing and service systems like emergency vehicle dispatch.  
> - Network simulation (SUMO) ensures vehicle flow and routing optimization.

---

## (b) Modelling, Implementation, and Validation Workflow

### 1. **Modelling Phase**
- Define scope and goals (e.g., reduce congestion by 20%, optimize emergency response time).
- Collect real-world data (maps, traffic patterns, peak hours, infrastructure layout).
- Identify agents: vehicles, pedestrians, emergency responders, traffic controllers.
- Map each sub-system to its appropriate simulation paradigm.

### 2. **Design & Architecture**
- Design communication interfaces between tools (e.g., SUMO ↔ SimPy via TraCI API).
- Use XML-based traffic configuration for SUMO.
- Define agent rules in NetLogo (e.g., walking paths, waiting times).
- Model event queues in SimPy for time-critical events.

### 3. **Implementation Phase**
- Develop ABM models in NetLogo for pedestrian behavior.
- Set up SUMO simulations with OpenStreetMap for Abuja CBD.
- Use SimPy for event scheduling and coordination logic.
- Sync components using Python as a control layer to orchestrate communication.

### 4. **Validation Phase**
- Compare simulation outputs with real traffic/emergency data from FRSC or FCTA.
- Use scenario testing (e.g., accident during rush hour) to assess system response.
- Perform sensitivity analysis to test robustness under varying input conditions.
- Use statistical metrics (RMSE, delay, throughput) to validate accuracy.

---

## (c) Challenges in Model Fidelity and Scalability

### 1. **Challenge: Model Fidelity**
- **Issue:** Behavioral diversity and real-time adaptation are hard to replicate with limited data.
- **Mitigation:**  
  - Use AI-based learning agents (e.g., reinforcement learning in SUMO) to mimic real-world decisions.  
  - Integrate real-time datasets (e.g., mobile GPS, traffic APIs) for feedback loops.

### 2. **Challenge: Scalability**
- **Issue:** Integrating multiple paradigms increases computational overhead and complexity.
- **Mitigation:**  
  - Use modular design with asynchronous communication between tools.  
  - Employ parallel computing and cloud resources for large-scale simulations.  
  - Simplify less impactful components using abstraction (e.g., group pedestrian agents).

---

## Tools Used
- **NetLogo:** Agent-based simulation  
- **SimPy:** Discrete-event modeling  
- **SUMO:** Network and traffic simulation  
- **Python:** Middleware/control logic  
- **TraCI API:** Interface for SUMO interaction

---

## Summary of Design and Justification
This simulation framework blends behavioral, structural, and dynamic modeling to represent a realistic urban ecosystem in Abuja. Each simulation paradigm addresses a different dimension—micro-interactions, system-level events, and infrastructure dynamics—enabling robust planning and optimization.

---

## Understanding of Background Studies
Through this project, I’ve demonstrated:
- The value of hybrid simulation in smart urban planning.
- How real-time and event-based simulations can be integrated using industry-standard tools.
- Practical application of course concepts like model abstraction, system decomposition, and digital twin alignment in simulation engineering.

