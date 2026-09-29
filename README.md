# SHIELD-M

### Smart Hazard Identification & Early-warning Life-safety Device for Mines

**SHIELD-M** is a reusable, modular underground coal mine safety and structural monitoring system designed for **real-time detection of structural instability and hazardous conditions**. It combines multi-sensor monitoring, Edge AI, LoRa-based mesh communication, and an early-warning system to support continuous underground mine safety.

---

## 🚨 Problem Statement

Underground coal mines are exposed to hazards such as:

* Roof falls and strata movement
* Crack formation and structural deformation
* Ground vibration
* Pillar instability
* Water/moisture ingress
* Hazardous gases such as CH₄ and CO

Conventional monitoring methods may depend on periodic inspection or individual monitoring systems, making continuous distributed monitoring difficult as mining areas change.

SHIELD-M addresses this challenge through a **distributed, reusable and intelligent sensor network**.

---

## 💡 Proposed Solution

SHIELD-M deploys multiple modular sensor nodes across underground mine pillars and active mining blocks.

Each node collects structural and environmental data and performs local processing using an **ESP32-based edge device**. Edge AI performs sensor fusion and anomaly detection to identify abnormal patterns.

Data is communicated through a **LoRa-based mesh network** to a local gateway, where the information is displayed on a monitoring dashboard and used to generate alerts.

### Core Workflow

**Sense → Process → Communicate → Analyze → Alert → Continuous Monitoring**

---

## 🏗️ System Architecture

```text
┌─────────────────────────────┐
│      Multi-Sensor Node      │
│                             │
│ LVDT / Strain / Vibration   │
│ IMU / Moisture / Gas        │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│        ESP32 Node            │
│ Data Acquisition +           │
│ Local Preprocessing          │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│        Edge AI               │
│ Sensor Fusion +              │
│ Anomaly Detection            │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│      LoRa Mesh Network       │
│ Long-Range + Low-Power       │
│ Communication                │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│     Local Gateway/Server     │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│   Dashboard + Alert System   │
│ Normal / Warning / Critical   │
└─────────────────────────────┘
```

**Cloud connectivity can be added as an optional layer for historical data storage and remote monitoring. Core detection and alert generation can operate locally without internet connectivity.**

---

# 🔧 Sensor Node

Each SHIELD-M node is designed as a **modular pillar-mounted monitoring unit**.

### Sensors

| Sensor                         | Purpose                                      |
| ------------------------------ | -------------------------------------------- |
| **LVDT / Displacement Sensor** | Crack opening and structural deformation     |
| **Strain Sensor**              | Structural stress and deformation            |
| **Vibration Sensor**           | Abnormal ground/rock vibrations              |
| **IMU**                        | Tilt, rotation and movement                  |
| **Soil Moisture Sensor**       | Water ingress and moisture-related weakening |
| **Gas Sensors**                | CH₄, CO, CO₂ and O₂ monitoring               |
| **GPS**                        | Node/pillar coordinate identification        |

> GPS is used for recording the location of a node/pillar rather than relying on it for underground positioning.

---

# 🧠 Edge AI

SHIELD-M uses **Edge AI** to process sensor data locally.

Instead of continuously sending raw sensor data to a remote cloud server, the edge device can analyze the data near the point of sensing.

### Functions

* Sensor data preprocessing
* Multi-sensor fusion
* Anomaly detection
* Pattern recognition
* Structural condition classification
* Early-warning generation

### Example

A simultaneous increase in:

**LVDT displacement + strain + vibration + IMU tilt**

can indicate an abnormal structural condition.

The system can classify the condition as:

🟢 **Normal**
🟡 **Warning**
🔴 **Critical**

The exact thresholds and AI model can be calibrated using experimental and mine-specific datasets.

---

# 📡 LoRa Mesh Communication

SHIELD-M uses **LoRa** for long-range, low-power communication between underground sensor nodes and the local gateway.

