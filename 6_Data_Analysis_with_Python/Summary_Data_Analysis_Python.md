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
    - Use the one-hot encoding to transform categories in numerical values

    ```python
    s = pd.Series(list('abca')) # Creates a series in Pandas
    pd.get_dummies(s) # Creates the encoder
    ```

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

      ```python
      anova_results = stats.f_oneway(grouped_anova.get_group("low_tier")["price"], grouped_anova.get_group("high_tier")["price"])
      ```

- Model Development
  - A model can be thought of as a mathematical equation used to predict a value given one or other values.
  - Relating independent variables to dependent ones
  - Linear Regression and Multiple Linear Regression
    - Linear Regression refers to independent Variables to make a prediction
    - We use some data to fit the model and other part to test the fit
    - The function for a simple linear regression is: Y = b0 + b1*x
    - Using sklearn to fit a simple linear regression, we have:
  
    ```python
    from sklearn.linear_model import LinearRegression 

    lm=LinearRegression() # Using the Linear Regression function from SkLearn to train
    X = df[['Independent_variable']] # Picking the X, for the inpendendent variable 
    Y = df[['result']] # Picking the Y

    lm.fit(X,Y) # Fitting the X to Y, using the SkLearn function

    y_hat = lm.predict(X) # Using the model to have a prediction

    ```

    - Using sklearn to train a multiple linear regression:
    ```python
    from sklearn.linear_model import LinearRegression 

    lm = LinearRegression() # Using the Linear Regression function from SkLearn to train
    X = df[['Independent_variable_1','Independent_variable_2','Independent_variable_3','Independent_variable_4']] # Picking the Xs, for the inpendendent variables
    Y = df[['result']] # Picking the Y

    lm.fit(X,Y) # Fitting the X to Y, using the SkLearn function

    y_hat = lm.predict(X) # Using the model to have a prediction

    ```

  - Model Evaluation Using Visualization
    -  Regression Plot
       -  Shows the relationship between two variables
       -  Strength of correlation
       -  Direction of relationship
       -  Uses the combination of Scatterplot and the fitted linear regression
       -  Plotting the regression plot

        ```python
        import seaborn as sns

        sns.regplot(x = "independent_variable", y = "result", data = df) # Using the seaborn library to plot the regression plot
        plt.ylim(0,) # Showing the plot

        ```

      - Residual Plot
        - Represents the error bwtween the actual value and the real value
        - Any patterns shown here are a sign of errors while modeling the prediction (Like a curvature)
        - Plotting:

         ```python
        import seaborn as sns

        sns.residplot(df["independent_variable"], df["result"]) # Using the seaborn library to plot the residual plot

        ```

      - Distribution Plots
        - Shows the distribution under a area of the variable and the result
        - Helps us to see the real values vs the predicted ones for the model and inacurracies

        ```python
        import seaborn as sns

        value_axis = sns.displot(df["result"], hist = "False", color = "r", label = "Actual Value") # Using the seaborn library to make the first the distribution plot
        sns.displot(Yhat, hist = "False", color = "b", label = "Predicted Values", ax = value_axis) # Using the seaborn library to make the distribution plot 

        ```

   - Polynomial Regression and Pipelines
     - The relations between variables and results can be in polynomial order
     - Using the ```np.polyfit``` we can use polynomial regression
     - Using scikit learn:

     ````python
     from sklearn.preprocessing import PolynomialFeatures

     pr = PolynomialFeatures (degree = 2) # Set the second order for our model
     pr.fit_transform([1,2], include_bias = False) # Transformed version of our features
     ````

     - Pre-Processing
       - Normalize features simultaneously
       - Scikit learn:

       ````python
        from sklearn.preprocessing import StandardScaler

        Scale = StandardScaler() # Make the object
        Scale.fit(x_data[['Feature_1','Feature_2']]) # Fit the data
        x_scale = Scale.transform(x_data[['Feature_1','Feature_2']])) # Transform the data into a new dataframe
       ````

    - Pipeline
      - Pipelines sequentially transform a series of transformations. The last step carries a prediction.
      - In scikit Learn:
      ````python
      # Importing all the libraries
      from sklearn.preprocessing import PolynomialFeatures
      from sklearn.linear_model import LinearRegression
      from sklearn.preprocessing import StandardScaler
      from sklearn.pipeline import Pipeline

      # Creating a list of tuples, the first element has the name of the element, the second has a model constructor
      Input = [('scale', StandardScaler(), ('polynomial', PolynomialFeatures(degree = 2),  ('mode', LinearRegression()))]

      # Inputing this in a pipeline constructor
      pipe = Pipeline(Input)

      # Training the Pipeline
      pipe.fit(df[['Feature_1', 'Feature_2', 'Feature_3']], y)

      # Prediction
      y_hat = pipe.predict(X[['Feature_1', 'Feature_2', 'Feature_3']])
      ````


  - Measures for In-Sample Evaluation
    - A way to numerically determine how good the model fits on the dataset
    - Two important measures to determine the fit are:
      - Mean Squared Error (MSE)
      - R-Squared (R²)
    - Mean Squared Error: Take the squared of the diference of prediction and realily, sum all, and divide by the number of samples.

    ```python
    from sklearn.metrics import mean_squared_error

    mean_squared_error(df["price"], Y_predict_simple_fit) # Using the Scikit Learn function to MSE
    ```
    - R-Squared (R²)
      - Coefficient of Determination
      - How close is the data to the fitted line in percentage
      - Uses a formula: MSE of Regression Line / MSE of the average

      ```python
      X = df[['Independent_variable_1','Independent_variable_2','Independent_variable_3','Independent_variable_4']] # Picking the Xs, for the inpendendent variables
      Y = df[['result']] # Picking the Y

      lm.fit(X,Y) # Fitting the X to Y, using the SkLearn function

      lm.score(X,y) # Testing the R²
      ```
  - Decision Making and Predictions
    - Decision Making
      - Do the Predicted Values make sense?
      - Visualization
      - Numerical measures for evaluation
      - Comparing Models
