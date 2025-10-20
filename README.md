# 🧠 Predicting Student Depression: A Big Data Analytics Approach with Apache Spark

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://python.org)
[![Apache Spark](https://img.shields.io/badge/Apache%20Spark-4.0.1-orange.svg)](https://spark.apache.org)
[![PySpark](https://img.shields.io/badge/PySpark-MLlib-green.svg)](https://spark.apache.org/docs/latest/ml-guide.html)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **A comprehensive machine learning pipeline leveraging Apache Spark to predict student depression and identify at-risk populations through advanced analytics on academic, lifestyle, and demographic factors.**

## 🎯 Project Overview

This project addresses one of the most pressing challenges in modern education: **student mental health**. By analyzing a comprehensive dataset of 27,901 students across India, I've developed a scalable machine learning framework that can identify students at risk of depression and provide actionable insights for early intervention.

### 🌟 Key Achievements

- **92.3% AUC Score** in depression prediction using Logistic Regression
- **88.24% Recall Rate** ensuring minimal false negatives in critical mental health screening
- **4 Distinct Student Profiles** identified through advanced clustering analysis
- **Scalable Architecture** capable of processing millions of student records
- **Actionable Insights** revealing strong correlations between stress factors and mental health outcomes

## 🚀 Why This Matters

Student mental health is a **global crisis**. According to recent studies:

- 60% of college students report overwhelming anxiety
- 40% experience severe depression
- Suicide is the second leading cause of death among college students

This project demonstrates how **big data technologies** can transform reactive mental health support into **proactive, data-driven interventions**.

## 🏗️ Technical Architecture

### System Design

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Data Sources  │    │  Cloud Storage  │    │  Apache Spark   │    │  ML Pipeline    │
│                 │    │                 │    │                 │    │                 │
│ • Student Info  │───▶│ • Google Cloud  │───▶│ • Data Ingestion│───▶│ • Classification│
│ • Academic Data │    │ • Storage (GCS) │    │ • Preprocessing │    │ • Regression    │
│ • Lifestyle     │    │ • Local Files   │    │ • Feature Eng.  │    │ • Clustering    │
│ • Mental Health │    │ • Hybrid Mode   │    │ • ML Training   │    │ • Association   │
└─────────────────┘    └─────────────────┘    └─────────────────┘    └─────────────────┘
```

### Technology Stack

- **Core Engine**: Apache Spark 4.0.1 with PySpark
- **Machine Learning**: Spark MLlib (Logistic Regression, Linear Regression, K-Means, FPGrowth)
- **Data Processing**: Distributed computing for 27K+ student records
- **Cloud Storage**: Google Cloud Storage (GCS) for scalable data storage and access
- **Visualization**: Matplotlib, Seaborn for comprehensive data insights
- **Languages**: Python 3.x with advanced data science libraries

## 📊 Dataset Overview

### Data Source

This project utilizes the **Student Depression Dataset** from Kaggle, a comprehensive collection of student mental health data from across India. The dataset provides a rich foundation for understanding the complex interplay between academic, lifestyle, and mental health factors.

**Dataset Reference**: [Student Depression Dataset](https://www.kaggle.com/datasets/adilshamim8/student-depression-dataset) by Adil Shamim on Kaggle

### Dataset Composition

Our comprehensive dataset includes **27,901 student records** across four integrated data sources:

| Dataset            | Records | Key Features                                         | Sample Variables                                       |
| ------------------ | ------- | ---------------------------------------------------- | ------------------------------------------------------ |
| **Student Info**   | 27,901  | Demographics, Location, Academic Level               | Gender, Age, City, Profession, Degree                  |
| **Academic Data**  | 27,901  | CGPA, Academic Pressure, Study Satisfaction          | CGPA, Academic Pressure, Work/Study Hours              |
| **Lifestyle Data** | 27,901  | Sleep Patterns, Diet, Financial Stress               | Sleep Duration, Dietary Habits, Financial Stress       |
| **Mental Health**  | 27,901  | Depression Status, Suicidal Thoughts, Family History | Depression (Binary), Suicidal Thoughts, Family History |

### Data Characteristics

- **Total Features**: 18 comprehensive variables spanning demographic, academic, lifestyle, and mental health dimensions
- **Geographic Coverage**: Students from major Indian cities including Bangalore, Mumbai, Delhi, Chennai, and others
- **Academic Diversity**: Various degree programs from undergraduate to PhD levels
- **Mental Health Indicators**: Binary depression classification with supporting risk factors
- **Data Quality**: High-quality dataset with minimal missing values (only 3 missing values in Financial Stress)

### Key Data Insights

- **Class Distribution**: Moderate imbalance with ~58% of students classified as depressed
- **Age Range**: Primarily 18-35 years, representing typical student demographics
- **Geographic Patterns**: Significant regional variations in mental health outcomes
- **Academic Performance**: CGPA distribution shows distinct peaks at integer values (7.0, 7.5, 8.0)
- **Stress Factors**: Academic and financial stress show strong correlations with mental health outcomes

### Data Preprocessing & Methodology

The dataset underwent comprehensive preprocessing to ensure optimal model performance:

- **Data Integration**: Four separate CSV files merged using inner joins on student ID
- **Type Correction**: Automatic schema inference with manual correction for numerical columns containing placeholder values
- **Missing Value Handling**: Mean imputation for the 3 missing Financial Stress values
- **Feature Engineering**: Categorical variables encoded using StringIndexer and OneHotEncoder
- **Feature Assembly**: All features combined into a single vector using VectorAssembler for Spark MLlib compatibility
- **Data Splitting**: 80/20 train-test split with fixed random seed for reproducibility

## 🔬 Machine Learning Pipeline

### 1. Classification: Depression Prediction

- **Algorithm**: Logistic Regression with Spark MLlib
- **Performance**: 92.3% AUC, 88.24% Recall, 84.51% Accuracy
- **Impact**: Identifies students at risk with minimal false negatives

### 2. Regression: Academic Performance Analysis

- **Algorithm**: Linear Regression
- **Target**: CGPA prediction
- **Insight**: Academic performance poorly predicted by lifestyle factors (R² = 0.0168)

### 3. Clustering: Student Profile Segmentation

- **Algorithm**: K-Means with Elbow Method optimization
- **Clusters**: 4 distinct student profiles identified
- **Key Finding**: Clear separation between "At-Risk" and "Resilient" student groups

### 4. Association Rule Mining: Pattern Discovery

- **Algorithm**: FPGrowth
- **Discovery**: Strong associations between high stress and suicidal thoughts
- **Confidence**: 75.4% for academic pressure → suicidal thoughts

## 🎯 Key Findings & Insights

### Critical Risk Factors Identified

1. **Geographic Location**: Specific cities show significantly higher depression rates
2. **Academic Pressure**: Students with high academic stress are 19% more likely to have suicidal thoughts
3. **Financial Stress**: Strong correlation with both depression and suicidal ideation
4. **Family History**: 5% increase in depression rate among students with family mental health history

### Student Profile Analysis

- **At-Risk Groups**: High academic/financial stress, 69% depression rate
- **Resilient Groups**: Lower stress levels, 42-49% depression rate
- **Academic Performance**: CGPA shows minimal correlation with mental health factors

## 🛠️ Installation & Setup

### Prerequisites

```bash
# Python 3.8+
# Java 8+ (required for Spark)
# 8GB+ RAM recommended for optimal performance
```

### Quick Start

```bash
# Clone the repository
git clone https://github.com/yourusername/student-mental-health-prediction.git
cd student-mental-health-prediction

# Create virtual environment
python -m venv smh_env
source smh_env/bin/activate  # On Windows: smh_env\Scripts\activate

# Install dependencies
pip install pyspark pandas matplotlib seaborn numpy jupyter

# For Google Cloud Storage support (optional)
pip install google-cloud-storage

# Launch Jupyter Notebook
jupyter notebook notebooks/smh.ipynb
```

### Spark Configuration

#### Local Development

```python
# Initialize Spark Session for local development
spark = SparkSession.builder \
    .appName("StudentMentalHealthPrediction") \
    .config("spark.sql.adaptive.enabled", "true") \
    .config("spark.sql.adaptive.coalescePartitions.enabled", "true") \
    .getOrCreate()
```

#### Google Cloud Storage Configuration

```python
# Initialize Spark Session with GCS support
spark = SparkSession.builder \
    .appName("StudentMentalHealthPrediction") \
    .config("spark.jars.packages", "com.google.cloud.bigdataoss:gcs-connector:hadoop3-2.2.20") \
    .config("spark.hadoop.fs.gs.impl", "com.google.cloud.hadoop.fs.gcs.GoogleHadoopFileSystem") \
    .config("spark.hadoop.fs.AbstractFileSystem.gs.impl", "com.google.cloud.hadoop.fs.gcs.GoogleHadoopFS") \
    .config("spark.hadoop.google.cloud.auth.type", "APPLICATION_DEFAULT_CREDENTIALS") \
    .getOrCreate()
```

### Google Cloud Storage Setup

#### Prerequisites for GCS

1. **Google Cloud Account**: Create a Google Cloud Platform account
2. **Authentication**: Set up application default credentials
3. **Bucket Creation**: Create a GCS bucket for your data

#### Authentication Setup

```bash
# Install Google Cloud CLI
curl https://sdk.cloud.google.com | bash
exec -l $SHELL

# Authenticate with Google Cloud
gcloud auth application-default login

# Set your project ID
gcloud config set project YOUR_PROJECT_ID
```

#### Data Loading Options

The project supports **flexible data loading** with a simple configuration switch:

```python
# Configuration switch in the notebook
USE_GCS = True  # Set to True for Google Cloud Storage
USE_GCS = False # Set to False for local files

# Automatic path resolution
if USE_GCS:
    bucket_name = "your-bucket-name"
    base_path = f'gs://{bucket_name}/'
    print(f"✅ Reading data from Google Cloud Storage bucket: {bucket_name}")
else:
    base_path = "../data/"
    print("✅ Reading data from local '../data/' directory.")
```

#### Benefits of Google Cloud Storage Integration

- **Scalability**: Handle datasets of any size without local storage constraints
- **Collaboration**: Share data across team members and environments
- **Performance**: Optimized data access for distributed computing
- **Cost-Effective**: Pay only for storage and compute resources used
- **Security**: Enterprise-grade security and access controls

#### Troubleshooting GCS Issues

If you encounter issues with Google Cloud Storage integration:

1. **Authentication Errors**:

   ```bash
   # Re-authenticate with Google Cloud
   gcloud auth application-default login
   ```

2. **Bucket Access Issues**:

   - Verify bucket name is correct
   - Check bucket permissions
   - Ensure files exist in the bucket

3. **Connection Timeouts**:

   - Check internet connectivity
   - Verify firewall settings
   - Review Google Cloud quotas

4. **File Not Found Errors**:
   - Confirm file paths in bucket
   - Check file naming conventions
   - Verify file uploads completed successfully

## 📈 Performance Metrics

### Model Performance Summary

| Model                   | Metric     | Score  | Interpretation                   |
| ----------------------- | ---------- | ------ | -------------------------------- |
| **Logistic Regression** | AUC-ROC    | 92.30% | Excellent discriminative ability |
| **Logistic Regression** | Recall     | 88.24% | Minimal false negatives          |
| **Logistic Regression** | F1-Score   | 86.69% | Well-balanced performance        |
| **Linear Regression**   | R²         | 1.68%  | Poor CGPA predictability         |
| **K-Means**             | Silhouette | 0.349  | Fair cluster separation          |

### Scalability Benchmarks

- **Data Processing**: 27,901 records processed in <30 seconds
- **Model Training**: All 4 models trained in <2 minutes
- **Memory Usage**: Optimized for distributed computing
- **Scalability**: Architecture supports 1M+ student records

## 🔍 Deep Dive Analysis

### Feature Importance Analysis

The model identified **geographic location** as the strongest predictor of depression, revealing significant regional disparities in student mental health outcomes.

### Stress-Depression Correlation

Our analysis revealed a **stark correlation** between stress levels and depression:

- Depressed students: 3.7/5 average academic pressure
- Non-depressed students: 2.4/5 average academic pressure

### Association Rules Discovery

**High-Confidence Rules Identified:**

- `High Academic Pressure` → `Suicidal Thoughts` (75.4% confidence, 1.19 lift)
- `High Financial Stress` → `Suicidal Thoughts` (72.9% confidence, 1.15 lift)

## 🚀 Future Enhancements

### Immediate Opportunities

- **Real-time Deployment**: Web application for student wellness screening
- **Advanced Models**: Gradient Boosting, Random Forest, Neural Networks
- **Feature Engineering**: Social media sentiment, attendance patterns
- **Integration**: University information systems for automated monitoring

### Long-term Vision

- **Predictive Analytics**: Early warning system for at-risk students
- **Intervention Strategies**: Personalized support recommendations
- **Policy Impact**: Data-driven mental health policy development
- **Global Expansion**: Multi-institutional, multi-country analysis

## 📚 Technical Documentation

### Code Structure

```
SMH/
├── notebooks/
│   └── smh.ipynb          # Main analysis notebook with GCS integration
├── data/                  # Local data storage (optional)
│   ├── student_info.csv   # Demographic data
│   ├── academic_data.csv  # Academic performance
│   ├── lifestyle_data.csv # Lifestyle factors
│   └── mental_health.csv  # Mental health outcomes
├── PROJECT_STRUCTURE.md   # Development guidelines
├── requirements.txt       # Python dependencies
└── README.md             # This file
```

### Data Storage Options

The project supports **dual data storage modes**:

1. **Local Storage**: Traditional file-based approach using the `data/` directory
2. **Google Cloud Storage**: Cloud-based storage for scalable data access
3. **Hybrid Mode**: Seamlessly switch between local and cloud storage

#### Data Loading Configuration

The notebook includes a **configuration switch** that automatically handles data source selection:

```python
# Simple toggle for data source
USE_GCS = False  # Use local files
USE_GCS = True   # Use Google Cloud Storage
```

### Key Algorithms Implemented

- **Logistic Regression**: Binary classification for depression prediction
- **Linear Regression**: Continuous target prediction for CGPA
- **K-Means Clustering**: Unsupervised student segmentation
- **FPGrowth**: Association rule mining for pattern discovery

## 🤝 Contributing

This project demonstrates advanced data science and machine learning capabilities. Contributions are welcome in the following areas:

- **Model Enhancement**: Advanced algorithms and ensemble methods
- **Feature Engineering**: Novel feature extraction techniques
- **Visualization**: Interactive dashboards and reporting
- **Deployment**: Production-ready applications

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨🏾‍💻 Author

**David Araba**

- **Student ID**: 48093143
- **Course**: INFS3208 - Cloud Computing
- **Institution**: University of Queensland
- **Specialization**: Big Data Analytics, Machine Learning, Cloud Computing

## 🏆 Recognition

This project showcases expertise in:

- **Distributed Computing**: Apache Spark and PySpark
- **Machine Learning**: Multi-algorithm implementation
- **Data Science**: End-to-end analytics pipeline
- **Mental Health Analytics**: Domain-specific insights
- **Scalable Architecture**: Production-ready design

---

> **"Transforming student mental health through the power of big data and machine learning. Every insight discovered is a potential life saved."**

**⭐ Star this repository if you find it valuable for advancing mental health analytics!**
