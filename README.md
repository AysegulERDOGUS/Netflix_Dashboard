## Netflix Dashboard
This dashboard report is designed with a user-friendly interface that aims to provide insights into marketing strategies. 
While geographical distributions are visualised using cartograms, gender and country-based distributions are also presented in detail. 
Calculations created using DAX codes make the data more meaningful and functional.With different filtering options, users can customise the data according to their needs.

## Data Loading and Conversion Process
In this project, the data used in Power BI were not directly loaded, but primarily prepared and loaded with SQL queries. Especially in columns containing more than one value, some functions were used to separate and analyse the data. In this way, cleaner and more structured data sets were transferred to Power BI and reporting processes were carried out in a healthier way.


      SELECT *,
             TRIM(CountrySplit.value) AS Countries,
             TRIM(CastSplit.value) AS Casts,
             TRIM(List.value) AS List
      
      FROM Netflix_table
      CROSS APPLY STRING_SPLIT(country, ',') AS CountrySplit
      CROSS APPLY STRING_SPLIT(casts, ',') AS CastSplit
      CROSS APPLY STRING_SPLIT(listed_in,',') AS List


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
