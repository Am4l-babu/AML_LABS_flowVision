# 💧 Smart Water Digital Twin - Intelligent Leak Detection System

> **A Physics-Informed Machine Learning Digital Twin for Real-Time Water Network Management**

---

## 👥 Team Identity

**Team Name:** AML LABS

**Team Leader:** Amal Babu  
**Contact:** +91 7034177362

**Team Members:**
- Amal Babu (Team Leader)
- Govind Lal T L
- Abel Jeevan
- Navaneeth Santosh

---

## 📋 Project Brief

### What We Built

A **fully explainable Digital Twin system** for Smart Water Management that combines:
- **Machine Learning** for demand prediction
- **Physics-Informed Rules** for validation
- **Multi-Signal Fusion** for robust leak detection
- **Self-Calibration** for continuous learning
- **Interactive Visualization** for operator understanding

### Technology Stack

**Core Technologies:**
- Python 3.8+
- Streamlit (Interactive UI)
- scikit-learn (Machine Learning)
- NetworkX (Graph modeling)
- Plotly (Network visualization)

**Machine Learning:**
- **Algorithm:** Linear Regression (Supervised Learning)
- **Purpose:** Demand prediction from historical patterns
- **Training:** Only normal operation data (no leaks)
- **Extensibility:** Ready for LSTM/SARIMA for temporal patterns

**Spiking Neural Network (SNN):**
- **Role:** Event-detection layer at sensor level
- **Function:** Converts sudden signal changes into discrete spike events
- **Benefit:** Low-power, real-time anomaly detection on edge devices
- **Integration:** Triggers Digital Twin reasoning when anomalies detected

**Physics Engine:**
- Simplified Darcy-Weisbach (pressure-flow relationship)
- Conservation of Mass (flow balance)
- Localized effect modeling (leak isolation)

**Leak Detection:**
- **Method:** Hybrid (Physics + ML)
- **Approach:** Residual analysis with multi-signal fusion
- **Output:** Location + Confidence score
- **Validation:** Continuous calibration against observations

### Dataset

- **File:** `location_aware_gis_leakage_dataset.csv`
- **Size:** 5,000 sensor readings
- **Features:** Pressure, Flow, Temperature, Vibration, RPM, Location (GPS)
- **Labels:** Ground truth leak flags (0=Normal, 1=Leak)

### Key Differentiators

✅ **This is a DIGITAL TWIN, not just AI:**
- Physics validates ML predictions
- Multi-signal fusion (not single model)
- Learns and calibrates over time
- Fully explainable (no black boxes)



---

## 🧠 Understanding the Digital Twin

### What is a Digital Twin?

A Digital Twin is **NOT** a single AI model. It's a **system of interconnected models** that:

1. **Represents** the physical water network (pipes, junctions, sensors)
2. **Learns** normal behavior patterns from historical data
3. **Compares** expected vs. observed behavior in real-time
4. **Detects** deviations that violate physical laws
5. **Corrects** its assumptions through continuous calibration
6. **Visualizes** network state for human understanding

**Key Insight:** 
> "The dataset provides observations, the Digital Twin compares them against expected system behavior, corrects its assumptions over time, and visualizes the inferred state of the network so operators can understand and act."

### The 5 Core Layers

```
Physical Network (graph model of pipes)
         ↓
Data Acquisition (sensors: pressure, flow)
         ↓
Physics & Rules (conservation, pressure-flow)
         ↓
Learning & Prediction (ML for demand forecasting)
         ↓
Decision & Visualization (multi-signal fusion)
```

Each layer is explainable and traceable.

---

## 🎯 What This Demo Does

This is a **data-driven visual simulation** that demonstrates:
- 🤖 **ML-based demand prediction** (Linear Regression)
- 🔍 **Real-time leak detection** (comparing expected vs observed flow)
- 🧠 **Digital Twin reasoning** (explainable AI - no black boxes!)
- 🎨 **Interactive network visualization** (see leaks appear in real-time)

## 🚀 Quick Start

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Train the ML Model
```bash
python demand_model.py
```
This will:
- Train a Linear Regression model on normal (non-leak) data
- Save the trained model as `trained_model.pkl`
- Output: R² score and Mean Absolute Error

