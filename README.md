# Pandas4

## 1 Problem 1 : Nth Highest Salary (https://leetcode.com/problems/nth-highest-salary/solution/)
<br>
import pandas as pd

def nth_highest_salary(employee: pd.DataFrame, N: int) -> pd.DataFrame:
    df=employee['salary']
    df=pd.DataFrame(df)
    df=df.drop_duplicates()
    df=df.sort_values('salary', ascending=False).head(N).tail(1)
    return df[['salary']].rename(columns={'salary': f'getNthHighestSalary({N})'})

## 2 Problem 2 : Second Highest Salary ( https://leetcode.com/problems/second-highest-salary/ )
<br>
import pandas as pd

def second_highest_salary(employee: pd.DataFrame) -> pd.DataFrame:
    employee.drop_duplicates(subset=["salary"], inplace=True)
    if employee.shape[0] < 2 :
        return pd.DataFrame([[None]], columns=["SecondHighestSalary"])
    employee.sort_values(by="salary", inplace=True, ascending=False)
    employee = employee[["salary"]]
    employee.rename(columns={"salary" : "SecondHighestSalary"}, inplace=True)
    return employee.iloc[1:2]
