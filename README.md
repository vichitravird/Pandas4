# Pandas4

## 1 Problem 1 : Nth Highest Salary (https://leetcode.com/problems/nth-highest-salary/solution/)
<br>

import pandas as pd

def nth_highest_salary(employee: pd.DataFrame, N: int) -> pd.DataFrame:
    
    dist = employee.drop_duplicates(subset='salary')
    dist['rnk'] = dist['salary'].rank(method='dense', ascending=False)
    ans = dist[dist.rnk == N][['salary']]
    if not len(ans):
        return pd.DataFrame({f'getNthHighestSalary({N})': [None]})
    ans = ans.rename(columns={'salary':f'getNthHighestSalary({N})'})
    return ans

## 2 Problem 2 : Second Highest Salary ( https://leetcode.com/problems/second-highest-salary/ )
<br>
import pandas as pd

def second_highest_salary(employee: pd.DataFrame) -> pd.DataFrame:
    df = employee.drop_duplicates(['salary'])
    if len(employee['salary'].unique())<2:
        return pd.DataFrame({"SecondHighestSalary":[np.NaN]})
    df = (df.sort_values(['salary']).tail(2).head(1).rename(columns = {'salary':'SecondHighestSalary'})).fillna('null')
    return df[['SecondHighestSalary']]