### 3. (Optional) Test Components
```bash
# Test leak detection algorithm
python leak_algorithm.py

# Test digital twin integration
python digital_twin.py
```

### 4. Run the Demo! 🎉
```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`

## 🎮 How to Use the Demo

1. **Move the time slider** - Scrub through 5000 real sensor readings
2. **Watch the reasoning panel** - See expected vs observed flow in real-time
3. **Observe the network** - Pipes turn RED when leaks are detected
4. **Check the statistics** - See overall accuracy and detection metrics



## 🏗️ Architecture

### System Layers

The system integrates **four intelligent layers** that work together:

```
┌─────────────────────────────────────────────────┐
│          USER INTERFACE (Streamlit)             │
│  - Time slider                                  │
│  - Digital Twin reasoning panel                 │
│  - Network visualization (green/red pipes)      │
└─────────────────┬───────────────────────────────┘
                  │
┌─────────────────▼───────────────────────────────┐
│         DIGITAL TWIN (Reasoning Layer)          │
│  - Coordinates all layers                       │
│  - Physics-informed validation                  │
│  - Provides explainability                      │
└────────┬────────────┬────────────┬──────────────┘
         │            │            │
    ┌────▼────┐  ┌────▼─────┐  ┌──▼──────────┐
    │   SNN   │  │    ML    │  │   PHYSICS   │
    │ (Event) │  │ (Memory) │  │   (Laws)    │
    └─────────┘  └──────────┘  └─────────────┘
         │            │            │
    Reflexes      Patterns      Constraints
```

### Component Breakdown

```
┌─────────────────────────────────────────────────┐
│  🎯 LAYER 1: SNN Event Detection (Reflexes)    │
│  - Processes time-series sensor signals         │
│  - Detects sudden pressure drops/flow surges    │
│  - Event-driven, low-power edge processing      │
│  - Triggers alert when anomaly detected         │
└─────────────────┬───────────────────────────────┘
                  │ Spike Event
┌─────────────────▼───────────────────────────────┐
│  🤖 LAYER 2: ML Demand Prediction (Memory)     │
│  - Linear Regression model                      │
│  - Learns normal consumption patterns           │
│  - Predicts EXPECTED flow rate                  │
└─────────────────┬───────────────────────────────┘
                  │ Expected Flow
┌─────────────────▼───────────────────────────────┐
│  ⚗️ LAYER 3: Physics Rules (Laws)              │
│  - Conservation of mass                         │
│  - Pressure-flow relationship                   │
│  - Validates against physical constraints       │
└─────────────────┬───────────────────────────────┘
                  │ Physics Validation
┌─────────────────▼───────────────────────────────┐
│  🧠 LAYER 4: Digital Twin (Reasoning)          │
│  - Fuses SNN alerts + ML predictions + Physics  │
│  - Localizes leak location                      │
│  - Provides explainable decisions               │
│  - Outputs: Status, Confidence, Reasoning       │
└─────────────────────────────────────────────────┘
```

---

## 🧬 Spiking Neural Network (SNN) Integration

### What is an SNN?

A **Spiking Neural Network (SNN)** mimics biological neural behavior by processing information as discrete **spike events** rather than continuous values. Unlike traditional neural networks, SNNs are inherently:
- **Event-driven**: Only activate when changes occur
- **Low-power**: Minimal energy consumption (ideal for IoT)
- **Time-aware**: Naturally encode temporal patterns

### Role in the Digital Twin

**SNN = Fast Reflexes (Layer 1)**

The SNN acts as the **first responder** at the sensor level:

```python
# Conceptual SNN behavior
if abs(pressure_change) > threshold:
    emit_spike()  # Alert the Digital Twin
```

**Key Point:** The SNN does **NOT** replace the Digital Twin or physics reasoning. It's a **trigger mechanism** that alerts the system when something unusual happens.

### Why Use SNN?

| Traditional Approach | SNN Approach |
|---------------------|-------------|
| Continuous polling of all sensors | Event-driven (only activates on change) |
| High power consumption | Ultra-low power (perfect for battery sensors) |
| May miss rapid transients | Captures sudden spikes naturally |
| No temporal encoding | Encodes timing of events |