### Advantages

* Long-range communication
* Low power consumption
* Suitable for distributed sensor nodes
* Reduced dependence on wired infrastructure
* Supports scalable deployment

### Mesh Topology

Multiple sensor nodes can communicate through neighboring nodes, allowing data to be relayed toward the gateway.

```text
Node 1 ─── Node 2 ─── Node 3
              │
              ↓
           Gateway
              │
              ↓
          Dashboard
```

This approach can improve communication coverage in complex underground mine layouts.

---

# 🚨 Alert System

When abnormal conditions are detected, SHIELD-M generates an immediate warning.

### Alert Levels

| Level       | Condition                  | Response               |
| ----------- | -------------------------- | ---------------------- |
| 🟢 Normal   | Stable parameters          | Continue monitoring    |
| 🟡 Warning  | Abnormal trend detected    | Warning notification   |
| 🔴 Critical | High-risk abnormal pattern | Immediate safety alert |

Alerts can be presented through:

* Local alarm/buzzer
* Dashboard notification
* Warning indicators
* Future SMS/mobile notifications

---

# 🔄 Reusable Modular Design

One of the major features of SHIELD-M is **node reusability**.

Underground coal mining areas continuously change as extraction progresses. SHIELD-M nodes are designed to be removable and redeployable.

```text
Active Block
     ↓
Sensor Node Deployment
     ↓
Continuous Monitoring
     ↓
Block Exhausted
     ↓
Node Removed
     ↓
Redeployed to New Active Block
```

This reduces the need to permanently install new sensor nodes throughout changing mine sections.

---

# ☁️ Cloud-Independent Operation

SHIELD-M does not require the cloud for its core safety function.

### Without Internet

```text
Sensors
   ↓
ESP32
   ↓
Edge AI
   ↓
LoRa Mesh
   ↓
Local Gateway
   ↓
Local Dashboard
   ↓
Alarm
```

### Optional Cloud

```text
Local Gateway
      ↓
    Cloud
      ↓
Historical Data
Remote Monitoring
Analytics
Model Improvement
```

This makes local detection and alert generation possible even when internet connectivity is unavailable.

---

# 💻 Software Stack

### Embedded System

* ESP32
* Arduino IDE / PlatformIO
* C/C++

### Edge AI

* Python
* TensorFlow / TensorFlow Lite
* Machine Learning
* Sensor Fusion
* Anomaly Detection

### Communication

* LoRa
* MQTT

### Dashboard

* HTML
* CSS
* JavaScript
* Node.js
* Chart.js
* Leaflet.js

### Development

* Visual Studio Code
* Git / GitHub

---

# ⚙️ Technical Approach

1. **Multi-Sensor Monitoring**
   Collect structural, environmental and gas data from underground sensor nodes.

2. **Edge AI Processing**
   Process sensor data locally and identify abnormal patterns.

3. **Mesh Networking**
   Connect multiple distributed nodes using a LoRa-based communication network.

4. **Real-Time Communication**
   Transfer processed data to the local gateway.

5. **Early Warning**
   Classify conditions and generate Normal, Warning or Critical alerts.

6. **Reusable Deployment**
   Relocate sensor nodes as mining blocks change.

---

# 🔄 Continuous Monitoring Flow

```text
SENSE
  ↓
COLLECT
  ↓
PROCESS
  ↓
ANALYZE
  ↓
COMMUNICATE
  ↓
ALERT
  ↓
RESPOND
  ↓
CONTINUE MONITORING
  ↺
```

---

# ✅ Feasibility

SHIELD-M is technically feasible because it combines established sensing, embedded processing and wireless communication technologies.

* Commercially available structural and environmental sensors
* ESP32-based data acquisition
* LoRa-based wireless communication
* Edge computing and machine-learning techniques
* Modular sensor-node architecture
* Local processing without mandatory cloud dependency
* Scalable distributed sensor deployment
* Existing underground mine monitoring practices provide a foundation for sensor integration

