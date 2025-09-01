# Pandas.py
import pandas as pd
import numpy as np
#series = pd.Series(range(1,11))
#print(series) 
#def factorial(n):
#  if n==0 or n==1:
#      return 1 
#  else:
#         return n*factorial(n-1)
# factorial = lambda n: 1 if n == 0 or n == 1 else n * factorial(n - 1)
# print((factorial(5)))
# def ncr(n,r):
#     return factorial(n)/(factorial(r)*factorial(n-r))
# print(ncr(8,4))
# my_dict = {
#     "grades": "A+", 
#     "name": "Nahin",
#     "marks": 80,
#     "subject": ["physics","mathematics","biology"]
# } 
# df = pd.DataFrame(my_dict)
# print(df)
# print(df.iloc[::])
data = {
    'Department': ['HR', 'Finance', 'IT', 'CSE', 'Marketing'],
    'Employee': ['Nahin', 'Ahan', 'Ahmed','Sabuz','Shamsuddin'],
    'Salary': [500000, 60000, 700000, 80000, 100000]
}
newdf = pd.DataFrame(data)
print(newdf.query('Salary > 60000'))
print(newdf.query('Salary > 60000 & Department == "IT"'))  
print(newdf.query('Salary > 60000 | Department == "IT"'))
pivot_df = newdf.pivot_table(index='Department', columns='Employee')
print(pivot_df)
print(newdf["Salary"])
df_dropped_row = newdf.drop([0,2])
print(df_dropped_row)
newdf["Country"]= ["Bangladesh", "Australia", "Usa", "Nz", "England"]
print(newdf)
newdf.iloc[3] = ['Pharmacy', 'XYZ', 80000, 'Finland']
print(newdf)
df_dropped_column = newdf.drop(["Salary"],axis=1)
print(df_dropped_column )
print(newdf['Department'])
print(newdf.head(2))
print(newdf.tail(2))
z=newdf.describe()
print(z)
print(newdf.columns)
print(newdf.dtypes)
print(z)

excel_file=newdf.to_excel("excel.xlsx",index=False)
print(excel_file) 
print(newdf.to_json("output.json"))
data= {
    'Name':["Nahin","Ahan","Sabuz",None],
    "Age" :[20,22,49,None],
     "Salary":[50000,60000,100000,None]
  }
print(data)
df1=pd.DataFrame(data)
print(df1.describe())
print(df1.drop(["Salary"],axis=1))
# drop_items=pd.dropna(df1)
# print(drop_items)
print(df1["Name"])
print(df1.fillna(0))
print(df1.isnull())

data ={'Age': [25, 30, 25, 35, 30, 40],
        'Salary':[50000, 60000, 55000, 70000, 65000, 80000]
}
df2 = pd.DataFrame(data)
print(df2.drop_duplicates())
grouped = df2.groupby(['Age']).mean()
print(pd.merge(newdf,df2))
# avg_salary = grouped['Salary'].mean()
print(grouped)
print(df2)
print(df2.head(2))
print(df2.tail(2))
print(df2.info())
# x=range(1,100,2)
# print(list(x))
# print([sum(x)])
# x = range(1, 100, 2)
# print([sum(x[:i]) for i in range(1, len(x) + 1)])
data1= pd.DataFrame({'A': [10, 20, 30], 'B': [5, 10, 15]})
print(data1)
print(data1.sum())
print(data1.sum(axis=1))
print(data1.sum(axis=0))
print(newdf.index)
rows=newdf.iloc[[0,1,2]]
print(rows)


print(newdf.query('Salary > 60000'))
print(newdf.query('Salary > 60000 & Department == "IT"'))
print(newdf.query('Salary > 60000 | Department == "IT"'))
print(newdf.describe())

data = {
    'Department': ['HR', 'Finance', 'IT', 'CSE', 'Marketing'],
    'Employee': ['Nahin', 'Ahan', 'Ahmed','Sabuz','Shamsuddin'],
}
newdf1 = pd.DataFrame(data)
print(newdf1)
print(type(newdf1))
print(newdf1.describe())
print(pd.merge(newdf,df2))
print(df2.drop_duplicates())
print(df2.head(2))
print(df2.tail(2))
print(df2.info())
print(df2.sum())


data= {
    'Name':["Nahin","Ahan","Sabuz",None],
    "Age" :[20,22,49,None],
     "Salary":[50000,60000,100000,None]
}
print(data)
df1=pd.DataFrame(data)
print(df1)
print(df1.to_excel("data.xlsx",index=False))
print(df1.to_csv("file.csv"))
print(df1.to_json("output.json"))