### Advantages

1. **⚡ Fast Detection**: Identifies sudden anomalies in microseconds
2. **🔋 Energy Efficient**: Runs on edge devices without draining batteries
3. **📡 Real-Time**: No latency from cloud processing
4. **🎯 Event-Focused**: Filters out noise, only alerts on significant changes
5. **🌐 Scalable**: Can deploy thousands of sensors without infrastructure overload
6. **🧠 Bio-Inspired**: Mimics human nervous system's fast reflex response

### Where SNN is Used

**Deployment Location:** Edge sensors in the water network

```
Underground Pipe Network
         ↓
   [Pressure Sensor] ← SNN chip
         ↓ (spike event)
   Wireless Gateway
         ↓
   Digital Twin Server
```

**Specific Use Cases:**
- **Burst pipe detection**: Sudden pressure drop triggers immediate spike
- **Valve malfunction**: Unexpected flow surge generates alert
- **Leak onset**: Gradual pressure decline accumulates spikes
- **Water hammer**: Rapid oscillations create spike patterns

### How SNN Integrates with Digital Twin

**Step-by-Step Process:**

1. **Sensor Reads Data**
   - Pressure: 95 PSI → 70 PSI (sudden drop)
   - Flow: 50 L/min → 75 L/min (surge)

2. **SNN Processes Signal**
   ```
   ΔPressure = -25 PSI (exceeds threshold)
   → SNN fires spike event
   ```

3. **Spike Triggers Digital Twin**
   - DT wakes up and analyzes the flagged segment
   - ML predicts expected flow (should be 50 L/min)
   - Physics checks if pressure drop is consistent with leak

4. **Multi-Signal Fusion**
   - SNN: ✅ Anomaly detected (reflex)
   - ML: ✅ Flow higher than expected (memory)
   - Physics: ✅ Pressure drop confirms leak (law)
   - **Decision: LEAK (High Confidence)**

5. **Explainable Output**
   ```
   Status: LEAK
   Location: Zone_4_Block_2_Pipe_3
   Confidence: 85%
   Reasoning:
     - SNN detected sudden pressure drop (-25 PSI)
     - ML predicted 50 L/min, observed 75 L/min (+50%)
     - Physics confirms: excess flow + pressure loss = leak
   ```

### SNN vs. Traditional ML

| Aspect | Traditional ML | SNN |
|--------|---------------|-----|
| **Operation** | Continuous inference | Event-driven |
| **Power** | High (always on) | Ultra-low (spikes only) |
| **Speed** | Batch processing | Instant (reflex) |
| **Use Case** | Pattern learning | Anomaly detection |
| **Deployment** | Cloud/server | Edge device |
| **Explainability** | Model-dependent | Event-based (clear trigger) |

**Hybrid Approach (This System):**
- SNN detects **when** something is wrong (fast, low-power)
- ML predicts **what** should be normal (learned patterns)
- Physics validates **why** it's a leak (fundamental laws)
- Digital Twin reasons **how** to respond (integrated intelligence)

### Implementation Architecture

**Hardware Level:**
```
┌─────────────────────┐
│  Water Pipe Sensor  │
│  - Pressure sensor  │
│  - Flow sensor      │
│  - MCU + SNN chip   │ ← Neuromorphic hardware (e.g., Intel Loihi)
└──────────┬──────────┘
           │ LoRa/NB-IoT (low power)
           ▼
   ┌───────────────┐
   │   Gateway     │
   └───────┬───────┘
           │
           ▼
   ┌───────────────────┐
   │  Digital Twin     │
   │  (Cloud/Server)   │
   └───────────────────┘
```

**Software Level:**
```python
# Pseudocode for SNN layer
class SNNEventDetector:
    def process_sensor_data(self, pressure, flow):
        # Encode changes as spikes
        pressure_spike = self.encode_spike(pressure, threshold=10)
        flow_spike = self.encode_spike(flow, threshold=5)
        
        if pressure_spike or flow_spike:
            return {
                'event_detected': True,
                'spike_type': 'pressure_drop' if pressure_spike else 'flow_surge',
                'timestamp': time.now(),
                'trigger_dt': True  # Alert Digital Twin
            }
        return {'event_detected': False}
```