---

# 📈 Viability

* **Cost-effective:** Uses compact embedded hardware and reusable nodes.
* **Scalable:** Additional nodes can be deployed as monitoring requirements increase.
* **Reusable:** Nodes can be relocated between active mining blocks.
* **Low-power:** LoRa enables low-power wireless communication.
* **Real-time:** Continuous monitoring enables rapid detection of abnormal conditions.
* **Adaptable:** Modular architecture can accommodate different sensors and mine layouts.
* **Maintainable:** Individual nodes can be serviced or replaced without replacing the complete network.

---

# 🌍 Impacts & Benefits

* Improved underground worker safety
* Early detection of structural abnormalities
* Continuous mine monitoring
* Real-time hazard alerts
* Crack and deformation monitoring
* Strata movement monitoring
* Gas hazard monitoring
* Reduced dependence on manual inspection
* Reusable monitoring infrastructure
* Scalable deployment
* Data-driven mine safety management
* Improved emergency response
* Potential reduction in monitoring and infrastructure costs

---

# 🔮 Future Scope

* Advanced Edge AI models trained on real mine datasets
* Digital twin of underground mine structures
* Automated risk prediction
* Integration with mine ventilation systems
* Mobile application for supervisors
* SMS/remote emergency notifications
* Advanced underground localization
* Automated sensor health monitoring
* Integration with existing mine-control systems
* Large-scale pilot deployment

---

# 🧪 Development Status

**Current Stage:** Prototype / Proof of Concept

### Current Development Areas

* Sensor-node design
* 3D mechanical design
* ESP32 integration
* LoRa communication
* Sensor-data acquisition
* Edge AI development
* Dashboard development
* Alert-system implementation

---

# 🎯 Key Features

| Feature                          | SHIELD-M |
| -------------------------------- | -------- |
| Multi-Sensor Monitoring          | ✅        |
| Structural Monitoring            | ✅        |
| Gas Monitoring                   | ✅        |
| Edge AI                          | ✅        |
| Sensor Fusion                    | ✅        |
| LoRa Communication               | ✅        |
| Mesh Networking                  | ✅        |
| Real-Time Alerts                 | ✅        |
| Cloud-Independent Core Operation | ✅        |
| Modular Nodes                    | ✅        |
| Reusable Deployment              | ✅        |
| Scalable Architecture            | ✅        |

---

# 🏆 Key Innovation

The key concept of SHIELD-M is the combination of:

**Multi-Sensor Monitoring + Edge AI + LoRa Mesh + Real-Time Alerts + Reusable Modular Nodes**

This creates a distributed monitoring architecture designed specifically for the changing environment of underground coal mines.

---

# 👥 Project

**Project:** SHIELD-M
**Problem Statement:** SIH 26025
**Domain:** Underground Coal Mine Safety
**Technology:** IoT + Edge AI + Wireless Sensor Network
**Application:** Structural & Hazard Monitoring

---

## 📌 Keywords

`Underground Coal Mining` `Mine Safety` `Structural Health Monitoring` `Crack Detection` `Strata Movement` `Roof Fall Detection` `Edge AI` `Sensor Fusion` `ESP32` `LoRa` `Mesh Network` `IoT` `LVDT` `IMU` `Strain Monitoring` `Vibration Monitoring` `Moisture Detection` `Gas Detection` `Early Warning System` `Real-Time Monitoring` `Predictive Monitoring` `Modular Sensor Node` `Reusable Sensors` `Industrial IoT`

---

## ⚠️ Disclaimer

SHIELD-M is a prototype/research project intended for demonstration and development. It should not be considered a certified mine-safety system until it has undergone appropriate laboratory validation, field testing, calibration, reliability assessment, and certification according to applicable mining safety regulations.

---

**SHIELD-M — Sense. Analyze. Communicate. Alert. Protect.**
