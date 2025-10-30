## Worker-Productivity-Prediction
The project predicts garment factory worker productivity using regression models (RandomForest, XGBoost, LightGBM) and compares two strategies for handling missing wip values — MICE imputation vs. feature removal. 

### 📂 Dataset Composition
- **Source:** Garment Worker Productivity Dataset
- **Target:** actual_productivity (continuous variable)
- **Features:** 10 core variables (e.g., targeted_productivity, incentive, smv, over_time, no_of_workers, wip, day, quarter, department)
- **Samples:** 1,197 records

### ⚙️ Workflow
**Exploratory Data Analysis (EDA)**

- Checked data consistency, missing values, and categorical balance.
- Found strong productivity variation across departments and days.
- wip missingness pattern: finishing = 100% missing, sewing = 0%.

**Preprocessing & Encoding**

- Removed rows with missing target values.
- Applied one-hot encoding to day, quarter, and department.
- Dropped redundant dummy variables (day_Sunday, quarter_Quarter2, etc.) to prevent multicollinearity.

**Imputation vs. Removal Strategy**

- **UseMICE_WIP:** Applied IterativeImputer (MICE) using LightGBMRegressor as estimator to fill wip values.
- **DropWIP:** Completely removed the wip column to reduce noise and bias from unreliable imputation.

**Model Training and Evaluation**

- Trained RandomForest, XGBoost, and LightGBM on both settings.
- Evaluated using RMSE, MAE, and R² metrics.
- Compared results across both versions and models to identify stability and generalization.

**Feature Importance & SHAP Analysis**

- Top contributing variables across models:
  - targeted_productivity, smv, incentive, no_of_workers, and over_time.
- MICE-based models showed less feature consistency, while DropWIP maintained clearer importance ordering.



<img width="702" height="417" alt="image" src="https://github.com/user-attachments/assets/23dcf201-daf1-4310-baa2-0ca8d8dd20ba" />

<img width="714" height="381" alt="image" src="https://github.com/user-attachments/assets/a2ec4744-bc0d-4613-ba33-ac2d043d4742" />