### Benefits to the Digital Twin System

1. **Reduced False Alarms**: SNN filters noise, DT only processes genuine anomalies
2. **Faster Response**: Edge detection (ms) + DT reasoning (seconds) = rapid leak isolation
3. **Lower Bandwidth**: Only transmit spike events, not continuous sensor streams
4. **Scalability**: Deploy in remote areas without constant connectivity
5. **Explainability**: Clear chain: SNN spike → ML deviation → Physics confirmation → Leak

### Conceptual Framework

**Biological Analogy:**

Think of the water network as a living organism:

- **SNN = Nerve Endings (Reflexes)**  
  Instantly react to pain (pressure drop)

- **ML = Hippocampus (Memory)**  
  Remember normal patterns ("this pipe usually flows at 50 L/min")

- **Physics = Laws of Nature (Constraints)**  
  Water can't disappear (conservation of mass)

- **Digital Twin = Cerebral Cortex (Reasoning)**  
  Integrates all signals and makes informed decisions

**Together:** Fast reflexes + learned memory + physical laws + intelligent reasoning = Robust leak detection

---

## 🧩 Project Structure

```
flowVision last/
├── data/
│   └── location_aware_gis_leakage_dataset.csv  # Dataset
├── demand_model.py          # ML training & prediction
├── leak_algorithm.py        # Leak detection logic
├── digital_twin.py          # Orchestration layer
├── app.py                   # Streamlit UI
├── requirements.txt         # Dependencies
├── trained_model.pkl        # Saved ML model (after training)
└── README.md               # This file
```

## 🧠 Digital Twin Concept

**What makes this a "Digital Twin"?**

1. **Expected Behavior**: ML model learns from historical normal data
2. **Observed Behavior**: Real sensor readings from the network
3. **Comparison**: Digital Twin compares expected vs observed
4. **Decision Making**: If observed flow >> expected AND pressure drops → LEAK
5. **Explainability**: Every decision is transparent and traceable
6. **Learning**: System calibrates and improves over time

**Example Reasoning:**
```
Expected Flow (ML):  50.0 L/min
Observed Flow:       65.0 L/min
Residual:           +15.0 L/min (+30%)
Pressure:            Dropped by 15%
Decision:            LEAK (Confidence: 30%)
Reasoning:           Flow is 30% higher than expected AND pressure dropped
```

---

## ⚗️ Physics-Informed Logic

**IMPORTANT:** This is NOT physics simulation (CFD/EPANET). These are **logical physical constraints** for explainable reasoning.

### Physical Principles Used

#### 1. Conservation of Flow (Kirchhoff's Law)
**Principle:** Water in = Water out + Consumption

```python
if (observed_flow > expected_flow + tolerance):
    # Water is missing → Possible leak
```

**Plain English:** If more water flows through than we expect people to use, it's going somewhere else (leak).

#### 2. Pressure-Flow Relationship (Simplified Darcy-Weisbach)
**Principle:** Higher flow → More friction → Pressure drop

```python
pressure_drop = f × (L/D) × (ρ × v²/2)
# Simplified for real-time calculation
```

**Plain English:** When water flows faster through a pipe, pressure naturally drops due to friction. If pressure drops MORE than expected, something unusual is happening.

#### 3. Localized Effects
**Principle:** Leaks affect specific pipe segments, not the entire network

**Plain English:** A leak in Pipe A won't affect flow in Pipe B (they're independent). This helps us pinpoint exactly WHERE the leak is.

### Why These Rules, Not Full Simulation?

✅ **Fast:** Real-time processing (milliseconds)  
✅ **Explainable:** Anyone can understand the logic  
✅ **Practical:** Works on IoT edge devices  
✅ **Robust:** Doesn't require perfect hydraulic models  

❌ CFD/EPANET would require:  
- Complete network topology  
- Accurate pipe dimensions  
- Expensive computation  
- Hard to explain to non-experts  

---

## 🎓 Digital Twin Learning & Calibration

**The system gets smarter over time!**

### How Calibration Works

