# Gujarat House Price Prediction – End-to-End ML & Streamlit App

## 📌 Project Overview
This project is an end-to-end **House Price Prediction System** built for real estate properties in **Gujarat (Ahmedabad & Surat)**.  
It predicts **property prices (in Lakhs)** using a Machine Learning model (**CatBoost**) and provides an interactive **Streamlit web application** for users to explore data and generate predictions.

The workflow includes:
- Data Cleaning & Preprocessing  
- Exploratory Data Analysis (EDA)  
- Feature Engineering  
- Model Selection & Training  
- Error Handling & Fixes  
- Streamlit App Deployment  

---

## 🧹 Step 1: Data Cleaning & Preprocessing
Performed deep cleaning on the raw Gujarat property dataset:

### ✔ Normalization & Formatting
- Converted all categorical features to **lowercase**  
- Standardized inconsistent text fields  

### ✔ Removal of Irrelevant/Leaky Columns
Dropped:
- `ID`  
- `State` (constant = Gujarat)  
- `Price_per_SqFt` (derived)  
- `Year_Built` (converted to age)  
- `Floor_No` & `floor_ratio` (too many nulls)

### ✔ Missing Value Handling
- **Median** for numerical features  
- **Mode** for categorical features  

### ✔ Outlier Treatment
Trimmed extreme values for:
- price  
- size (sqft)  

---

## 🔍 Step 2: Exploratory Data Analysis (EDA)
Key insights discovered:
- Price per sqft (`pps_rupees`) and property size are strongest predictors  
- Locality and amenities significantly affect median price  
- Aging properties generally show lower price trends  
- City-level pricing patterns differ for Ahmedabad vs Surat  

Visualizations included:
- Distribution plots  
- Correlation heatmaps  
- Locality-wise price comparison  
- Amenity impact analysis  

---

## 🏗️ Step 3: Feature Engineering
Created several new meaningful features:

### ✔ Binary Feature Flags
- `parking_space_bin`  
- `security_bin`  
- `is_ground`  
- `is_top`  

### ✔ Amenity Features
- `amenity_pool`  
- `amenity_garden`  
- `amenity_gym`  
- `amenity_playground`  
- `amenity_clubhouse`  
- Created `amenities_count` = sum of amenities  

### ✔ Categorical Encoding
Encoded:
- city  
- property_type  
- furnished_status  
- facing  
- owner_type  
- availability_status  
- public_transport_accessibility  

---

## 🤖 Step 4: Modeling
Multiple models were trained and compared:
- Ridge Regression  
- Random Forest  
- XGBoost  
- **CatBoost (Final Model)**  

CatBoost performed the best due to:
- Ability to handle categorical features  
- Lower RMSE  
- Better generalization  

Final model saved as:  
`final_catboost_model.pkl`

---

## 🛠️ Step 5: Issues Faced & Fixes Implemented
### ❗ CatBoost `cat_features` index error  
✔ Fixed by ensuring prediction input uses **exact same column order** as training data.  

### ❗ Case mismatch (Ahmedabad vs ahmedabad)  
✔ Forced lowercase across all inputs & dataset.  

### ❗ Dropped high-null floor features  
✔ Simplified using flags (`is_ground`, `is_top`).  

### ❗ .cbm vs .pkl model loading issues  
✔ Handled with a robust fallback loader in Streamlit.  

### ❗ Schema mismatch during prediction  
✔ Ensured prediction DataFrame matches training schema exactly.

---

## 🌐 Step 6: Deployment – Streamlit Web Application

### ✔ Sidebar Navigation  
- **About Project**  
- **House Price Prediction** (interactive form)  
- **Dataset Viewer** (raw + cleaned with download buttons)  

---

### 🏠 About Page  
Includes:
- Project overview  
- Workflow explanation  
- Expandable sections for each phase (cleaning → EDA → engineering → modeling)  
- Download links for datasets  

---

### 🎯 Prediction Page  
User inputs:
- Numerical: `size_in_sqft`, `bhk`, `pps_rupees`, `age_years`, `nearby_schools`, etc.  
- Categorical: city, property_type, furnished_status, facing, owner_type  
- Binary: parking, security  
- Floor type (ground/top/middle)  
- Amenities (gym, pool, garden, etc.)

On clicking **Predict Price**:
- Builds 1-row DataFrame  
- Auto-fills missing defaults  
- Ensures correct training schema order  
- Displays **Predicted Price (in Lakhs)**  
- Shows processed DataFrame used for prediction  

---

### 📊 Dataset Page  
- View first 200 rows of **raw** and **cleaned** datasets  
- Download full CSV files  

---

## 🧰 Tech Stack
- **Python**  
- **Pandas, NumPy** – cleaning & preprocessing  
- **Seaborn, Matplotlib** – EDA  
- **CatBoost** – modeling  
- **Joblib** – model saving  
- **Streamlit** – web app  
- **PyCharm** – development environment  

---
