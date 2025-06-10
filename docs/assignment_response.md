# SEN410 Assignment - Hybrid Simulation Framework Design

## Part A: Hybrid Simulation Architecture

### Proposed Architecture:
1. **Agent-Based Modeling (ABM)**  
   - **Subsystem**: Pedestrian movement & Emergency response coordination  
   - **Justification**:  
     - Captures individual decision-making in crowded zones using NetLogo
     - Models complex interactions between pedestrians/emergency vehicles
     - Simulates adaptive behaviors during incidents

2. **Discrete-Event Simulation (DES)**  
   - **Subsystem**: Traffic dynamics & Charging station operations  
   - **Justification**:  
     - Handles queue-based events efficiently using SimPy
     - Models vehicle routing as discrete state transitions
     - Optimizes resource allocation at charging stations

3. **System Dynamics (SD)**  
   - **Subsystem**: Long-term infrastructure load  
   - **Justification**:  
     - Simulates feedback loops in road/bridge deterioration
     - Models city-scale trends via stock-flow relationships
     - Predicts maintenance needs using Vensim/PySD

### Integration Strategy:
- **ABM-DES Interface**: NetLogo agents trigger SimPy events via Python API
- **SD-ABM Feedback**: Infrastructure conditions modulate agent behaviors
- **Central Coordinator**: Custom Python controller manages time synchronization

## Part B: Implementation Workflow

### 1. Modeling Phase:
| Step | Tools | Output |
|------|-------|--------|
| System decomposition | Mermaid.js | Component diagram |
| ABM specification | NetLogo | Pedestrian behavior rules |
| DES specification | SimPy | Traffic event schema |
| SD formulation | Vensim | Causal loop diagrams |

### 2. Implementation Phase:
```python
# Sample integration pseudocode
import simpy, pysd, pyNetLogo

def main():
    # Initialize components
    traffic_sim = simpy.Environment() 
    infra_model = pysd.load('infrastructure.py')
    pedestrian_sim = pyNetLogo.NetLogoLink()
    
    while simulation_running:
        # Synchronize timesteps
        traffic_state = traffic_sim.step()
        pedestrian_sim.command(f'set traffic-density {traffic_state}')
        infra_model.run(params={'vehicle_count': traffic_state.vehicles})