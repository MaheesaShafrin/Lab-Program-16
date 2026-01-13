# Lab-Program-16
EXERCISES TO VISUALIZE THE DATA USING SCATTER PLOT AND HEAT MAP.
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns


np.random.seed(0)


x = np.random.rand(100) * 10 
y = np.random.rand(100) * 10  

heatmap_data = np.random.rand(10, 10)

plt.figure(figsize=(12, 6)) 

plt.subplot(1, 2, 1) 
plt.scatter(x, y, color='blue', alpha=0.7)
plt.title("Scatter Plot")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")


plt.subplot(1, 2, 2)  
sns.heatmap(heatmap_data, annot=True, cmap='coolwarm', cbar=True)
plt.title("Heatmap")


plt.tight_layout()  
plt.show()








import sqlite3


conn = sqlite3.connect('my_database.db')

cursor = conn.cursor()


cursor.execute("CREATE TABLE IF NOT EXISTS employees (id INTEGER PRIMARY KEY, name TEXT, salary REAL)")
cursor.execute("INSERT INTO employees (name, salary) VALUES ('Jane Smith', 25000.00)")
cursor.execute("INSERT INTO employees (name, salary) VALUES ('John Doe', 70000.00)")
cursor.execute("INSERT INTO employees (name, salary) VALUES ('Jane Smith', 80000.00)")
cursor.execute("INSERT INTO employees (name, salary) VALUES ('Priya Smith', 10000.00)")
conn.commit() 
employee_name = 'John Doe'
update_query = """
UPDATE employees
SET salary = ?
WHERE name = ?
"""
cursor.execute(update_query, (new_salary, employee_name))


update_multiple_cols_query = """
UPDATE employees
SET salary = ?, name = ?
WHERE name = ?
"""
cursor.execute(update_multiple_cols_query, (90000.00, 'John J. Doe', 'John Doe'))


update_all_query = """
UPDATE employees
SET salary = salary * 1.1
"""

cursor.execute("UPDATE employees SET salary = salary * 1.05 WHERE salary < ?", (80000,))


conn.commit()


print("Updated employee data:")
for row in cursor.execute("SELECT * FROM employees"):
    print(row)
    conn.close()

Output:
Updated employee data:
(1, 'Jane Smith', 27562.5)
(2, 'John J. Doe', 90000.0)
(3, 'Jane Smith', 80000.0)
(4, 'Priya Smith', 11025.0)
(5, 'Jane Smith', 26250.0)
(6, 'John J. Doe', 90000.0)
(7, 'Jane Smith', 80000.0)
(8, 'Priya Smith', 10500.0)

