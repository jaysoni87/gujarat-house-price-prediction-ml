# Gujarat House Price Prediction – End-to-End ML & Streamlit App

## 📁 Access to Large Files (Dataset + Model)
This project contains **large data files and model files (over 90 MB)** which cannot be uploaded directly to GitHub due to file size limits.

To access:
- Raw Dataset  
- Cleaned Dataset (`gujarat_clean_model_table.csv`)  
- Trained CatBoost Model (`final_catboost_model.pkl`)  
- Backup Model Files (`.cbm`, `.joblib`)  

👉 **Download the entire project folder from Google Drive:**  
**[Click Here to Download](https://drive.google.com/drive/folders/1uM9Vs4HW8Lc8WkDQZd1wwwbeY-4pDHKQ?usp=sharing)**

---

## 📌 Project Overview
This project is an end-to-end **House Price Prediction System** built for real estate properties in **Gujarat (Ahmedabad & Surat)**. It predicts **property prices (in Lakhs)** using a Machine Learning model (**CatBoost**) and provides an interactive **Streamlit web application** for users to explore data and generate predictions.

The workflow includes:
- Data Cleaning & Preprocessing  
- Exploratory Data Analysis (EDA)  
- Feature Engineering  
- Model Selection & Training  
- Error Handling & Fixes  
- Streamlit App Deployment  

---

## 🧹 Step 1: Data Cleaning & Preprocessing
Performed extensive cleaning operations on the raw dataset:

### ✔ Normalization & Formatting
- All categorical features converted to lowercase  
- Inconsistent text formats standardized  

### ✔ Removal of Irrelevant / Leaky Columns
Dropped:
- `ID`  
- `State` (always Gujarat)  
- `Price_per_SqFt` (derived from price and size)  
- `Year_Built` (converted into `age_years`)  
- `Floor_No` and `floor_ratio` (too many nulls)

### ✔ Missing Value Handling
- Median for numeric columns  
- Mode for categorical columns  

### ✔ Outlier Treatment
- Removed extreme values for price & property size  

---

## 🔍 Step 2: Exploratory Data Analysis (EDA)
Insights derived:
- Strong correlation between price per sqft and final house price  
- Size (sqft) is a major contributor  
- Amenity-rich buildings have significantly higher median prices  
- Age of property affects value  
- Ahmedabad and Surat show different pricing patterns

Visuals included:
- Distribution plots  
- Heatmaps  
- Locality-wise comparison  
- Amenity impact charts  

---

## 🏗️ Step 3: Feature Engineering
Created meaningful new features:

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
- `amenities_count` = sum of all amenity flags  

### ✔ Categorical Transformations
Encoded:
- city  
- furnished_status  
- property_type  
- facing  
- owner_type  
- availability_status  
- public_transport_accessibility  

---

## 🤖 Step 4: Modeling
Models tested:
- Ridge Regression  
- Random Forest  
- XGBoost  
- **CatBoost (Final Model)**  

### ✔ Why CatBoost?
- Handles categorical data efficiently  
- Lowest RMSE among all models  
- Highly stable predictions  

Final model stored as:
- `final_catboost_model.pkl`

(Download via Google Drive)

---

## 🛠️ Step 5: Issues & Fixes

### ❗ CatBoost categorical index mismatch  
✔ Fixed by ensuring prediction DataFrame matches original feature order.  

### ❗ Case mismatch (Ahmedabad vs ahmedabad)  
✔ Standardized to lowercase everywhere.  

### ❗ Dropped high-null floor features  
✔ Replaced with `is_ground` & `is_top` flags.  

### ❗ Model loading issues (`.pkl`, `.cbm`)  
✔ Added fallback logic in Streamlit to load multiple formats.  

### ❗ Schema mismatch  
✔ Enforced strict column alignment during prediction.  

---

## 🌐 Step 6: Deployment – Streamlit App

### ✔ Sidebar Navigation
- **About Project**  
- **House Price Prediction** (interactive form)  
- **Dataset Viewer** (raw & cleaned + download options)  

---

### 🏠 About Page
Includes:
- Project summary  
- Workflow explanation  
- Download dataset & model  
- Expandable sections (Cleaning → EDA → Engineering → Modeling)  

---

### 🎯 Prediction Page
Takes user input:
- Numeric values  
- Categorical dropdowns  
- Amenity checkboxes  
- Parking/security flags  
- Floor position (ground / top / middle)

Outputs:
- **Predicted House Price (in Lakhs)**  
- The exact processed DataFrame row used for prediction  

---

### 📊 Dataset Viewer Page
- Displays first 200 rows of raw & cleaned datasets  
- Buttons to download CSV files  

(Large files downloadable via Google Drive)

---

## 🧰 Tech Stack
- Python  
- Pandas, NumPy  
- Seaborn, Matplotlib  
- CatBoost  
- Joblib  
- Streamlit  
- PyCharm IDE  

---