1. **Observation Phase:** System tracks deviations (residuals) for each pipe
2. **Pattern Detection:** If consistent offset detected (not intermittent spikes)
3. **Baseline Adjustment:** DT adjusts expected flow for that specific pipe
4. **Validation:** Continue monitoring to ensure adjustment is correct

### Example Scenario

```
Pipe_A historical residuals: [+5, +6, +5, +7, +5] L/min (consistent)
Pipe_A leak flags: [0, 0, 0, 0, 0] (no leaks)

→ Digital Twin learns: "This pipe naturally uses 5-6 L/min more than ML predicts"
→ Calibration applied: baseline_flow += 5.5 L/min
→ Future predictions adjusted automatically
→ Result: Fewer false positives for this pipe!
```

### What is NOT Being Done

❌ **NOT retraining the ML model** (model stays the same)  
❌ **NOT changing detection thresholds** (thresholds stay the same)  
✅ **IS adjusting pipe-specific baselines** based on learned behavior  

### Why This Matters

- **Reduces false positives** over time
- **Adapts to pipe-specific characteristics** (roughness, age, local consumption patterns)
- **Proves the Digital Twin is learning**, not just detecting
- **No manual intervention required** - fully automated

### Viewing Calibration in Action

1. Run the app: `streamlit run app.py`
2. Select a pipe from the dropdown
3. Look for:
   - "⚙️ Calibration Active" indicator
   - Calibration offset value
   - "Digital Twin has learned this pipe's baseline behavior" message
   - Historical average residual display

---

## 🔬 Technical Deep Dive

### How Leakage is Predicted (Step-by-Step)

#### Detection
DT detects leakage when:
1. Pressure drops abnormally (below physics-expected level)
2. Flow increases abnormally (beyond predicted demand)
3. Pattern persists over time (not transient spike)

This is **change detection**, not guessing.

#### Pinpointing the Leak
DT narrows location by:
1. Comparing upstream vs. downstream sensors
2. Observing pressure gradients along pipe segments
3. Simulating hypothetical leaks in different sections
4. Matching simulated vs. observed behavior

**Result:** "Leak likely between Junction_2 and Junction_3 (confidence 82%)"

No digging. No blind search.

### How DT Calculates Demand

```
Expected Demand = 
    historical baseline +
    time-of-day effect +
    day-of-week effect +
    seasonal effect
```

ML learns these coefficients from normal data.

The DT uses demand to:
- Predict expected flow
- Separate leak flow from usage flow

### How Predictions are Validated

**Continuous Validation:**
Every new data point:
1. Is compared with prediction
2. Error is calculated
3. Model parameters are updated (online calibration)

**Event-Based Validation:**
When leak is repaired, valve closed, or pipe replaced:
1. DT checks: "Did system behavior return to expected?"
2. If YES → Confidence increases
3. If NO → Model adjusts assumptions

### How DT Gains Accuracy Over Time

Accuracy improves because:
1. Demand models learn usage patterns
2. Pipe roughness parameters are calibrated
3. False positives are eliminated through memory
4. Sensor noise is filtered out
5. Historical context grows (DT remembers)

### How DT Knows About Corrosion & Old Pipes

DT does NOT see corrosion directly.

**It infers it:**

Corroded pipes show:
- Higher pressure loss (more friction)
- Lower efficiency (reduced flow capacity)
- Gradual worsening over time

DT adjusts:
- Roughness coefficient ↑
- Effective diameter ↓

This becomes: **"Pipe Health Score"**

### How Existing Systems Are Converted to a DT

**Step-by-step conversion:**
1. Digitize maps (even rough drawings work)
2. Create initial graph model (nodes + edges)
3. Attach sensors (limited coverage is OK)
4. Run baseline simulation with assumptions
5. Start observing deviations from expected
6. Calibrate continuously as data arrives

**No shutdown required.**  
DT is added on top of existing infrastructure.

### How DT "Knows" Past vs. Current Condition

DT stores:
- Historical sensor data (time-series)
- Historical inferred parameters (pipe roughness, etc.)
- Event logs (repairs, leak occurrences)

So it compares:
```
Current behavior
    vs.
Its own memory
```

**This is the essence of a twin.**

---

