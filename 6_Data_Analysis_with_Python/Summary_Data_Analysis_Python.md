# Summary Data Analysis with Python- Summary
## Made by Pablo Nunes
----
- Why Data Analysis?
  - Data is everywhere
  - Data helps answer our questions from data
  - Helps us discover useful information
- Python Libraries
  - Pandas
  - NumPy
  - SciPy
  - Matplotlib
  - Seaborn
  - Scikit-learn
  - Statsmodels
- Import Data
  - Format/File Path
  - To import data in pandas do:
  ```python
  df = pd.read_csv(path, header = None) #If you want a header change this setting
  df.head(n) #Show the first n rows of the dataframe
  df.tail(n) #Show the last n rows of the dataframe
  df.columns = headers #Change the header
  df.to_csv(new_path) #Save the dataframe to another file in a new path
  ```
  - Pandas supports csv, json, Excel, sql.
- Exploring the data
  - In Pandas there are 4 basic data types
    - Object - String
    - Int64 - Integers
    - Float64 - Float
    - Datetime64 - Time Data
  - Exploring the variables to check if the types are correct.
  - Checking any inconsistencies, check with describe. Which returns a statistical summary.
  ```python
  df.describe() #Only int and float
  df.describe(include="all") #All variables including objects
  df.info() #Shows the types and quantities
  ```
- DB-API
  - It is how python uses APIs to acess Databases
  ```python  
  # Create a connection object
  conn = connect('DbName', 'user', 'pswd')

  # Create a cursor object
  cursor = conn.cursor()

  # Run queries
  cursor.execute('select * from my table')
  results = cursor.fetchall()

  # Free resources
  cursor.close()
  conn.close()
  ```
- Data Wrangling
  - Missing Value
    - Check the original source, try to recover the data
    - Drop the Variable or data entry
    - Replace with average of similar datapoints
    - Replace with frequency
    - Leave as missing data
  ```python
  df["Feature"].dropna() # Drop row (axis = 0) or column (axis=1)
  df["Feature"].replace(missing_value, new_value)
  ```
  - Data Formatting
    - Converting units
      - Pandas allow alows to change the units for use in dataframes
  ```python
  df["to_convert"] = fixed_const * df["to_convert"]
  
  ```
  - Change types
    - Sometimes the wrong datatype is used in variables
  ```python
  df["price"] = df["price"].astype("float")
  ```
  - Data Normalization
    - Simple Feature Scaling
    ```python
    df["to_normalize"] = df["to_normalize"]/df["to_normalize"].max()
    ```
    - Min-Max
    ```python
    diff = df["to_normalize"]/df["to_normalize"].min()
    min_max = df["to_normalize"].max()-df["to_normalize"].min()
    df["to_normalize"] = diff/min_max
    ```
    - Z-score
    ```python
    mean = df["to_normalize"]/df["to_normalize"].mean()
    std = df["to_normalize"].max()-df["to_normalize"].std()
    df["to_normalize"] = mean/std
    ```
  - One-hot enconding
    - Use the one-hot encoding to tranform categories in numerical values

- Exploratory Data Analysis
  - The main question of this step: *What are the characteristcs that have the most impact on the carm price?*
  - Descriptive Statistics
    - We use explore our data before using it. Using Descriptive Statistics helps us to understand it.
    - Using the describe function give us a summary for our dataset.
    ```python
    df.describe()
    ```
    - Using the Value Counts function give us a sum for our dataset.
    ```python
    count_data = df["to_count"].value_counts()
    count_data.rename(columns = {'to_count': 'value'}, inplce = True )
    count_data.index.name = 'Category'
    ```
    - Using Box Plots is easy to see the outliers.
    ```python 
    sns.boxplot(x="X", y="Y", data=df)
    ```
    - Scatter Box helps us the see the relation to two variables
    ```python
    plt.scatter(x,y)
    ```
  - GroupBy
    - Used on categorical variables
    - Single or multiple variables
    ```python
    df_test = df[['Category', 'Sub-category', 'Variable']]
    df_grp = df_test.groupby(['Category', 'Sub-category'], as_index = False).mean()
    df_grp
    ```
    - Pivot
    ```python
    df_pivot = df_grp.pivot(index='Category', columns='Sub-category')
    ```
    - Heatmap
    ```python
    plt.pcolor(df_pivot, cmap='RdBu')
    plt.colorbar()
    plt.show()
    ```
  - Correlation
    - Measures to what extent different vairables are independent
    - **Correlation doesn't imply causation.**
    - Using the Seaborn Linear Regression
    ```python
    sns.regplot()
    ```
    - Pearson Correlation
      - Measure the strength of the correlation between two features
      - It gives: **Correlation coeficient** and **P-value**
      - To Correlation coeficient:
        - Close to +1: Positive relationship
        - Close to 0: No relationship
        - Close to -1: Negative relationship
      - To P-value:
        - P-value < 0.001: Strong certainty in the result
        - P-value < 0.05: Moderate certainty in the result
        - P-value < 0.1: Weak certainty in the result
        - P-value > 0.1: No certainty in the result
      - Syntax:
      ```python
      pearson_coef, p_value = status.peasonr(df['Variable_1'], df['Variable_2'])
      ```
    - ANOVA - Analysis of Variance
      - Finding correlation between different groups of a categorical variable
      - ANOVA returns: 
        - F-test score
        - p-value
      - Large F-test imply in strong correlation and Small imply in a weak one. (Using the extremes and comparing categories)
      - Syntax:
      ```pyrhon
      anova_results = stats.f_oneway(grouped_anova.get_group("low_tier")["price"], grouped_anova.get_group("high_tier")["price"])```
