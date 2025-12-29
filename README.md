Data Analysis Practice Using Pandas (Tips & Employee Attrition)

This repository contains hands-on data analysis exercises using Python and Pandas.
The datasets are loaded directly from online CSV sources, and the exercises focus on data exploration, aggregation, filtering, and feature engineering.

🛠️ Tools & Libraries

Python

Pandas

Jupyter Notebook / VS Code

📁 Datasets Used

Tips Dataset (Seaborn)

https://raw.githubusercontent.com/mwaskom/seaborn-data/master/tips.csv


Employee Attrition Dataset

https://raw.githubusercontent.com/ybifoundation/Dataset/main/EmployeeAttrition.csv

✅ Practice Exercises – Question 1 (Tips Dataset)
🔹 Load Dataset
import pandas as pd

url = "https://raw.githubusercontent.com/mwaskom/seaborn-data/master/tips.csv"
tips = pd.read_csv(url)

1️⃣ Show First 10 Rows
tips.head(10)

2️⃣ Display Columns and Data Types
tips.info()

3️⃣ Average Tip Given Per Day
tips.groupby("day")["tip"].mean()

4️⃣ Maximum Tip Amount and Who Gave It
tips.loc[tips["tip"].idxmax()]

5️⃣ Add Tip_Percent Column
tips["Tip_Percent"] = (tips["tip"] / tips["total_bill"]) * 100

6️⃣ Rows Where Tip Percentage > 20
tips[tips["Tip_Percent"] > 20]

7️⃣ Average Total Bill by Gender
tips.groupby("sex")["total_bill"].mean()

✅ Practice Exercises – Question 2 (Employee Attrition Dataset)
🔹 Load Dataset
url = "https://raw.githubusercontent.com/ybifoundation/Dataset/main/EmployeeAttrition.csv"
emp = pd.read_csv(url)

1️⃣ First 8 Rows & Total Columns
emp.head(8)
emp.shape[1]

2️⃣ Employees in Each Department
emp["Department"].value_counts()

3️⃣ Average MonthlyIncome & YearsAtCompany
emp[["MonthlyIncome", "YearsAtCompany"]].mean()

4️⃣ Attrition = Yes and OverTime = Yes
emp[(emp["Attrition"] == "Yes") & (emp["OverTime"] == "Yes")]

5️⃣ Average MonthlyIncome by JobRole
emp.groupby("JobRole")["MonthlyIncome"].mean()

6️⃣ Max, Min, Average Age
emp["Age"].agg(["max", "min", "mean"])

7️⃣ EducationField with Highest Average Salary
emp.groupby("EducationField")["MonthlyIncome"].mean().idxmax()

8️⃣ MonthlyIncome > 15000 and PerformanceRating = 4
emp[(emp["MonthlyIncome"] > 15000) & (emp["PerformanceRating"] == 4)]

9️⃣ Add IncomeCategory Column
def income_category(income):
    if income < 5000:
        return "Low"
    elif income <= 10000:
        return "Medium"
    else:
        return "High"

emp["IncomeCategory"] = emp["MonthlyIncome"].apply(income_category)

🔟 Attrition Percentage by IncomeCategory
(emp[emp["Attrition"] == "Yes"]
 .groupby("IncomeCategory")
 .size() / emp.groupby("IncomeCategory").size() * 100)

1️⃣1️⃣ Count by Department & Gender
emp.groupby(["Department", "Gender"]).size()

1️⃣2️⃣ Top 10 Highest Paid Employees
emp.nlargest(10, "MonthlyIncome")

1️⃣3️⃣ Avg PerformanceRating & YearsAtCompany (OverTime = Yes)
emp[emp["OverTime"] == "Yes"][["PerformanceRating", "YearsAtCompany"]].mean()

🎯 Learning Outcomes

Load and explore real-world datasets

Perform grouping and aggregation

Filter data using multiple conditions

Create new derived columns

Analyze employee and customer behavior

👨‍💻 Author

Name: Faizan Bhat
Domain: Data Analysis / Python
Skills: Pandas, Data Cleaning, Data Analysis
