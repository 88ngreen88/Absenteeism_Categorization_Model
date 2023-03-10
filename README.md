# Absenteeism_Categorization_Model

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
