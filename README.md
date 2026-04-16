# CyberCleanAir 🌿
A two-day hackathon project focused on air quality sensor security and cyberattack detection using real-world PurpleAir sensor data.

## 👥 Team
Victoria Treder, Sri Harshitha Battula, Luice Khamboo, Kelvin Boakye Fosu, Michel Atayi


**Background**
Nature areas outside of Atlanta, Georgia showed unexpectedly high AQI readings. This raised the question: **can we actually trust these sensors?** Our team set out to analyze real air quality data, build a trust score system, and test it against simulated cyberattacks.

** What We Did?**

### Part 1 — Sensor Selection
- Pulled real PM2.5 data from 3 PurpleAir sensors in the Brevard, Atlanta area (April 1-3, 2026)
- Sensors: **Delphia Pondside**, **Pisgah Forest**, **Shining Rock Wilderness**
- Analyzed spatial and temporal patterns across all 3 sensors
- Selected **Delphia Pondside** as our primary sensor — the only one consistently exceeding the 50 µg/m³ poor air quality threshold

### Part 2 — Trust Score System
- Built a mathematical trust score to evaluate how reliable a sensor's data is
- Used purely statistical methods — no machine learning
- Baseline trust score for Delphia Pondside: **81.95 / 100**

### Part 3 — Attack Simulation (Stress Testing)
- Simulated 3 real-world cyberattacks on the sensor data
- Tested how much each attack caused the trust score to drop
- Flatline attack dropped the score to **67.76 / 100**

### Part 4 — Recommendations
- Proposed both internal and external defenses to protect PurpleAir sensor networks from cyberattacks


## 🧮 Trust Score Formula

$$TrustScore = \frac{Q + S + N}{3}$$

| Category | What It Measures |
|---|---|
| **Q — Data Quality** | Missing values, accuracy, completeness |
| **S — Statistical Behavior** | Variance, outliers, rate of change, repetition |
| **N — Neighbor Comparison** | Value difference vs neighbors, correlation with neighbors |

Each category is equally weighted at **33.3%**

---

## ⚔️ Attacks Simulated

| Attack | What It Does | Trust Score |
|---|---|---|
| Baseline (No Attack) | Real sensor data | 81.95 / 100 |
| Replay Attack | Replaces pollution event with old clean air data | Drops |
| Flatline Attack | Sensor stuck reporting one constant value | 67.76 / 100 |
| Threshold Manipulation | Reduces all values by 30% to hide pollution | Drops |

---

## 🔬 Algorithms Used

- **Z-Score** — Statistical outlier detection
- **Pearson Correlation Coefficient** — Measures agreement between sensors
- **Coefficient of Variation** — Measures data consistency
- **Rate of Change Detection** — Flags sudden extreme jumps
- **Repetition Detection** — Catches flatline and replay patterns
- **Weighted Average Scoring** — Combines all metrics into final trust score

---

## 🛡️ Recommendations to Protect PurpleAir

**Internal Defenses:**
- Encrypt all sensor communications
- GPS location and timestamp verification to prevent replay attacks
- Build historical baseline profiles for each sensor
- Automatic flatline detection and alerts

**External Defenses:**
- Cross validate with other systems like EPA and NASA
- Real time anomaly monitoring alerts
- Deploy decoy sensors to detect attackers
- Train a machine learning model on suspicious data patterns for automated detection

---

## 🔌 API Integration
- Used the **PurpleAir REST API** with API key authentication
- Fetched historical PM2.5 sensor data using Unix timestamps
- Queried 3 different sensors by unique sensor index IDs
- Fetched two separate date ranges — event period (April 1-3) and clean period (March 29-31)
- Parsed JSON responses into Pandas dataframes for analysis

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Statistical calculations |
| Matplotlib | Data visualization |
| PurpleAir REST API | Real sensor data source |
| Google Colab | Development environment |

---

## 📁 Files in This Repo

| File | Description |
|---|---|
| `CyberCleanAir.ipynb` | Main notebook — sensor analysis and trust score |
| `CyberCleanAir Presentation.pptx` | Final hackathon presentation |

---

## 🏆 Hackathon
**CyberCleanAir Hackathon 2026**
West Virginia State University
April 3-4, 2026
