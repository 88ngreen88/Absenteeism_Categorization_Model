# Exploring Chronic Absenteeism in New York's Public School System

# Business Problem and Objective

Since the onset of the 2020 COVID-19 pandemic, chronic absenteeism has jumped from around 25% in 2020 to 41% in 2022, making absenteeism one of most significant problems public schools are currently facing. Chronic absenteeism is defined as a student missing 10% or more of the school days in a year. Studies have shown that students who are chronically absent have reduced reading proficiency in Elementary School and are less likely to graduate High School. With this in mind, I wanted to create a model that would be able to categorize and identify schools that are likely to have high rates of chronic absenteeism. My hope is for the Department of Education to identify the key features from the categorization model and use these features to create interventions that help address the root causes of chronic absenteeism in schools.

Three questions that I hope my model can address are as follows:

1. With what level of accuracy can schools be categorized as having or not having a high rate of chronic absenteeism?
2. What features/measures contribute the most to accurately categorizing a school as having a high rate of chronic absenteeism?
3. What other features should schools measure in order to improve the current model?

I started this modeling process by importantubg python libraries for data processing, EDA, and categorization modeling.


# Importing Data and Data Processing

I began this project by importing data sets that will eventually become my final dataframe. For each data set I decided to only use data from the 2020-2021 and 2021-2022 school years because I wanted to use data that was collected after the onset of the 2020 COVID-19 pandemic. 

All the data was retrieved from the Open Data NYC or the DOE’s Website. I used features from the following data sets to create my final data frame:

1. DOE Demographic Data 
2. Attendance Data
3. Guidance Counselor and Social Worker school Data
4. Indoor/outdoor space in NYC public Schools
5. Graduation Rates 
6. Family Survey Data
7. Teacher Survey Data

# Visualizing Data

After combining all my data together, I wanted to look at the distribution of my target feature ('% Chronically Absent'). Looking at the histogram below, we can see that their is a large range of values for rate of chronic absenteeism in New York City Schools. This shows me that chronic absenteeism does not impact every school equally in New York City.

![download](https://user-images.githubusercontent.com/115309980/224388633-92a438a7-5625-4a34-aca9-215a2a74de8c.png)

In order to understand my data a bit better, I first want to see how chronic absenteeism has changed over time in NYC. Below I made a graph looking at average rate of chronic absenteeism per year in nyc. Based on the graph below, we can see that Chronic absenteeism has really increased since the onset of the pandemic!

![download-7](https://user-images.githubusercontent.com/115309980/224388812-5fba2ab9-c25c-45ed-beff-d5a0cde634c3.png)

Next I want to see how chronic absenteeism changes with race in NYC schools

![download-8](https://user-images.githubusercontent.com/115309980/224388999-9a3e2374-0db8-41f7-b625-64c9cfa33f6e.png)

Looking above, we can see that as the percentage of black and hispanic students increased at a school, so does the rate of chronic absenteeism. I also want to see how the rate of poverty at a school impacts absenteeism.

![download-9](https://user-images.githubusercontent.com/115309980/224389104-efe84153-49bf-477e-a5eb-f389a38c38f2.png)

Based on the graph above, we can see that as the rate of poverty increases at a school, the rate of absenteeism also increases.

![download-10](https://user-images.githubusercontent.com/115309980/224389268-9caa862c-3486-4d9d-b755-de3753a57905.png)


# Creating My Models

To start my modeling process, I split my data into a X_train, X_test, y_train and y_test. I will fit my data on the X and y train and then evaluate the model on the test data set.  When evaluating my model I decided to use the recall score. I decided to use recall instead of precision or accuracy to assess my models because I feel like my stakeholder (the Department of Education) will want to the lowest number of false negatives possible. A false positive in the context of this project would be if a school that had an issue with a high rate of chronic absenteeism was classified as not having a high rate of chronic absenteeism. If recall is about the same across models, I will then look at precision to decide on my best model.

In addition, because my target are schools in the top 25% of chronic absenteeism, I have created a class imbalance.

<img width="1026" alt="Screenshot 2023-03-10 at 2 05 04 PM" src="https://user-images.githubusercontent.com/115309980/224406847-1ddff789-96ec-4057-a6dd-237a6c30f64b.png">

I will need to use SMOTE and sk.imblearn pipline in all categorization models because I have this class imbalance.

Next, I created three models: A basline logistic model, a logist model using parameter tuning and a decision tree model using parameter tuning.

<img width="736" alt="Screenshot 2023-03-10 at 12 58 41 PM" src="https://user-images.githubusercontent.com/115309980/224389626-43a0d8de-6c9f-41e3-b5bf-5180110c0185.png">

Looking at the baseline model, the model is overall pretty good but there is a bit of over fitting because the accuracy train score is better than the accuracy test score. Next I will also look at decision tree and another logistic regression model.

The logistic regression with parameter tuning has a recall score of 0.91, which is the same as the decision tree model. However, I feel like this model is better than the decision tree model because the accuracy and precision are higher for the logistic regression model. As a result, I will use the logistic regression model with parameter tuning for my final model. 

# Finding The Most Important Features

After creating my final model, I looked at the most important features in my model

![download-11](https://user-images.githubusercontent.com/115309980/224389908-07eff6d2-e8c7-4cb5-ac28-3448a027a376.png)

Looking at the chart above, we can see that the most important features for categorizing a school as being at risk or not at risk for a high rate of absenteeism are as follows: Number of Counselors, Srong Core Instruction, Social-Emotional and Teacher Influence. These most important features can now be used to make recommendations to the Department of Education.


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


# Repo Structure
├── Clean Notebook.ipynb

├── Slides.pdf

├── .gitignore

├── gen_data folder

├── survey_data Folder

└── README.md

