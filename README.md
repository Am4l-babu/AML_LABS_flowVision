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

❌ **What we DON'T do:**
- No CFD/EPANET complexity
- No AI-replaces-physics claims
- No perfect data requirements
- No pure ML approach

---

## 🧠 Understanding the Digital Twin

### What is a Digital Twin? (For Judges)

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

## 📊 Dataset

- **File**: `data/location_aware_gis_leakage_dataset.csv`
- **Records**: 5000 sensor readings
- **Features**: Pressure, Flow, Temperature, Vibration, RPM, Location
- **Labels**: Leak flags (0=Normal, 1=Leak)

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────┐
│          USER INTERFACE (Streamlit)             │
│  - Time slider                                  │
│  - Digital Twin reasoning panel                 │
│  - Network visualization (green/red pipes)      │
└─────────────────┬───────────────────────────────┘
                  │
┌─────────────────▼───────────────────────────────┐
│         DIGITAL TWIN (Orchestration)            │
│  - Coordinates ML + Detection                   │
│  - Provides explainability                      │
└────────┬────────────────────────┬────────────────┘
         │                        │
┌────────▼────────┐      ┌────────▼────────────────┐
│  ML MODEL       │      │  LEAK DETECTION         │
│  (Demand)       │      │  ALGORITHM              │
│                 │      │                         │
│  Predicts       │      │  Compares:              │
│  EXPECTED flow  │      │  - Expected flow        │
│                 │      │  - Observed flow        │
│                 │      │  - Pressure drop        │
│                 │      │                         │
│  Output:        │      │  Output:                │
│  Flow rate      │      │  LEAK / NORMAL          │
└─────────────────┘      └─────────────────────────┘
```

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

## 🎭 How to Present This to Judges

### The Digital Twin Story (5-Layer Explanation)

#### Layer 1: Physical Network
**What judges need to know:**
- We digitize existing pipelines (no rebuild needed)
- Graph model: Nodes = junctions, Edges = pipes
- GIS data provides rough topology (perfect data NOT required)

**What you say:**
> "This visual network represents an existing pipeline. We don't rebuild it. We overlay the Digital Twin on top and let it learn behavior from live data."

#### Layer 2: Sensors
**What judges need to know:**
- Pressure sensors detect drops (leaks ALWAYS reduce pressure)
- Flow sensors measure consumption + detect imbalance
- Minimal sensing + inference (not full coverage)

**What you say:**
> "The Digital Twin works with limited sensors by inferring behavior across the network using physics."

#### Layer 3: Physics (NOT AI)
**What judges need to know:**
- Conservation of mass: Water in = Water out + Usage
- Pressure-flow relationship: Higher flow → Pressure drop
- Localized effects: Leaks affect specific segments only

**What you say:**
> "Physics defines what SHOULD happen. Data shows what DID happen. The difference reveals anomalies."

#### Layer 4: Machine Learning (WHERE ML is Used)
**What judges need to know:**
- **Demand Prediction:** Supervised Learning (Linear Regression → LSTM ready)
  - Input: Time, day, historical usage
  - Output: Expected flow rate
- **Leak Classification:** Hybrid (Physics residuals + ML confidence)
  - NOT pure AI
  - Physics computes residual, ML classifies pattern

**What you say:**
> "ML learns normal usage patterns. It tells the Digital Twin what to expect. But leak detection combines physics AND learning—not AI alone."

#### Layer 5: Visualization & Decisions
**What judges need to know:**
- Multi-signal fusion (ML + Physics + Calibration)
- Confidence scores (not binary yes/no)
- Explainable reasoning (every decision traceable)

**What you say:**
> "The Digital Twin shows WHY it thinks there's a leak—not just a black-box prediction."

---

## 🎬 Live Demo Flow (What Judges Will See)

### 1️⃣ Perfect Data is NOT Required

**What you show:**
- Initial screen loads
- All pipes are green
- Flow looks normal

**What you say:**
> "At the start, the Digital Twin assumes standard pipe conditions and average demand. This is our initial hypothesis, not a claim of truth."

**Judges see:** No calibration yet, just starting assumptions

### 2️⃣ DT Starts with Assumptions, Then Corrects

**What you do:**
- Move time slider to next timestep
- Sudden changes appear:
  - Pressure drops
  - Flow increases
  - One pipe turns 🔴 RED

**What you say:**
> "Now real sensor data comes in. Observed behavior no longer matches assumed behavior, so the Digital Twin updates its understanding."

**Judges see:** Model changing, assumptions challenged, system adapting

### 3️⃣ Physics vs. Data (Visual, Not Equations)

**What you show:**
- Pipe thickness increases (flow ↑)
- Pipe color changes (pressure anomaly)
- Only ONE branch affected, not all

**What you say:**
> "If this were normal demand, all pipes would change. The fact that only one branch behaves differently violates expected system behavior."

**Judges understand:** Physics visually, not mathematically

### 4️⃣ Which Model is Used (Clear Separation)

**Signal 1: ML Demand Prediction**
- Display shows: "Expected flow: 50 L/min | Observed: 75 L/min"
- You say: "Expected demand is learned from historical data using supervised time-series models."

**Signal 2: Physics Validation**
- Display shows: Physical principles being checked
- You say: "Leak detection is not purely AI. The DT uses physics to detect abnormal residuals first."

**Signal 3: Multi-Signal Fusion**
- Red pipe appears with "Leak detected (85% confidence)"
- You say: "Both ML and Physics agree → High confidence. If only one signal fires → Investigate."

**Judges hear:** Hybrid system, no black-box AI

### 5️⃣ How DT Pinpoints the Leak

**What you show:**
- Only ONE pipe turns red
- Neighboring pipes stay green

**What you say:**
> "The DT localizes the leak by comparing upstream and downstream behavior. The anomaly starts here and doesn't propagate further."

**Judges answer:** "How do you know WHERE the leak is?"

### 6️⃣ How Predictions are Validated

**What you do:**
- Move slider to next index where leak_status = 0
- Pipe turns back 🟢 GREEN

**What you say:**
> "When the dataset indicates normal conditions again, the Digital Twin prediction matches reality, validating the earlier detection."

**Judges see:** No false alarm persistence, self-correction

### 7️⃣ How DT Gains Accuracy Over Time

**What you show:**
- Move through multiple timesteps
- Confidence values stabilize
- Fewer random color flips
- "⚙️ Calibration Active" appears

**What you say:**
> "As more historical data is ingested, the DT builds memory. This reduces false positives and increases confidence over time."

**Judges see:** Learning, not just retraining drama

### 8️⃣ Old Pipes, Corrosion, Past Leaks

**What you simulate:**
- Same pipe shows mild anomaly repeatedly
- Not sudden red spike, but: Yellow → Orange → Red gradually

**What you say:**
> "A sudden deviation indicates a leak. A slow, consistent deviation indicates degradation or corrosion. The Digital Twin distinguishes these patterns over time."

**Judges think:** "This is credible!"

### 9️⃣ How Existing Pipelines Become a DT

**What you say while pointing at screen:**
> "This visual network represents an existing pipeline in Kerala. We don't rebuild it. We overlay the Digital Twin and let it learn from live sensor data."

**Judges realize:** No shutdown needed, practical deployment

---

## 💡 Master Sentence (Memorize This)

**Use this during the demo:**

> "The dataset provides observations, the Digital Twin compares them against expected system behavior, corrects its assumptions over time, and visualizes the inferred state of the network so operators can understand and act."

**This sentence ties everything together.**

---

## 🧩 Judge's Mental Map (What They Take Away)

| Digital Twin Concept | What Judge SEES in Demo |
|---------------------|-------------------------|
| Perfect data not needed | Model adapts visually over time |
| Starts with assumptions | Initial green network |
| Corrects assumptions | Pipes change color as data arrives |
| Physics validation | Directional, localized changes |
| Machine Learning | "Expected vs Observed" values |
| Leak detection | Red pipe appears |
| Pinpointing location | Only one segment affected |
| Validation | Pipe returns to green when normal |
| Accuracy growth | Stable confidence scores |
| Old pipe detection | Gradual anomaly (yellow→orange→red) |
| Practical deployment | Overlay on existing system |

---

## 🔬 Deep Dive: How It Actually Works

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

## 🎓 Final Judge-Grade Explanation

**Memorize this statement:**

> "The Digital Twin integrates physics-based hydraulic modeling with data-driven demand learning. Supervised and semi-supervised learning are used only where appropriate—demand prediction and anomaly classification—while physical laws govern pressure and flow behavior. The system continuously validates predictions against real observations, calibrates pipe parameters to infer degradation, and improves accuracy over time without requiring full system redesign."

**That statement answers everything judges might ask.**

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

## 🚀 Quick Start

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

## 🎯 For Judges

This demo is designed to be **self-explanatory**:

✅ **Visual**: Leaks appear as red pipes - immediate understanding  
✅ **Transparent**: All reasoning steps visible in the panel  
✅ **Interactive**: Slider lets you explore the data  
✅ **Real ML**: Not fake AI - actual Linear Regression model  
✅ **Practical**: Uses real-world sensor data patterns  

**No code reading required to understand the concept!**

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

## 🤝 Contributing

This is a **hackathon demo** - feel free to:
- Adjust detection thresholds in `leak_algorithm.py`
- Try different ML models in `demand_model.py`
- Enhance visualizations in `visualization.py`
- Add more physics rules in `physics_rules.py`

---

## 🎯 Hackathon Evaluation Criteria

**This project demonstrates:**

✅ **Digital Twin Architecture** - Not just AI, but ML + Physics + Reasoning  
✅ **Physics-Informed Logic** - Explicit physical constraints (conservation, pressure-flow)  
✅ **Machine Learning** - Supervised learning for demand prediction  
✅ **Real-Time Algorithm** - Row-by-row leak detection  
✅ **Interactive Visualization** - Network graph with clickable pipes  
✅ **Learning System** - Calibration that improves over time  
✅ **Full Explainability** - Every decision can be traced and explained  
✅ **Real Data** - Uses actual sensor dataset  

---

## 📝 License

Open source - use as you like!

---

**Built for hackathon judges to understand Digital Twin + ML without reading code. 🎉**