## 🧪 The Complete DT Pipeline

```
Physical Pipeline
       ↓
Graph Model + Physics Rules
       ↓
Sensor Data Ingestion (real-time)
       ↓
Demand Learning (ML: supervised)
       ↓
Anomaly Detection (physics residuals)
       ↓
Leak Localization (gradient analysis)
       ↓
Validation & Calibration (online learning)
       ↓
Visualization & Operator Decisions
```

**Each block is explainable. No magic.**

---



---

## 💎 The Deepest Insight

**What makes a TRUE Digital Twin:**

| Component | Role |
|-----------|------|
| **Physics** | Gives truth (what MUST happen) |
| **Data** | Gives context (what DID happen) |
| **Learning** | Gives adaptation (improving over time) |
| **Memory** | Gives experience (learning from history) |
| **Visualization** | Gives understanding (for humans) |

**That combination—not AI alone—is a true Digital Twin.**

---

## 📊 Performance

Based on the test dataset:
- **Accuracy**: ~83%
- **Recall**: 100% (catches all real leaks)
- **Precision**: ~26% (some false positives, which is safer for critical infrastructure)

The model is intentionally **conservative** (better to check a false alarm than miss a real leak).

## 🎨 UI Features

### Digital Twin Reasoning Panel
- 🤖 Expected Flow (ML prediction)
- 📊 Observed Flow (sensor data)
- 🔧 Pressure reading
- ± Residual calculation
- Status badge (GREEN = Normal, RED = Leak)
- Confidence score with progress bar

### Network Visualization
- Interactive graph with zones and blocks
- Color-coded pipes (Green/Red/Orange)
- Pipe thickness proportional to flow
- Real-time updates when slider moves

### Statistics Dashboard
- Total records processed
- Leaks detected
- Accuracy, Precision, Recall
- Confusion matrix details



## 🔧 Technical Details

### ML Model
- **Algorithm**: Linear Regression (sklearn)
- **Features**: Pressure, Temperature, RPM, Operational_Hours, Vibration
- **Target**: Flow_Rate
- **Training**: Only on normal (non-leak) data
- **Purpose**: Learn what "normal" looks like

### Leak Detection
- **Method**: Residual analysis
- **Threshold**: 15% deviation from expected
- **Confirmation**: Pressure drop indicator
- **Output**: Status + Confidence score

### Network Visualization
- **Library**: NetworkX + Plotly
- **Nodes**: Zones and Blocks
- **Edges**: Pipes connecting them
- **Colors**: Dynamic based on detection status

## 🚨 Constraints (By Design)

- ❌ No physics simulation (CFD/EPANET)
- ❌ No fake AI
- ✅ Data-driven approach
- ✅ Explainable decisions
- ✅ Visual cause-and-effect

## 🛠️ Troubleshooting

### Problem: "Model not found" error

**Solution:**
```bash
python demand_model.py
```
This trains and saves the model as `trained_model.pkl`

### Problem: "Dataset not found" error

**Solution:**
- Ensure `data/location_aware_gis_leakage_dataset.csv` exists
- Check the file path is correct
- Dataset must have columns: `Location_Code`, `Pressure`, `Flow_Rate`, `Temperature`, `RPM`, `Vibration`, `Operational_Hours`, `Leakage_Flag`, `Zone`, `Block`, `Pipe`, `Latitude`, `Longitude`

### Problem: Streamlit app runs but shows errors

**Solution:**
```bash
pip install --upgrade streamlit pandas numpy scikit-learn plotly networkx matplotlib joblib
```

### Problem: Network visualization doesn't show anything

**Solution:**
- Check that the dataset has valid `Latitude` and `Longitude` values
- Try zooming out in the plot
- Refresh the page (F5)

### Problem: Performance is slow

**Solution:**
- The app samples data for performance metrics (every 10th record)
- Reduce the window size in `get_network_snapshot` if needed
- For large datasets (>10k records), consider downsampling

---

## 📚 Additional Resources

- **Demo Guide:** See `demo_guide.md` for presentation tips
- **Code Comments:** All Python files have detailed explanations
- **Test Functions:** Run individual modules to see unit tests

---

## 📝 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

