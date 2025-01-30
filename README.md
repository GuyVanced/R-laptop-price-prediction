# Laptop Price Prediction Project

## 📊 Project Overview

This project focuses on **Exploratory Data Analysis (EDA)** and **Machine Learning-based price prediction** for laptops. The goal is to understand the factors that influence laptop pricing and develop accurate predictive models to estimate laptop prices based on their specifications.

## 🎯 Project Objectives

1. **Data Exploration**: Analyze laptop specifications and their relationships with pricing
2. **Feature Engineering**: Transform raw data into meaningful features for prediction
3. **Model Development**: Build and compare multiple machine learning models
4. **Performance Evaluation**: Assess model accuracy using various metrics
5. **Insights Generation**: Identify key factors affecting laptop pricing

## 📁 Project Structure

```
laptop/
├── dataset/
│   └── laptop_data.csv          # Raw laptop dataset
├── exports/
│   └── laptop_price_prediction.html  # Generated HTML report
├── Visualization/               # Generated plots and charts
│   ├── Company vs Price Relationship.png
│   ├── Correlation Analysis ALL.png
│   ├── Distribution of Laptop Size.png
│   ├── Linear Regression Model.png
│   ├── Random Forest Model.png
│   └── ... (other visualizations)
├── laptop_price_prediction.Rmd  # Main analysis file
└── README.md                    # This file
```

## 🛠️ Technologies Used

### R Libraries
- **Data Manipulation**: `tidyverse`, `dplyr`
- **Visualization**: `ggplot2`, `corrplot`, `scales`
- **Machine Learning**: `randomForest`, `caret`, `e1071`, `MASS`
- **Data Processing**: `caTools`, `car`
- **Documentation**: `knitr`

## 📈 Data Analysis Process

### 1. Data Loading and Initial Exploration
- Loaded laptop dataset with specifications and pricing information
- Performed initial data quality checks (duplicates, missing values)
- Analyzed dataset dimensions and structure

### 2. Data Preprocessing
- **Currency Conversion**: Converted prices from INR to NPR (1 INR = 1.6 NPR)
- **Unit Standardization**: 
  - Removed "GB" suffix from RAM values
  - Removed "kg" suffix from Weight values
  - Converted to numeric data types

### 3. Exploratory Data Analysis (EDA)

#### Price Distribution Analysis
- Analyzed overall price distribution patterns
- Identified right-skewed distribution requiring log transformation

#### Company and Brand Analysis
- **Razer** laptops found to be significantly more expensive
- Analyzed price variations across different laptop manufacturers

#### Technical Specifications Analysis
- **CPU Impact**: Intel Core i7 processors command higher prices
- **RAM Analysis**: 8GB RAM most common, but higher RAM doesn't always mean higher price
- **GPU Analysis**: NVIDIA GPUs significantly more expensive than Intel/AMD
- **Storage**: SSD storage shows positive correlation with price, HDD shows negative correlation

#### Display Features
- **Touchscreen**: Limited impact on pricing
- **IPS Panel**: Analyzed prevalence and price impact
- **Screen Resolution**: Created PPI (Pixels Per Inch) feature from resolution and screen size

#### Operating System
- **Windows** laptops generally more expensive than Mac and Linux variants

### 4. Feature Engineering

#### Memory Storage Processing
- Separated complex memory configurations (e.g., "256GB SSD + 1TB HDD")
- Created separate features for HDD, SSD, Hybrid, and Flash Storage
- Removed low-correlation features (Hybrid, Flash Storage)

#### Screen Resolution Processing
- Extracted X and Y resolution values
- Calculated PPI (Pixels Per Inch) for better screen quality representation
- Removed redundant resolution columns

#### Categorical Encoding
- Converted categorical variables to numeric using factor encoding
- Processed: Company, TypeName, OS, CPU brand, GPU brand

### 5. Data Transformation
- Applied **logarithmic transformation** to price variable to handle right-skewed distribution
- Removed outliers using robust linear model (RLM) with MAD-based threshold

## 🤖 Machine Learning Models

### Model Comparison

| Model | R² Score | MAE | Performance |
|-------|----------|-----|-------------|
| **Random Forest** | 0.988 | Low | ⭐⭐⭐⭐⭐ Best |
| Support Vector Regression | 0.861 | Medium | ⭐⭐⭐⭐ Good |
| Linear Regression | Lower | Higher | ⭐⭐⭐ Fair |

### 1. Linear Regression
- **Performance**: Baseline model with moderate accuracy
- **Use Case**: Simple, interpretable predictions
- **Limitations**: Assumes linear relationships

