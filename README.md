# Behaviour-Analysis-on-Person-Phone-Usage-Data

  ![image](https://github.com/HammadHk1/Behaviour-Analysis-on-Person-Phone-Usage-Data/assets/117303560/81744abf-699b-48b2-a698-cdf29375c61c)


## Introduction
The code provided demonstrates how to combine and preprocess two datasets, `screen_df` and `app_usage_df`, and train a decision tree classifier to predict the app usage when the screen is unlocked. It involves steps such as data loading, filtering, concatenation, data transformation, encoding, splitting into training and testing sets, model training, evaluation, and prediction.
## Flow of the Code:
- Import the required libraries: pandas, sklearn.model_selection, sklearn.preprocessing, and sklearn.tree.
- Load the data from the CSV files data1 and data2 into two separate DataFrames: screen_df and app_usage_df.
- Filter the screen_df DataFrame to keep only rows where the "App name" column is equal to "Screen on (unlocked)". Create a new DataFrame called unlocked_screen_df containing the filtered data.
- Combine the unlocked_screen_df DataFrame and the app_usage_df DataFrame using pd.concat(), resulting in a new DataFrame called combined_df. This combines the data from both sources.
- Convert the `Date` and `Time` columns of combined_df to a datetime format using pd.to_datetime() and combine them into a new 'Timestamp' column.
- Sort the combined_df DataFrame by the `Timestamp` column to ensure the data is in chronological order.
- Calculate the time difference between consecutive rows using the diff() function on the 'Timestamp' column. Store the result in a new 'TimeDiff' column.
- Convert the 'TimeDiff' column to seconds by applying the dt.total_seconds() method on the 'TimeDiff' column.
- Encode the categorical variable 'App name' using LabelEncoder(). Create a new column 'AppLabel' in combined_df to store the encoded labels.
- Drop irrelevant columns such as `Date`, `Time`, `Duration`, and `Timestamp` from combined_df using the drop() function with the axis=1 parameter.
-Handle missing or null values by dropping rows with missing values using dropna() on combined_df.
- Split the data into training and testing sets using train_test_split(). Assign the input features to X (containing the `TimeDiff` column) and the target variable to y (containing the `AppLabel` column). Use a test size of 0.2 (20% of the data) and set a random state of 42 for reproducibility.
- Create an instance of the DecisionTreeClassifier and train the model using fit() with the training data (X_train and y_train).
- Evaluate the trained model's accuracy on the test set using score() with the testing data (X_test and y_test).
- Print the accuracy of the model.
- Predict the app usage when the screen is unlocked for a new data point represented by a DataFrame named new_data with a single value of 'TimeDiff'.
- Use the trained classifier (clf) to predict the app labels for new_data using predict().
- Decode the predicted app labels using the inverse_transform() method of the LabelEncoder, which converts the encoded labels back to their original app names.
- Print the predicted app labels and their corresponding app names.

## Note
It's assumed that the variables data1 and data2 contain valid data, and the code snippet provided is a continuation of a larger program or script.