data ={'Age': [30, 35, 25, 40, 50, 25],
        'Salary':[50000, 60000, 55000, 70000, 65000, 80000]
}
df2 = pd.DataFrame(data)
print(df2.sort_values(by=['Age','Salary'],ascending=[True,True]))
print(df2.rename(columns={'Age': 'Years', 'Salary': 'Income'}))
print(df2.rename(index={0:"A", 1:'B',2:"C",3:"D",4:"E",5:"F"}))
print(df2.astype({'Age': 'float64', 'Salary': 'int64'}))
df2.loc[0,"Salary"] = 51000
print(df2)
df2.loc[0,"Salary"]
print(df2)
# df2['Zeros'] = [0 for i in range(len(df2))]
# print(df2)

# fx= lambda x: x**2


# df2['Squares'] = df2['Salary'].apply(fx)
# print(df2) 

# def function(a):
#     return a>5
# c=[1,2,3,4,5]
# print(list(filter((function,c))))

data = {
    'Category': ['Pineapple','Mango', 'Watermelon',
 'Cucumber','Letus-leaf'],
    'Price/kg': [140,100, 80, 50, 60],
    'Quantity/kg': [1,2,2,3,2],
}
print(len(data['Category']))
df = pd.DataFrame(data)

print(df.groupby('Category').count())  # Number of items
print(df.groupby('Category')['Price/kg'].min())    # Minimum price
print(df.groupby('Category')['Price/kg'].max())    # Maximum price

print(df.groupby('Category')['Price/kg'].sum())    # Total price
print(df.groupby('Category')['Price/kg'].mean())   # Average price
print(df.groupby('Category')['Price/kg'].std())    # Standard deviation
print(df.groupby('Category')['Price/kg'].agg(['min', 'max', 'mean']))  # Min, Max, Mean together
print(df.groupby('Category')['Price/kg'].var())    # Variance
print(df.groupby('Category')['Price/kg'].median()) # Median
print(df.groupby('Category')['Price/kg'].agg(['min', 'max', 'mean']))  # Min, Max, Mean together


data = {
    'Department': ['IT', 'IT', 'HR', 'HR', 'Finance'],
    'Employee': ['A', 'B', 'C', 'D', 'E'],
    'Salary': [60000, 65000, 40000, 42000, 50000],
    'Bonus': [2000, 2500, 1000, 1200, 1500]
}
df3= pd.DataFrame(data)
pivot = df3.pivot_table(index='Department', values=['Salary', 'Bonus'], aggfunc=['mean', 'sum'])
print(pivot)

d=[1,2,3,4,5,7]
q=[11,12,13,14,15,16]
df4=pd.DataFrame({0:d,1:q})
print(df4)
# print(pd.merge(df,df4), how='inner',on='Employee')
print(pd.read_csv("file.csv"))
print(pd.read_json("output.json"))
print(pd.read_excel("excel.xlsx"))
print(pd.concat([df3, df4], axis=1))
print(pd.concat([df3, df4], axis=0))
# df3.set_index(['Department', 'Employee'], inplace=True)

filtered_data=df3.query('Salary > 60000 & Department == "IT"')
print(filtered_data)



data = {
    'Date': ['2024-01-01', '2024-01-02', '2024-01-03', '2024-01-04'],
    'Temperature': [30, 31, np.nan, 33]
}
newdf1 = pd.DataFrame(data)

newdf1['Date'] = pd.to_datetime(newdf1['Date'])      # Step 1
newdf1.set_index('Date', inplace=True)           # Step 2
newdf1['Temperature'] = newdf1['Temperature'].interpolate()  # Step 3

print(newdf1)
print(pd.concat([df3, df4], axis=1))
print(pd.concat([df3, df4], axis=0))

df2.loc[0,"Salary"] = 51000
print(df2)
print(df2.loc[0:1])
x=df2["Salary"][1]
print(x)
import csv

# Data to be written to the CSV file
data_to_write = [
	['Name', 'Age', 'City'],
	['John Doe', '30', 'New York'],
	['Jane Smith', '25', 'London'],
	['Peter Jones', '42', 'Sydney']
]

# File path for the CSV file
csv_file_path = 'my_data.csv'

# Writing to a CSV file
try:
	with open(csv_file_path, 'w', newline='') as csvfile:
		csv_writer = csv.writer(csvfile)
		csv_writer.writerows(data_to_write)
	print(f"Successfully wrote data to {csv_file_path}")
except IOError as e:
	print(f"Error writing to file: {e}")

# Reading from a CSV file
try:
	with open(csv_file_path, 'r', newline='') as csvfile:
		csv_reader = csv.reader(csvfile)
		print(f"\nReading data from {csv_file_path}:")
		for row in csv_reader:
			print(', '.join(row))
except FileNotFoundError:
	print(f"Error: File not found at {csv_file_path}")
except IOError as e:
	print(f"Error reading file: {e}")