### 2. Support Vector Regression (SVR)
- **Performance**: 86% accuracy (R² = 0.861)
- **Configuration**: Radial kernel, epsilon-regression
- **Advantages**: Handles non-linear relationships well

### 3. Random Forest
- **Performance**: 98.8% accuracy (R² = 0.988)
- **Configuration**: 200 trees, mtry = 4
- **Advantages**: 
  - Highest accuracy
  - Handles non-linear relationships
  - Feature importance ranking
  - Robust to outliers

## 📊 Key Findings

### Price Influencing Factors
1. **Brand**: Razer laptops command premium prices
2. **Processor**: Intel Core i7 processors significantly increase price
3. **Graphics**: NVIDIA GPUs add substantial value
4. **Storage**: SSD storage positively correlates with price
5. **Operating System**: Windows laptops generally more expensive

### Data Insights
- **Most Common Configuration**: 8GB RAM, Intel GPU, Windows OS
- **Price Distribution**: Right-skewed, requiring log transformation
- **Storage Trend**: SSD adoption correlates with higher prices
- **Brand Premium**: Certain brands (Razer) command significant price premiums

## 📈 Model Performance

### Random Forest Model (Best Performer)
- **R² Score**: 0.988 (98.8% accuracy)
- **Advantages**: 
  - Excellent prediction accuracy
  - Robust to outliers
  - Handles complex feature interactions
- **Visualization**: Actual vs Predicted price plots show excellent alignment

## 🚀 Usage Instructions

### Prerequisites
- R environment with required packages
- RStudio (recommended)

### Running the Analysis
1. **Install Dependencies**:
   ```r
   install.packages(c("tidyverse", "randomForest", "caret", "e1071", "MASS", "corrplot"))
   ```

2. **Load the R Markdown File**:
   - Open `laptop_price_prediction.Rmd` in RStudio
   - Ensure `laptop_data.csv` is in the dataset folder

3. **Run the Analysis**:
   - Click "Knit" to generate HTML report
   - Or run code chunks individually

### Output Files
- **HTML Report**: `exports/laptop_price_prediction.html`
- **Visualizations**: Stored in `Visualization/` folder
- **Model Results**: Embedded in the R Markdown output

## 📋 Dataset Information

### Features Analyzed
- **Company**: Laptop manufacturer
- **TypeName**: Laptop type/category
- **Inches**: Screen size
- **ScreenResolution**: Display resolution
- **Cpu**: Processor specifications
- **Ram**: Memory capacity
- **Memory**: Storage configuration
- **Gpu**: Graphics card
- **OpSys**: Operating system
- **Weight**: Laptop weight
- **Price**: Target variable (in NPR)

### Data Quality
- **No Missing Values**: Clean dataset
- **No Duplicates**: Unique records
- **Currency**: Prices converted to NPR
- **Units**: Standardized (GB for RAM, kg for weight)

## 🔍 Business Applications

### For Consumers
- **Price Estimation**: Predict laptop prices based on desired specifications
- **Budget Planning**: Understand cost implications of different configurations
- **Value Assessment**: Identify overpriced or underpriced laptops

### For Retailers
- **Pricing Strategy**: Set competitive prices based on market analysis
- **Inventory Management**: Understand price-demand relationships
- **Market Analysis**: Identify pricing trends and opportunities

### For Manufacturers
- **Product Development**: Understand feature-price relationships
- **Market Positioning**: Identify pricing sweet spots
- **Competitive Analysis**: Benchmark against market prices

## 📚 Technical Details

### Data Preprocessing Steps
1. **Currency Conversion**: INR → NPR
2. **Unit Standardization**: Remove suffixes, convert to numeric
3. **Feature Engineering**: Create derived features (PPI, storage types)
4. **Categorical Encoding**: Convert categories to numeric
5. **Outlier Removal**: Use RLM with MAD threshold
6. **Log Transformation**: Handle price distribution skewness

### Model Training
- **Train-Test Split**: 85% training, 15% testing
- **Cross-Validation**: Built into model training process
- **Hyperparameter Tuning**: Optimized for each algorithm
- **Performance Metrics**: R² score and Mean Absolute Error (MAE)

## 🤝 Contributing

This project is part of a Statistical Inference and Modeling course assignment. For questions or improvements:

1. Review the R Markdown file for detailed methodology
2. Check the generated visualizations for insights
3. Examine the model performance comparisons

## 📄 License

This project is created for educational purposes as part of academic coursework in Statistical Inference and Modeling.

---

**Note**: This analysis demonstrates comprehensive data science workflow from data exploration to model deployment, showcasing both statistical analysis and machine learning techniques for real-world price prediction problems.
