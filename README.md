# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Importing essential libraries for data handling, visualization, and clustering. 

2.Load the customer dataset into a pandas DataFrame.
   
3.Preview the dataset.
  
4.Use only the relevant numerical features: Annual Income and Spending Score.
   
5.Calculate WCSS (Within-Cluster Sum of Squares) for different cluster counts.

6.Plot the results to visually determine the "elbow point" where adding more clusters doesn’t significantly reduce WCSS.

7.Train the KMeans model with n_clusters=5.

8.Predict cluster labels for each customer.

9.Assign each data point to its respective cluster.

10.Use a scatter plot to visualize how customers are grouped based on Annual Income and Spending Score.


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Swetha S
RegisterNumber:212224040344
*/
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
print("Name: Swetha S\n Reg.no: 212224040344")
data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss=[]

for i in range(1,11):
    kmeans=KMeans(n_clusters=i,init="k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("NO. of. clusters")
plt.ylabel("wcss")
plt.title("Elbow method")

km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred

data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img width="558" height="278" alt="Screenshot 2025-10-14 103912" src="https://github.com/user-attachments/assets/bbfbf6c0-e010-4445-a0ba-fab864ab8d3b" />

<img width="401" height="155" alt="Screenshot 2025-10-14 103925" src="https://github.com/user-attachments/assets/fa43d1b4-a8e8-4064-afe4-0648f037c3fa" />

<img width="880" height="601" alt="Screenshot 2025-10-14 103939" src="https://github.com/user-attachments/assets/9e471aad-642f-4bf5-8a9f-ed7bdcc1a509" />


<img width="815" height="231" alt="Screenshot 2025-10-14 103947" src="https://github.com/user-attachments/assets/e8915851-f51d-4352-a624-0eed07aafcec" />


<img width="819" height="587" alt="Screenshot 2025-10-14 103957" src="https://github.com/user-attachments/assets/35171a18-7784-4b63-ac77-b98199cf5374" />



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
