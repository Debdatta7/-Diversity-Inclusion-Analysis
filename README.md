# -Diversity-Inclusion-Analysis
Pwc Power BI Virtual Work - Task 3

### **Problem Statement :**
The purpose of this task is to:
* Define proper KPIs in hiring, promotion, performance and turnover
* Create a visualisation for the HR manager that reflects all relevant Key Performance indicators(KPIs) and metrics in the dataset.

Calculating the following measures could help to define proper KPIs:
* Number of men
* Number of women
* Number of leavers
* % employees promoted (FY21)
* % of women promoted
* % of hires men
* % of hires women
* % turnover

### **Datasource :**
Dataset used for this task was presented by Pwc 
* Dataset: Diversity and Inclusion

### **Data Preparation:**
Completed the Data transformation in Power Query and the dataset loaded into Microsoft Power BI Desktop for modelling.

Diversity and Inclusion dataset which has 500 rows and 31 Column of observation.

Data Cleaning for the dataset was done in the power query editor as follows:

* Changed the header row of dataset
* Replacing the value is New hire FY20? N converted No and Y converted Yes
* Replaced the value is In base group for turnover FY20 N converted No and Y converted Yes
* Replacing the value is Promotion in FY20? N converted No and Y converted Yes
* Removed Unnecessary columns
* Removed Unnecessary rows
* Each of the columns in the table were validated to have the correct data type

### **Data Analysis (DAX):**
Measures used in all visualisation are:

* #of leavers = CALCULATE(COUNTA('HR Manager'[Employee ID]), 'HR Manager'[Leaver FY] IN { "FY20" })

* #of men =Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Gender]="Male"))

* #of women = Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Gender]="Female"))

* % employees promoted (FY21) =Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Promotion in FY21?]="Yes")),Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[In base group for Promotion FY21]="Yes")))

* % of hires men = Divide('HR Manager'[# of men],('HR Manager'[# of men]+'HR Manager'[# of women]))

* % of hires women = Divide('HR Manager'[# of women],('HR Manager'[# of women]+'HR Manager'[# of men]))

* % Promotees who were men = Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Gender]="Male")),distinctcount('HR Manager'[Employee ID]))

* % Promotees who were women = Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Gender]="Female")),distinctcount('HR Manager'[Employee ID]))


* % Turnover = Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[FY20 leaver?]="Yes")),Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[In base group for turnover FY20]="Y"))+Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager',NOT('HR Manager'[Department @01.07.2020]=BLANK()))),2))

### **Insights:**
As shown the data Visualisation, It can be deduced that:

* 41 % Female hires of the year and 59 % Male hires of the year.
* 53.8% of promotions were Female in the Junior Officer category, the highest for the year.
* 47% of promotions were Male in the Junior Officer category, the lowest for the year.
* Director is the highest Average time of job level promoted in this year.
* Finance department 22% highest turnover of the year.
* Employees promoted in the year of 2021 are 54.34% Male and 45.66% Female.
* The most common age group is 20-29 having 223 employees fall in this category.
