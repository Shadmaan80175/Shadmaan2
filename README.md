# FUTURE_DS_03
![Capture py](https://github.com/user-attachments/assets/02908b72-1621-4e20-b20c-7d5782f2b16e)
![Capture py1](https://github.com/user-attachments/assets/fc4c487e-a906-4967-a024-d1f9d2400ce6)
![Capture py2](https://github.com/user-attachments/assets/1b1fe9b4-9518-4d66-b8fc-6cca6ff39725)
![Capture py3](https://github.com/user-attachments/assets/0d9eb814-e095-4253-8106-d4be8775412c)
![Capture py4](https://github.com/user-attachments/assets/2982e57c-cc47-4abc-863d-1d70816ad0d1)

Project Overview
This Python script is designed to perform a descriptive analysis of a simulated college event feedback dataset. The program covers the entire data science pipeline, from creating a sample dataset to data cleaning, analysis, and visualization. The final output provides key insights, such as the best-rated event, the most active department, and the most liked features of the events.

Key Components of the Script
1. Importing Libraries
The script begins by importing essential Python libraries for data manipulation and visualization.

pandas (pd): Used for creating and managing the DataFrame, which is the primary data structure for this project.

random: Used to generate random data for the simulated dataset, including student IDs, events, departments, and ratings.

matplotlib.pyplot (plt): A plotting library used for creating visualizations like bar charts and histograms.

seaborn (sns): A statistical data visualization library built on top of Matplotlib. It's used here for creating more aesthetically pleasing and informative plots.

textblob (TextBlob): A library for processing textual data. It's used specifically for performing sentiment analysis on the feedback comments.

2. Creating the Dataset
Instead of using a pre-existing CSV file, the script programmatically generates a simulated dataset of 100 student feedback entries. It defines lists of possible values for various columns, such as events, departments, and liked_features. A loop then iterates 100 times to create a row for each student, assigning random values for each field. The comment text is also generated based on the rating: a rating of 4 or 5 gets a "Great experience!" comment, while a rating of 1, 2, or 3 gets a "Needs improvement." comment. Finally, this generated data is compiled into a pandas DataFrame and saved as a college_event_feedback.csv file.

3. Data Cleaning
This section ensures the data is ready for analysis. The script performs two simple but crucial data cleaning steps:

Checking for Missing Values: It uses df.isnull().sum() to check for any null or missing values across all columns. Since the data is programmatically generated, there shouldn't be any, but this is a good practice to include in any data analysis workflow.

Removing Duplicates: It uses df.drop_duplicates(inplace=True) to remove any duplicate rows. This ensures that each feedback entry is unique and doesn't skew the analysis results.

4. Descriptive Analysis
This part of the script calculates key metrics from the cleaned data.

Average Rating per Event: It groups the data by Event_Name and calculates the mean of the Rating for each event. This helps identify the most popular or highly-rated events.

Department-wise Participation: It uses value_counts() on the Department column to count how many students from each department provided feedback. This identifies the departments with the highest participation.

Most Liked Features: This is a more complex step. The Liked_Features column contains a comma-separated string of features. The script uses .str.split(", ") to separate these strings into individual features and then .explode() to create a new row for each feature. Finally, it uses value_counts() to find the top 5 most frequently mentioned features.

5. Sentiment Analysis on Comments
This section adds a new dimension to the analysis by evaluating the emotional tone of the feedback comments.

get_sentiment function: A function is defined that takes a text string and uses TextBlob to return its sentiment.polarity. The polarity value is a float between -1.0 (very negative) and 1.0 (very positive).

Applying Sentiment Analysis: The df['Comments'].apply(get_sentiment) line applies this function to every comment in the DataFrame, creating a new Sentiment column. This allows you to quantify the overall sentiment of the feedback.

6. Visualization
The script creates several plots to visually represent the findings.

Average Rating per Event: A seaborn bar plot (sns.barplot) displays the average rating for each event. The rotation=45 argument for the x-axis labels (plt.xticks) prevents them from overlapping.

Department-wise Participation: A Matplotlib bar chart (.plot(kind='bar')) shows the count of participants from each department, making it easy to see which departments were most active.

Sentiment Distribution: A seaborn histogram (sns.histplot) visualizes the distribution of sentiment scores. This helps you understand whether the overall feedback is more positive or negative.

7. Insights
The final section consolidates the key findings and prints them in a clear, easy-to-read format. It uses f-strings to dynamically insert the calculated values.

Best-Rated Event: Prints the name and average rating of the event with the highest average rating, found using .idxmax().

Most Active Department: Prints the name and participant count of the department with the highest participation, also found using .idxmax().

Most Liked Feature: Prints the name of the most liked feature based on the top_features calculation from the descriptive analysis section.
