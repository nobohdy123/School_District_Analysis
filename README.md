# School District Analysis

- How does school budget and size relate to test scores?


## Overview

- I analyzed school passing percentages of students by school type (charter vs district), spending (per student), and student population (total student count).

- I discovered that less spending per student and smaller student population schools were typically charter schools, and these schools typically had much higher average overall passing percentage of students and higher average grades. 

- This covers 39,170 students across 15 schools. 

## Data

| File | Columns |
|------|---------|
| `Resources/schools_complete.csv` | School ID, school_name, type, size, budget |
| `Resources/students_complete.csv` | Student ID, student_name, gender, grade, school_name, reading_score, math_score |


## Tools & Libraries

- Python 3.14.8
- Pandas version 3.0.6

    - Note: Pandas 2.0 changed how .mean() handles non-numeric columns, so I select the columns before averaging, which is the more efficient pattern


## Approach

1. **Cleaned the data** (see `cleaning_student_names.ipynb` and `cleaning_data.ipynb`)
    - Removed prefixes (`Dr.`, `Mr.`) and suffixes (`MD`, `PhD`) from student names
    - Practiced filling missing grades on a small sample file
2. **Analyzed the data** (see `PyCitySchools.ipynb`)
    - Merged the school and student data
    - Calculated per-school budget per student, average scores, and passing rates
    - Grouped schools by spending, size, and type


## Key Findings

- Schools in the lowest spending group (under $586 per student) had an overall passing rate of **90%**, compared with **54%** in the highest group.

- Charter schools averaged **1,524 students** per school vs **3,854** in district schools.

- Charter schools had a much higher overall passing rate (**90.43%**) than district schools (**53.67%**).

- Passing rate tracks **school type** much more than spending. Charter and district schools with nearly the same per-student spending (for example Griffin at $625 and Bailey at $628) had overall passing rates of about 91% and 55%.

- Within each type, spending made little difference, and school size didn't either. The lowest-spending schools being charters is what creates the apparent link between lower spending and better results.

- This is an association, not proof of cause. All of the lowest-spending schools are charters, and all of the highest-spending schools are district schools.


## Limitations

- **Overlapping factors:** spending, school type and school size are tangled together (all of the lowest-spending schools are charters), so spending can't be separated from the other two.
- **Averages of averages:** group results are the mean of each school's percentage, so a 427-student school counts the same as one with 4,976.
- **Small sample:** 15 schools, so patterns are suggestive, not statistically significant.
- **Other factors not in the data:** I didn't have information on things like school security, bullying rates, athletics or local family income, which could also affect results.


## Future Work

- Analyze trends across grade levels.
- Analyze trends across gender.
- Cross analyze grade level and gender trends with each other and school type, spending.

    - Note: There are age ranges for each grade level, I.e. some younger and older students can be in 9th grade.


## How to Run

## How to Run

1. Clone the repository and open the folder:
```bash
   git clone https://github.com/FuegoSol/School_District_Analysis.git
   cd school_district_analysis
```
2. Install the requirements:
```bash
   pip install -r requirements.txt
```
3. Make sure the CSV files are in the `Resources/` folder.
4. Launch Jupyter and open `PyCitySchools.ipynb`:
```bash
   jupyter notebook
```


## Project Structure

```
├── PyCitySchools.ipynb
├── cleaning_data.ipynb
├── cleaning_student_names.ipynb
├── requirements.txt
├── README.md
└── Resources/
    ├── schools_complete.csv
    ├── students_complete.csv
    └── missing_grades.csv
```