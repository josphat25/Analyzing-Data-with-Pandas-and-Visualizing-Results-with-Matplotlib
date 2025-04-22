# Analyzing-Data-with-Pandas-and-Visualizing-Results-with-Matplotlib
# Description
# Objective For this Assignment:
-To load and analyze a dataset using the pandas library in Python.
-To create simple plots and charts with the matplotlib library for visualizing the data.
## answer
# import libraries 
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# load the dataset
# Example: Load CSV file
df = pd.read_csv('your_dataset.csv')  # Replace with your actual file path
# Quick overview
print(df.head())
print(df.info())
print(df.describe())

# basic data exploration
# Check for missing values
print(df.isnull().sum())
# Check unique values of categorical columns
print(df['ColumnName'].value_counts())  # Replace ColumnName
# Correlation (if numerical)
print(df.corr())

# basic visuaiazations
# Histogram of a numeric column
df['NumericColumn'].hist(bins=20)
plt.title('Distribution of NumericColumn')
plt.xlabel('Value')
plt.ylabel('Frequency')
plt.show()
# Bar plot of a categorical column
df['CategoryColumn'].value_counts().plot(kind='bar')
plt.title('Counts by Category')
plt.xlabel('Category')
plt.ylabel('Count')
plt.show()
# Scatter plot (if relevant)
plt.scatter(df['ColumnX'], df['ColumnY'])
plt.title('Scatter Plot of X vs Y')
plt.xlabel('ColumnX')
plt.ylabel('ColumnY')
plt.show()
# Correlation heatmap (optional)
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()

# Submission Requirements (.py file) containing:
 -Data loading and exploration steps.
 -Basic data analysis results.
 -Visualizations.
 -Any findings or observations.

## Task 1: Load and Explore the Dataset
 1.Choose a dataset in CSV format (for example, you can use datasets like the Iris dataset, a sales dataset, or any dataset of your choice).
 2.Load the dataset using pandas.
 3.Display the first few rows of the dataset using .head() to inspect the data.
 4.Explore the structure of the dataset by checking the data types and any missing values.
 5.Clean the dataset by either filling or dropping any missing values.
 # ANSWERS
# 1.load dataset using pandas
    import pandas as pd
  # Load the dataset
    df = pd.read_csv("iris.csv")
  # Display the first few rows
    print(df.head())
# 2.Explore the structure of the dataset
  # Check data types and general structure
    print(df.info())
  # Check for missing values
    print("\nMissing values in each column:")
    print(df.isnull().sum())
# 3. Clean the dataset (if needed)
  # Option 1: Drop rows with missing values (if any)
    df_cleaned = df.dropna()
  # Option 2 (alternative): Fill missing values with mean (if it makes sense)
  # df_cleaned = df.fillna(df.mean(numeric_only=True))
  # Confirm no missing values remain
    print("\nMissing values after cleaning:")
    print(df_cleaned.isnull().sum())


## Task 2: Basic Data Analysis
 1.Compute the basic statistics of the numerical columns (e.g., mean, median, standard deviation) using .describe().
 2.Perform groupings on a categorical column (for example, species, region, or department) and compute the mean of a numerical column for each group.
 3.Identify any patterns or interesting findings from your analysis.
 # ANSWERS
 ## Basic Data Analysis of the Iris Dataset
   # 1.Overall Statistics (.describe())
   
   Metric | Sepal Length | Sepal Width | Petal Length | Petal Width
   
      Mean | 5.84         | 3.05        | 3.76         | 1.20
     
    Median | 5.80         | 3.00        | 4.35         | 1.30
   
    Std Dev | 0.83         | 0.43        | 1.76         | 0.76
  
    Min/Max | 4.3 – 7.9    | 2.0 – 4.4   | 1.0 – 6.9    | 0.1 – 2.5
  
  # 2.Mean Values Grouped by Species
  
   Species | Sepal Length | Sepal Width | Petal Length | Petal Width
   
    Setosa | 5.01         | 3.42        | 1.46         | 0.24
    
  Versicolor | 5.94         | 2.77        | 4.26         | 1.33

   Virginica | 6.59         | 2.97        | 5.55         | 2.03
 
 ## TaskInteresting Findings
Setosa flowers have notably smaller petal length and width compared to the other two species — making them visually easy to separate.
Virginica has the largest overall measurements, especially in petal dimensions.
Sepal width shows less variability across species than petal features.
Petal measurements are key to distinguishing species — as evident in their grouped means and high standard deviations. 

## Task 3: Data Visualization
 1.Create at least four different types of visualizations:
    .Line chart showing trends over time (for example, a time-series of sales data).
    .Bar chart showing the comparison of a numerical value across categories (e.g., average petal length per species).
    .Histogram of a numerical column to understand its distribution.
    .Scatter plot to visualize the relationship between two numerical columns (e.g., sepal length vs. petal length).
 2.Customize your plots with titles, labels for axes, and legends where necessary.
 # ANSWERS
  # 1.Bar Chart – Average Petal Length per Species
     import matplotlib.pyplot as plt
     import seaborn as sns
  # Bar chart of average petal length by species
     plt.figure(figsize=(8, 5))
     sns.barplot(data=df, x='species', y='petal_length', palette='Set2')
     plt.title('Average Petal Length by Species')
     plt.xlabel('Species')
     plt.ylabel('Average Petal Length (cm)')
     plt.show()
  # 2.Histogram – Distribution of Sepal Width
    plt.figure(figsize=(8, 5))
    plt.hist(df['sepal_width'], bins=15, color='skyblue', edgecolor='black')
    plt.title('Distribution of Sepal Width')
    plt.xlabel('Sepal Width (cm)')
    plt.ylabel('Frequency')
    plt.grid(True)
    plt.show()
 # 3.Scatter Plot – Sepal Length vs Petal Length
    plt.figure(figsize=(8, 5))
    sns.scatterplot(data=df, x='sepal_length', y='petal_length', hue='species', palette='muted')
    plt.title('Sepal Length vs Petal Length')
    plt.xlabel('Sepal Length (cm)')
    plt.ylabel('Petal Length (cm)')
    plt.legend(title='Species')
    plt.show()
# 4.Line Chart (Simulated Trend for Petal Width) 
    plt.figure(figsize=(10, 5))
    plt.plot(df.index, df['petal_width'], label='Petal Width', color='purple')
    plt.title('Simulated Trend of Petal Width over Samples')
    plt.xlabel('Sample Index')
    plt.ylabel('Petal Width (cm)')
    plt.grid(True)
    plt.legend()
    plt.show()







