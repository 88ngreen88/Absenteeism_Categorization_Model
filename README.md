# Absenteeism_Categorization_Model

# Repo Structure

├── Data

├── .gitignore

├── Slides.pdf

├── Classification.ipynb

└── README.md

# Business Problem and Objective

Since the outset of the pandemic, chronic absenteeism has jumped from around 25% in 2020 to 41% in 2022 making it one of the largest and most significant problems public schools are currently facing. Chronic absenteeism is defined as a student missing 10% or more of the school days in a year. Studies have shown that students who are chronically absent have reduced reading proficiency in Elementary School and are less likely to graduate High School. With this in mind, I wanted to create a model that would be able to categorize and identify schools that are at most to suffer from high rates of chronic absenteeism. 

Some key questions that I was hoping my model would answer were as follows:

1. Would I be able to accurately categorize a school has having a high rate of chronic absenteeism?
2. What features/measures contribute the most to accurately categorizing a school has having a high rate of chronic absenteeism?
3. What other features should schools be measuring to improve my current model?

I started this modeling process by important python libraries for data processing, EDA, and modeling 


# Importing Data and Data Processing

After importing the python libraries, I started importing data sets that will eventually become my final dataframe. For each data set I decided to only use data from the 2020-2021 and 2021-2022 school years because I wanted to use data that was collected after the onset of the 2020 COVID-19 pandemic. I only wanted to use post COVID data because that is when Chronic Absenteeism really began to increase. The first data set that I imported was demographic data from the DOE which included key data on class size, race/ethnicity, poverty rates, and rates of students with disabilities


The second data set I decided to import was the DOE dataset on school attendance. For this data sets, I only included rows that had data for "all grades" because grade level data was already included in the df_demo. I also dropped unneccessary columns and dropped 's' values in the '% Chronically Absent' column. The s value is a place holder for schools that were too small to have their data displayed. 

# Combining Data

Now that I have my two main datasets I decided to combine the dataset together and begin to perfrom some Data EDA

Now that my two data sets are merged together, I wanted to look at the distribution of my target feature ('% Chronically Absent'). Looking at the histogram below, we can see that their is a large range of values for rate of chronic absenteeism in New York City Schools. This shows me that chronic absenteeism does not impact every school equally in New York City.

![download](https://user-images.githubusercontent.com/115309980/224388633-92a438a7-5625-4a34-aca9-215a2a74de8c.png)

The histogram above is a good start for visualizing my data, but I want to create a few more graphs in order to better understand my data. This will be a good time to get more information on our data frame. Looking at the information table of my data frame, it looks like we do not have any Null values. Good News!

I am also noticing that columns like # poverty and % poverty have a good chance of being multi-colinear. I need to explore this more through a heatmap.

In addition, feature values like '% chronically absent', '% poverty', and 'Economic Need Index' are all listed as object when they should be float data types.

# Combined Data EDA

In order to understand my data a bit better, I first want to see how chronic absenteeism has changed over time in NYC. Below I made a graph look at average rate of chronic absenteeism per year in nyc. Based on the graph below, we can see that Chronic absenteeism has really increased since the onset of the pandemic!

![download-7](https://user-images.githubusercontent.com/115309980/224388812-5fba2ab9-c25c-45ed-beff-d5a0cde634c3.png)

Now that we understanding when chronic absenteeism began to spike, we can drop rows that are in a year before 2020. Below I am dropping all rows that are not from the 2020-21 and 2021-22 school year. I am also changing the year from 2020-2021 to 2021 and 2021-22 to 2022.

Next I want to see how chronic absenteeism changes with race in NYC schools

![download-8](https://user-images.githubusercontent.com/115309980/224388999-9a3e2374-0db8-41f7-b625-64c9cfa33f6e.png)

Looking above, we can see that at the percentage of black and hispanic students increase at a school, so does the rate of chronic absenteeism. I also want to see have the rate of poverty at a school impacts absenteeism.

![download-9](https://user-images.githubusercontent.com/115309980/224389104-efe84153-49bf-477e-a5eb-f389a38c38f2.png)

Based on the graph above, we can also see that as the rate of poverty increases at a school, then the rate of absenteeism also increases.

![download-10](https://user-images.githubusercontent.com/115309980/224389268-9caa862c-3486-4d9d-b755-de3753a57905.png)

# Adding Additional Features/Measures to My DataSet

Before creating my first (Baseline) model, I am going to add a few more feature columns to my final data set. Specifically, I plan on adding data on the amount of indoor/outdoor space in NYC public schools, Survey Data from Parents and Teachers, and Guidance Counselor data. My hope is that these additional features will better help to better categorize my target feature.

# Creating My Models

Below I will use the X_train and y_train data to create mutliple categorizing models. I will assess these models based on teh recall score. I decided to use recall instead of precision or accuracy to assess my models because I feel like my stakeholder (the Department of Education) will want to the lowest number of false negatives possible. If recall is about the same, I will then look at precision to ensure that the number of false positives are also low.

In addition, I will need to use SMOTE and imblearn pipline in my categorization models because I have a class imbalance.

<img width="736" alt="Screenshot 2023-03-10 at 12 58 41 PM" src="https://user-images.githubusercontent.com/115309980/224389626-43a0d8de-6c9f-41e3-b5bf-5180110c0185.png">

Looking at the baseline model, the model is overall pretty good but there is a bit of over fitting because the accuracy train score is better than the accuracy test score. Next I will also look at decision tree and another logistic regression model where I used parameter tuning for both.

The logistic regression with parameter tuning has a recall score of 0.91, which is the same as the decision tree model. However, I feel like this model is better than the decision tree model because the accuracy and precision are higher for this model. As a result, I will use this model for my final model. 

# Finding Most Important Features

After creating my final model, I looked at the most important features in my model

![download-11](https://user-images.githubusercontent.com/115309980/224389908-07eff6d2-e8c7-4cb5-ac28-3448a027a376.png)

# Recommendations

Based on my model, I believe that the Department of Education should flag schools for high rates of absenteeism and provide additional funding to those schools for the following resources:

1. Additional guidance counselors and social works at the school

2. Additional staff that can lead small group instruction and independent projects for students who have fallen behind in reading and math during the pandemic

3. Further funds for field trips and community partnerships


# Next Steps
In order to improve my model I would want to scrape and find  data on the following:

1. Public transportation offered by each school.
2. Student employment
3. School Start Times
4. The number of tests given by a school
5. Suspension data

