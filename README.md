# Supply Chain Performance Analysis

## 📌 Project Overview
Inefficient supply chains increase delivery delays and operational costs.  
This project analyzes supplier and logistics data to evaluate performance metrics, predicts delivery delays using machine learning, and builds dashboards for monitoring supply chain efficiency.

---

## 🎯 Objectives
- Analyze historical trips and route schedules to identify delays and inefficiencies.
- Compare **actual vs. planned performance** using OSRM data.
- Predict potential delays using **Machine Learning** models.
- Build interactive **dashboards** to monitor KPIs for decision-making.

---

## 🗂 Dataset Description
The dataset contains logistics and trip information with the following key columns:

| Column | Description |
|--------|-------------|
| `data` | Indicates whether the record is for training or testing. |
| `trip_uuid` | Unique identifier for each trip. |
| `route_schedule_uuid` | Unique identifier for each scheduled route. |
| `route_type` | Type of route (Carting / FTL). |
| `source_center` / `destination_center` | Codes of origin and destination centers. |
| `od_start_time` / `od_end_time` | Start and end time of the origin-destination trip. |
| `actual_time` | Actual time taken for the trip. |
| `osrm_time` / `osrm_distance` | Estimated time and distance by OSRM routing engine. |
| `factor` / `segment_factor` | Performance deviation factors. |
| `is_cutoff` / `cutoff_factor` | Cutoff flag and related factor. |

---

## 🛠 Tech Stack
- **Python (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn)**  
  For data cleaning, analysis, visualization, and ML modeling.
- **Power BI**  
  For building dashboards and KPIs monitoring.
- **OSRM (Open Source Routing Machine)**  
  Provides route time and distance estimates for benchmarking.
- **Git/GitHub**  
  Version control and project repository management.

---

## 🔍 Methodology

### 1. Data Understanding & Cleaning
- Convert timestamp columns to datetime.
- Handle missing values for cutoff and factor columns.
- Separate features into **trip-level**, **route-level**, and **segment-level**.

### 2. Feature Engineering
- **Trip duration**: `od_end_time - od_start_time`
- **Time deviation**: `actual_time - osrm_time`
- **Distance deviation**: `actual_distance_to_destination - osrm_distance`
- **Delay flag**: `is_delayed = 1 if actual_time > osrm_time else 0`

### 3. Exploratory Data Analysis (EDA)
- Analyze delay patterns by:
  - Route type (`Carting` vs `FTL`)
  - Scheduled routes
  - Source & destination centers
  - Cutoff impact
- Segment-level analysis for efficiency evaluation.

### 4. Machine Learning
- Problem type: **Binary classification** (predict delayed trips)
- Features:
  - Pre-trip features: `route_type`, `osrm_time`, `osrm_distance`, `is_cutoff`, `segment_osrm_time`, `segment_osrm_distance`
- Model used:
  - Random Forest Classifier
  - Train-test split (80%-20%)
- Metrics: Accuracy, confusion matrix, and F1-score.

### 5. Dashboard & KPI Monitoring
- Power BI dashboards to track:
  - Average delay per route type
  - Delay rate per scheduled route
  - Cutoff impact on delays
  - OSRM vs actual performance
- Interactive visuals for management decision support.

---

## 💡 Key Insights
- **Carting routes** have higher delays than FTL routes.
- Scheduled routes with **high factor values** consistently show inefficiency.
- Cutoff events significantly increase the probability of delays.
- Segment-level analysis helps identify bottlenecks and problematic route legs.

---

## 🔮 Scope & Future Enhancements
- Extend ML models using **XGBoost, Gradient Boosting, or RNNs** for better predictions.
- Integrate **real-time data streaming** for live delay prediction.
- Optimize route scheduling using reinforcement learning or metaheuristics.
- Include cost analysis and environmental impact evaluation.
- Build a **web-based interactive dashboard** for management.

---

## 🏆 What We Learn
- Real-world **supply chain analytics and performance measurement**.
- **Data preprocessing and feature engineering** in logistics datasets.
- Using **OSRM for benchmarking** actual vs expected trip performance.
- Building **predictive ML models** for delivery delay forecasting.
- Creating **visual dashboards** for KPIs and operational decision-making.

---

## 📂 Repository Structure
