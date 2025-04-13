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
