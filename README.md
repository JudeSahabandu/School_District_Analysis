# School_District_Analysis
---
Analysis of Funding and Student Test Results of the School District

## Review of School District Analysis Data

### Comments on data review

#### Cleaning the Data

The new_full_student_data.csv file has 19514 rows of student data pertaining to test scores. We come across 2 key data cleaning exercises which are to;

1. Remove rows of data with Nan data
2. Remove duplicated data

To remove rows of missing data the analysis used the `dropna` function, which resulted in 1,968 reading_score values and 982 math_score values. If we checked null values using the `.mean()` function, instead of the `.sum()` function, we would see that there was approximately 10% missing reading score values and 5% missing math_score values.

Furthermore, if we used the `.mean()` function to verify the duplicated rows data, we see we dropped approximately 10% of additional data as well.

Across the total cleaned data, we have removed close to 25% of our data sheet from 19514 to 14831 data rows. Given the significant amount of data loss, it is recommended to review the data collection phase to determine why we had to eliminate 1/4th of the data for our analysis.

#### Summarizing the Data

To get the general overview of the data set, we use summary statistics to determine key outputs for numerical data. We obtain summary statistics by using the following code;

```student_df.describe()```

Although, we can dive further into dataset summary statistics by looking at the summary statistics of grouped data to get meaningful comparisons of statistical overview across the groups. We can obtain summary statics for following group comparisons;

1. School Types

```school_type_df = student_df.loc[student_df["school_type"]== "Input school type options"]```

```school_type_df.describe()```

2. Grade

```student_grade_df = student_df.loc[student_df["grade"]== "Input grade options"]```

```student_grade_df.describe()```

3. School Name

```school_name_df = student_df.loc[student_df["school_name"]== "Input school name options"]```

```school_name_df.describe()```

The above will enable us to review how the school type, grade and school name impact the test scores of students.

#### Drilling Down and Comparing the Data

Considering the new_full_student_data.csv file, there are multiple cross analyses we can conduct to determine the performance of school types and school names. We can also look at grade based performances in addition to determining whether students are stronger in English or Math.

Like we use the following code to determine the average funding by school type;

```avg_school_budget_by_school_type = student_df.groupby(by='school_type').mean()```

```avg_school_budget_by_school_type.loc[:, ["school_budget"]]```

We can use the following code to determine the average student_count by school type to help determine the average funding per student across Public and Charter schools;

```student_count_df = student_df.rename(columns={"student_id":"Student Count"})```

```avg_student_count_by_school_type = student_count_df.groupby(by='school_type').mean()```

```avg_student_count_by_school_type.loc[:, ["student_count"]]```

The above output will help us determine the funding per student across Public and Charter school and we can do further analysis to help determine if different levels in funding has an impact on Reading and Math score outcomes.