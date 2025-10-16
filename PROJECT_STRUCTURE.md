# SMH Project Structure & Guidelines

## Part 0: Project Initialization & Overview

This section sets the stage. It should be concise and professional, telling the reader what you're doing and why.

### 1. Introduction & Project Goals

**Objective:** State the primary goal: "o build and evaluate several machine learning models using PySpark to predict both the likelihood of depression and academic performance among students based on academic, lifestyle, and demographic factors."

**Significance:** Briefly explain why this is important (e.g., addressing the growing mental health crisis in academia, providing potential for early intervention). This maps to the "motivation and significance" part of the proposal.

**Technical Stack:** List the technologies used (e.g., Python, Apache Spark, Spark MLlib, Pandas, Matplotlib). This shows you understand the "New Technologies" criterion.

### 2. Project Architecture & Workflow

**Description:** Explain the end-to-end process. "This project follows a standard data science workflow: data is ingested from multiple CSV files, merged, and pre-processed within a Spark environment. Several ML models from Spark's MLlib library are then trained and evaluated. Finally, the results are visualised to provide actionable insights."

**Workflow Diagram:** (Crucial for top marks) Create a simple diagram and include it here. This directly addresses the "Architecture Design" requirement.

### 3. Environment Setup

- A single code cell to import all necessary libraries (pyspark, pandas, matplotlib.pyplot, etc.).
- Another cell to initialize your SparkSession. Add comments explaining what the code does.

## Part 1: Data Loading and Exploratory Data Analysis (EDA)

Here, you get to know your data. This is where you demonstrate curiosity and analytical thinking.

### 1.1. Ingest Data

Load your four prepared CSV files (student_info.csv, etc.) into separate Spark DataFrames.

### 1.2. Merge Datasets

Join the four DataFrames on the id column to create a single, unified dataset for analysis.

### 1.3. Initial Data Inspection

- Use `.printSchema()` to show the data types.
- Use `.show(5)` to display a sample.
- Use `.describe().show()` to get summary statistics for numerical columns.

### 1.4. Data Quality Check

- Systematically check for null or NaN values in each column.
- Formulate and justify your strategy (e.g., "Missing CGPA values will be filled with the mean, as it's a critical feature..."). This is a key "data pre-processing" step.

### 1.5. Exploratory Visualisation

- **Target Variable Distribution:** A bar chart showing the balance between students with and without depression. Is the dataset imbalanced?
- **Categorical Features:** Bar charts showing distributions for Gender, City, Degree, etc.
- **Numerical Features:** Histograms for Age, CGPA, and Work/Study Hours.

## Part 2: Feature Engineering & Pre-processing

This section is about preparing your data for the machine learning models. It shows your technical understanding of how Spark MLlib works.

### 2.1. Data Cleaning

Implement the cleaning strategy you decided on in Part 1 (e.g., filling null values).

### 2.2. Feature Transformation

- Explain why categorical features (like text) need to be converted to numbers for ML models.
- Use StringIndexer and OneHotEncoder to transform your categorical columns.

### 2.3. Feature Assembling

- Use VectorAssembler to combine all your processed feature columns into a single vector column named features. This is a mandatory step for all Spark MLlib models.

## Part 3: Machine Learning Modelling

This is the core of your implementation. The marking guide requires at least four different functionalities. Frame each model as a distinct "functionality."

### 3.1. Data Splitting

Split your master DataFrame into training (e.g., 80%) and testing (e.g., 20%) sets.

### 3.2. Functionality 1: Classification - Predicting Depression

- Train a LogisticRegression model.
- Evaluate its performance using BinaryClassificationEvaluator (for Area Under ROC) and by calculating accuracy, precision, and recall from a confusion matrix.
- Interpret and visualise: Show the confusion matrix and explain what the metrics mean.

### 3.3. Functionality 2: Regression - Predicting Academic Performance (CGPA)

- Train a LinearRegression or RandomForestRegressor model to predict CGPA.
- Evaluate using RegressionEvaluator (RMSE and R²).
- Interpret: Which factors are the strongest predictors of a student's CGPA?

### 3.4. Functionality 3: Clustering - Identifying At-Risk Student Groups

- Use KMeans clustering. Justify your choice for the number of clusters (k) using the "Elbow Method" and a plot.
- Interpret: Analyse the characteristics of each cluster. You might find a cluster representing "High-Achieving, High-Stress" students, for example. This demonstrates "Excellence and Innovation".

### 3.5. Functionality 4: Association Rule Mining - Discovering Hidden Patterns

- Use the FPGrowth algorithm.
- Interpret: Display the rules with the highest "confidence" and "lift". For example, you might find a rule like {Low Sleep, High Financial Stress} => {Suicidal Thoughts}.

## Part 4: In-Depth Analysis & Key Findings

Go beyond the basic model building. This is where you create the "wow" factor for the competition.

### 4.1. Feature Importance Analysis

- From your best-performing classification model (e.g., Logistic Regression or a tree-based model), extract the feature importances.
- Create a bar chart to visualise which factors are the most powerful predictors of depression.

### 4.2. "Deep Dive" Visualisation

- Create a compelling chart that summarises a key finding. For instance, a grouped bar chart showing the average AcademicPressure and FinancialStress for depressed vs. non-depressed students.

## Part 5: Conclusion & Future Work

Wrap up your project with a strong conclusion.

### 5.1. Summary of Findings

Briefly summarise the key insights you discovered. What were the most important predictors? What student profiles did you identify?

### 5.2. Project Reflection

Discuss the benefits of using a cloud computing tool like Spark for this analysis (e.g., scalability for larger datasets, unified framework for EDA and ML). This links back to the proposal criteria.

### 5.3. Future Work

Suggest what could be done next (e.g., "Deploying the classification model as a real-time web application for student wellness checks," or "Incorporating more complex models like Gradient-Boosted Trees").

---

## Key Marking Criteria to Address

### 1. Motivation and Significance

- Clearly articulate why this problem matters
- Connect to real-world mental health challenges in academia

### 2. Architecture Design

- Include a workflow diagram
- Explain the technical stack and rationale

### 3. New Technologies

- Demonstrate proficiency with PySpark and Spark MLlib
- Show understanding of distributed computing concepts

### 4. Data Pre-processing

- Systematic approach to handling missing data
- Justification for transformation choices

### 5. At Least Four Functionalities

- Classification (depression prediction)
- Regression (CGPA prediction)
- Clustering (student segmentation)
- Association Rule Mining (pattern discovery)

### 6. Excellence and Innovation

- Deep dive analysis beyond basic model building
- Creative visualizations and insights
- Novel approaches to student mental health analysis

### 7. Quality of Implementation

- Clean, well-commented code
- Proper use of Spark transformations and actions
- Efficient data processing

---

## Tips for Success

1. **Start Early**: This is a comprehensive project that requires time for experimentation and refinement.
2. **Document Everything**: Include explanations for every major decision and transformation.
3. **Visualize Extensively**: Good visualizations can significantly boost your marks.
4. **Interpret Results**: Don't just show numbers - explain what they mean in the context of student mental health.
5. **Test Multiple Models**: Try different algorithms and compare their performance.
6. **Focus on Insights**: The goal isn't just to build models, but to discover actionable insights about student mental health.

---

_This document serves as your constant reference throughout the project development process._
