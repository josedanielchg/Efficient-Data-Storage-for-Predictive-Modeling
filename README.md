# Efficient Data Storage for Predictive Modeling

This project, part of the *Associate Data Scientist in Python* from DataCamp Carerer Track, involves optimizing the storage of a dataset from *Training Data Ltd.*, a leading online data science training provider. The goal is to preprocess and transform the dataset into an efficient format to facilitate faster and more scalable machine learning model development.

## Project Description

Large datasets can significantly slow down machine learning pipelines. In this project, the dataset `customer_train.csv` is optimized for efficient storage by converting data types and filtering relevant data. The processed dataset will eventually be used to predict whether students are seeking new job opportunities, aiding recruiters in targeting potential candidates.

## Dataset Overview

The dataset contains anonymized student information and includes the following columns:

| Column                   | Description                                                                      |
|--------------------------|----------------------------------------------------------------------------------|
| `student_id`             | A unique ID for each student.                                                   |
| `city`                   | A code for the city the student lives in.                                       |
| `city_development_index` | A scaled development index for the city.                                        |
| `gender`                 | The student's gender.                                                           |
| `relevant_experience`    | Indicates if the student has relevant work experience.                          |
| `enrolled_university`    | The type of university course enrolled in (if any).                             |
| `education_level`        | The student's education level.                                                  |
| `major_discipline`       | The educational discipline of the student.                                      |
| `experience`             | The student's total work experience (in years).                                 |
| `company_size`           | The size of the student's current employer.                                     |
| `company_type`           | The type of company employing the student.                                      |
| `last_new_job`           | The number of years between the student's current and previous jobs.            |
| `training_hours`         | The number of hours of training completed.                                      |
| `job_change`             | Indicates if the student is looking for a new job (`1` = Yes, `0` = No).        |

## Project Objectives

1. **Optimize Data Types**:
   - Convert columns with two-factor categories into Booleans.
   - Convert integer columns to 32-bit integers for memory efficiency.
   - Convert floating-point columns to 16-bit floats.
   - Convert nominal categorical data to the `category` type.
   - Convert ordinal categorical data to ordered categories based on natural order.

2. **Filter Relevant Data**:
   - Retain only students with 10+ years of experience at companies with at least 1,000 employees.

3. **Assess Memory Usage**:
   - Compare memory usage of the original and transformed DataFrames using `.info()` and `.memory_usage()` methods.

## Results

The preprocessing steps applied to the dataset resulted in significant memory optimization, even before filtering by experience and company size. Below is a comparison of memory usage for each column before and after transformation:

| Column Name            | Records Count | Original Dtype | Original Memory (bytes) | Transformed Dtype | Transformed Memory (bytes) | Memory Reduction (%) |
|-------------------------|---------------|----------------|--------------------------|--------------------|----------------------------|-----------------------|
| `student_id`           | 19,158        | int64          | 153,264                  | int32              | 76,632                     | **50.00**                |
| `city`                 | 19,158        | object         | 1,235,888                | category           | 31,246                     | **97.47**                |
| `city_development_index` | 19,158      | float64        | 153,264                  | float16            | 38,316                     | **75.00**                |
| `gender`               | 19,158        | object         | 1,040,573                | category           | 19,452                     | **98.13**                |
| `relevant_experience`  | 19,158        | object         | 1,527,274                | bool               | 19,158                     | **98.75**                |
| `enrolled_university`  | 19,158        | object         | 1,341,257                | category           | 19,482                     | **98.55**                |
| `education_level`      | 19,158        | object         | 1,231,558                | category           | 19,658                     | **98.40**                |
| `major_discipline`     | 19,158        | object         | 1,095,945                | category           | 19,718                     | **98.20**                |
| `experience`           | 19,158        | object         | 1,121,964                | category           | 21,004                     | **98.13**                |
| `company_size`         | 19,158        | object         | 1,023,519                | category           | 19,965                     | **98.05**                |
| `company_type`         | 19,158        | object         | 1,047,279                | category           | 19,733                     | **98.12**                |
| `last_new_job`         | 19,158        | object         | 1,113,264                | category           | 19,683                     | **98.23**                |
| `training_hours`       | 19,158        | int64          | 153,264                  | int32              | 76,632                     | **50.00**                |
| `job_change`           | 19,158        | float64        | 153,264                  | bool               | 19,158                     | **87.50**                |

### Key Observations:
- **Overall Memory Reduction**: Many columns achieved memory savings of over 90% due to dtype transformations, particularly the conversion of object columns to categories and reducing numeric precision (e.g., float64 to float16 and int64 to int32).
- **Most Significant Savings**: 
  - `gender`: 98.13% memory reduction.
  - `relevant_experience`: 98.75% memory reduction.
  - `enrolled_university`: 98.55% memory reduction.
- **Categorical Conversions**: Transforming columns with nominal and ordinal data into categories drastically reduced memory usage, particularly for high-cardinality columns like `city`.

These transformations demonstrate the power of efficient data storage techniques, preparing the dataset for more complex filtering and analysis steps while ensuring significant resource savings.


## Requirements

- Python 3.x
- pandas library

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/josedanielchg/Efficient-Data-Storage-for-Predictive-Modeling.git
   ```

2. **Navigate to the project directory**:
   ```bash
   cd Efficient-Data-Storage-for-Predictive-Modeling
   ```

3. **Install required dependencies**:
   ```bash
   pip install pandas
   ```

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request for improvements or new features.

## License

This project is licensed under the MIT License.