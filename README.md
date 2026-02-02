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

Output:

<img width="302" height="594" alt="Screenshot 2026-02-02 132821" src="https://github.com/user-attachments/assets/bc2a9062-47b3-4973-9644-026fd5cca358" />




