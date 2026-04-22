# 🏠 House Price Prediction Project

## 📋 Task Objective

The primary objective of this project is to build a **regression model** that accurately predicts house prices based on various property features. The goal is to understand which factors most significantly influence housing prices and create a reliable prediction system that can estimate property values using characteristics such as:

- Square footage (Area)
- Number of bedrooms and bathrooms
- Number of floors
- Year built
- Location
- Property condition
- Garage presence

## 📊 Dataset Used

**Dataset Name:** House Price Prediction Dataset

**Source:** Available on Kaggle

**Dataset Statistics:**
- **Total Records:** 2,000 houses
- **Total Features:** 10 columns (including target variable)
- **Target Variable:** Price (house price in dollars)

### Features Description:

| Feature | Description | Data Type |
|---------|-------------|-----------|
| Id | Unique identifier for each property | Integer |
| Area | Square footage of the property | Integer |
| Bedrooms | Number of bedrooms | Integer |
| Bathrooms | Number of bathrooms | Integer |
| Floors | Number of floors | Integer |
| YearBuilt | Year the property was constructed | Integer |
| Location | Property location category | Categorical |
| Condition | Property condition rating | Categorical |
| Garage | Presence of garage | Categorical |
| Price | House price (target variable) | Integer |

### Data Distribution:
- **Price Range:** $50,000 - $1,000,000+
- **Locations:** Downtown, Suburban, Urban, Rural
- **Conditions:** Poor, Fair, Good, Excellent

## 🧠 Models Applied

### 1. **Linear Regression**
- Served as the baseline model
- Assumes linear relationship between features and price
- Provides interpretable coefficients for feature importance

### 2. **Gradient Boosting Regressor**
- Ensemble learning method
- Builds multiple decision trees sequentially
- Each tree corrects errors from previous trees
- Handles non-linear relationships effectively

### 3. **Hyperparameter Tuning** (GridSearchCV)
- Optimized Gradient Boosting parameters:
  - `n_estimators`: 100-200 trees
  - `max_depth`: 3-7 levels
  - `learning_rate`: 0.05-0.1
  - `min_samples_split`: 2-5

### Preprocessing Steps:
1. Removal of ID column
2. Outlier detection and analysis
3. Encoding categorical variables:
   - Location (ordinal encoding based on price)
   - Condition (Poor=0, Fair=1, Good=2, Excellent=3)
   - Garage (No=0, Yes=1)
4. Feature engineering:
   - Age = 2024 - YearBuilt
   - TotalRooms = Bedrooms + Bathrooms
   - Area_per_Room = Area / (TotalRooms + 1)
   - Is_New = YearBuilt >= 2000
5. Feature scaling using StandardScaler

## 📈 Key Results and Findings

### Model Performance Comparison:

| Model | MAE (Test) | RMSE (Test) | R² Score (Test) |
|-------|------------|-------------|-----------------|
| Linear Regression | ~$260,000 | ~$330,000 | ~0.48 |
| Gradient Boosting | ~$225,000 | ~$295,000 | ~0.58 |
| **Tuned Gradient Boosting** | **~$210,000** | **~$280,000** | **~0.62** |

### Cross-Validation Results (5-fold):
- **Linear Regression:** Mean R² = 0.47 (±0.08)
- **Tuned Gradient Boosting:** Mean R² = 0.60 (±0.06)

### 🔍 Key Findings:

#### 1. **Most Important Features for Price Prediction:**

| Rank | Feature | Importance Score (GB) |
|------|---------|----------------------|
| 1 | Area (Square Footage) | 0.42 |
| 2 | Location | 0.18 |
| 3 | Age of Property | 0.12 |
| 4 | Condition | 0.09 |
| 5 | Garage Presence | 0.06 |

#### 2. **Location Impact on Prices:**
- **Downtown:** Highest average prices ($550,000+)
- **Suburban:** Moderate prices ($480,000+)
- **Rural:** Lower prices ($420,000+)
- **Urban:** Lowest average prices ($400,000+)

#### 3. **Condition Impact:**
- **Excellent:** Premium of 25-35% over Poor condition
- **Good:** Premium of 15-20% over Poor condition
- **Fair:** Slight premium of 5-10% over Poor condition

#### 4. **Correlation Insights:**
- **Strong positive correlation:** Area ↔ Price (0.65)
- **Moderate positive correlation:** Bathrooms ↔ Price (0.42)
- **Weak correlation:** Bedrooms ↔ Price (0.15)
- **Negative correlation:** Age ↔ Price (-0.28)

### 💡 Business Insights:

1. **Square footage is the king** - Each additional 100 sq ft increases predicted price by approximately $15,000-20,000

2. **Location matters significantly** - Downtown properties command 30-40% premium over similar properties in Urban areas

3. **Newer properties sell for more** - Houses built after 2000 sell for 20-25% premium

4. **Condition upgrades provide ROI** - Moving from Fair to Excellent condition can increase value by 25-30%

5. **Garage adds value but not as much as expected** - Presence of garage adds ~8-12% to property value

## 📊 Visualizations Included:

1. Price distribution histogram
2. Area vs Price scatter plot
3. Average price by location (bar chart)
4. Price distribution by condition (box plots)
5. Year built vs Price trend
6. Correlation heatmap
7. Predicted vs Actual prices (scatter plots)
8. Residual analysis plots
9. Feature importance charts

## 🛠️ Technologies Used:

- **Python 3.8+**
- **Pandas** - Data manipulation
- **NumPy** - Numerical operations
- **Matplotlib & Seaborn** - Data visualization
- **Scikit-learn** - Machine learning models and preprocessing
- **Jupyter Notebook** - Interactive development environment


## 🚀 How to Run:

1. **Clone the repository**
```bash
git clone <repository-url>
cd house-price-prediction

Install dependencies

bash
pip install -r requirements.txt
Launch Jupyter Notebook

bash
jupyter notebook house_price_prediction.ipynb
