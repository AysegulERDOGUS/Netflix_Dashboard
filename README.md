## Netflix Dashboard
This dashboard report is designed with a user-friendly interface that aims to provide insights into marketing strategies. 
While geographical distributions are visualised using cartograms, gender and country-based distributions are also presented in detail. 
Calculations created using DAX codes make the data more meaningful and functional.With different filtering options, users can customise the data according to their needs.

## Data Loading and Conversion Process
During the data loading process, columns containing multiple values were correctly parsed using SQL queries. This transformation allowed the data to be imported into the Power BI environment in a more structured and analyzable format, resulting in a clean and relational data model suitable for both modeling and reporting purposes.

You can reach the data cleaning process I did from here: https://github.com/AysegulERDOGUS/Data_Cleaning



## DAX Calculations Used

1) Classification of Age Groups

    Age Group = 

                SWITCH(
                    TRUE(),
                    N_Customers[age] >= 18 && N_Customers[age] < 30, "18-29",
                    N_Customers[age] >= 30 && N_Customers[age] < 45, "30-44",
                    N_Customers[age] >= 45 && N_Customers[age] < 60, "45-59",
                    N_Customers[age] >= 60, "60++",
                    "unknown"
                       )
2) Average Value Calculation

     Avg_Duration_Movie = 


                       CALCULATE( AVERAGE(Netflix[duration]), Netflix[type]="Movie")

     Avg_Season =


                       CALCULATE(AVERAGE(Netflix[duration]),Netflix[type]="TV Show")
