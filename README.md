# Manufacturing Quality & Process Risk Optimization Engine 🛠️🏭
An end-to-end data analytics pipeline designed to quantify manufacturing waste, evaluate process capabilities, and provide an interactive command center for plant operations.

---

## 📊 Interactive Executive Dashboard
*Replace this line with an image link or drag-and-drop a screenshot of your final Power BI dashboard here.*

---

## 🚀 Project Overview & Business Impact
A major retail supply chain operation lacked granular visibility into shop-floor quality metrics, leading to unquantified physical material waste and delayed production post-mortems. 

This project bridges that visibility gap by creating a unified **Data Pipeline + BI Command Center**. By linking raw manufacturing volumes to localized defect logs, the dashboard empowers plant managers to transition from reactive troubleshooting to proactive process adjustment—**safeguarding up to 15-20% of annual material capital currently lost to defective runs.**

### 📈 Core Operational Benchmarks Established:
*   **First-Time Yield (FTY):** 97.72% 🟢
*   **Average Process Defect Rate:** 2.28% ⚠️
*   **Total Project Production Target:** 57,000+ units audited

---

## 🛠️ Tech Stack & Skills Demonstrated
*   **Data Prep & Cleaning:** Python (`Pandas`, `NumPy`)
*   **Business Intelligence & Modeling:** Power BI Desktop, DAX Studio
*   **Advanced Logic Integration:** Conditional Matrix Formulations, Root-Cause Analysis

---

## 🏗️ Pipeline Architecture & Feature Engineering

### 1. The Cost of Poor Quality (COPQ) Formulation
Traditional manufacturing logs track raw error counts, which obscures the financial gravity of product failures. Using `Pandas`, a custom engineering column was formulated to calculate actual economic waste per batch:
\[\text{COPQ} = (\text{Production Volume} \times \frac{\text{Defect Rate}}{100}) \times \text{Unit Manufacturing Cost}\]

### 2. Multi-Criteria Risk Stratification
Using `NumPy`'s vectorized conditional execution, batches were split into targeted priority buckets. This code completely eliminates slow iterative loops, processing massive manufacturing matrix rows instantly:

```python
conditions = [
    (df["defect_rates"] >= 3.0) & (df["inspection_results"] == "Fail"),
    (df["defect_rates"] >= 1.5) & (df["defect_rates"] < 3.0),
    (df["defect_rates"] < 1.5) & (df["inspection_results"] == "Pass"),
]
choices = ["Critical - Action Required", "Warning - Monitor Line", "Optimal"]

df["process_risk_status"] = np.select(conditions, choices, default="Unclassified")
```

---

## 🔍 Key Analytical Insights & Discoveries

1.  **The 80/20 Rule Applied:** Over **80% of total financial scrap costs** ($\$62.32\text{K}$) are strictly concentrated in the **Skincare** and **Haircare** product segments. The Cosmetics division maintains highly stable quality compliance.
2.  **Batch Volume Inflection Point:** Scatter plot trends show that when manufacturing batch size exceeds standard limits, process stability drops, indicating tool wear or operator pacing inefficiencies.

---

## 🧮 Advanced DAX Formulations
To ensure high performance and ultra-fast visual rendering, the front-end dashboard utilizes highly optimized DAX measures rather than calculated columns:

*   **Total Financial Scrap Loss:**
    ```dax
    Total Scrap Cost = SUM(powerbi_supply_chain_master[cost_of_poor_quality])
    ```
*   **First-Time Process Yield:**
    ```dax
    Yield Efficiency = AVERAGE(powerbi_supply_chain_master[yield_efficiency]) / 100
    ```

---


