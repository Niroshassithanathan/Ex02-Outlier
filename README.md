# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

Aim:

TO detect and remove the outliers in the given data set and save the final data.

Algorithm:

Step 1

Import the required packages(pandas,numpy,scipy)

Step 2

Read the given csv file

Step 3

Convert the file into a dataframe and get information of the data.

Step 4

Remove the non numerical data columns using drop() method.

Step 5

Detect the outliers in the data set using z scores method.

Step 6

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

Step 7

Check if the outliersare removed from data set using graphical methods.

Step 8

Save the final data set into the file.

Program:

1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
Program developed by : R.brindha Register number : 21222230023
~~~py
import pandas as pd 
import numpy as np 
import seaborn as sns

df = pd.read_csv("/content/bhp.csv") df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25) 
q3 = df['price_per_sqft'].quantile(0.75) 
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5*IQR ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))] 
df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)
~~~

(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
~~~py
from scipy import stats 
z = np.abs(stats.zscore(df['price_per_sqft'])) 
df2 = df[(z<3)] 
df2
print(df2.shape) 

sns.boxplot(x="price_per_sqft",data=df2)
~~~

(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
~~~py
df3 = pd.read_csv("height_weight.csv") df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape

sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25) 
q3 = df3['weight'].quantile(0.75) 
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5*IQR ll = q1-1.5*IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))] 
df4

df4.shape

sns.boxplot(x="weight",data=df4)
~~~

(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
~~~py
sns.boxplot(x="height",data=df3) 
q1 = df3['height'].quantile(0.25) 
q3 = df3['height'].quantile(0.75) 
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5*IQR ll = q1-1.5*IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))] 
df5

df5.shape

sns.boxplot(x="height",data=df5)
~~~

Output:

(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

Dataset:

![a1](https://user-images.githubusercontent.com/121418437/227312355-8ebbdc60-a134-46d6-94b4-061f9848e900.PNG)

Dataset Head :

![a2](https://user-images.githubusercontent.com/121418437/227312742-34f70b8d-1dd2-43f4-871c-4a3632288973.PNG)

Dataset Info :

![a3](https://user-images.githubusercontent.com/121418437/227313083-2f89fb6d-3119-4a1b-b977-698ea681e5e3.PNG)

Dataset Describe:

![a4](https://user-images.githubusercontent.com/121418437/227313294-133d1e7c-4eef-4d0b-a3e4-41438e73d740.PNG)

Null Values:

![a5](https://user-images.githubusercontent.com/121418437/227313434-59896e04-9f8a-4090-a0f9-f28c179b2e8c.PNG)

Dataset Shape:

![a6](https://user-images.githubusercontent.com/121418437/227313725-11768a41-3694-4c4f-b79c-d54c1103f433.PNG)

Box plot of price_per_sqft column with outliers:

![a7](https://user-images.githubusercontent.com/121418437/227313885-40cd220d-9c0c-4007-b8c9-eb677a3b058e.PNG)

price_per_sqft - Dataset after removing outliers:

![a8](https://user-images.githubusercontent.com/121418437/227314147-32468d60-1fcd-4e4e-80f4-7bba031c1c76.PNG)

price_per_sqft - Shape of Dataset after removing outliers :

![a9](https://user-images.githubusercontent.com/121418437/227314348-f3bac8b2-3c65-4f6f-9c9a-13f44d73017a.PNG)

Box Plot of price_per_sqft column without outliers:

![a10](https://user-images.githubusercontent.com/121418437/227315350-0d2fd3d3-ad61-406d-9eef-7625305a7131.PNG)

(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.
Dataset after removal of outlier using z score:

![a11](https://user-images.githubusercontent.com/121418437/227315754-e63b54b9-5b3d-4450-8401-d025ce7708e8.PNG)

Shape of Dataset after removal of outlier using z score:

![a11](https://user-images.githubusercontent.com/121418437/227316893-d7faecf4-c19d-454b-9cbf-1984cba7fb70.PNG)
![a12](https://user-images.githubusercontent.com/121418437/227316940-08dfc622-c4e1-4db7-af11-2726d850691e.PNG)

(4) For the data set height_weight.csv detect weight and height outliers using IQR method:
Dataset Head:

![a13](https://user-images.githubusercontent.com/121418437/227317167-f7943b27-d79c-403b-b22e-36eff94312c4.PNG)

Dataset Info:

![a14](https://user-images.githubusercontent.com/121418437/227317521-ee5e3989-5a8d-41b3-b89d-2fb2794b18f2.PNG)

Dataset Describe:

![a15](https://user-images.githubusercontent.com/121418437/227317658-099183f5-0529-4820-86cd-a80ff2807321.PNG)

Null Values:

![a16](https://user-images.githubusercontent.com/121418437/227317949-8373da84-48ec-497b-8002-ffb08d2cb5e6.PNG)

Dataset Shape:

![a17](https://user-images.githubusercontent.com/121418437/227318022-0e4f1987-1127-4212-9192-9d9b9fac9c22.PNG)

Weight - With outliers:

![a18](https://user-images.githubusercontent.com/121418437/227318099-f196edca-4cef-4ebd-a8b5-1f0d41002b2f.PNG)

Weight - Dataset after removing Outliers using IQR method:

![a20](https://user-images.githubusercontent.com/121418437/227318607-16c44bcc-1fc1-43dd-a81b-5f9580f24db6.PNG)

Weight - Shape of Dataset after removing Outliers using IQR method:

![a21](https://user-images.githubusercontent.com/121418437/227318893-4facc9f5-ba42-4ccc-94cb-285e5250d93a.PNG)

Weight - Without Outliers using IQR method:

![a22](https://user-images.githubusercontent.com/121418437/227319063-fb65ed7b-e0d6-4945-8b04-022912d74803.PNG)

Height - With outliers:

![a23](https://user-images.githubusercontent.com/121418437/227319237-7ebf288f-6228-41b3-9ac7-f9fb35489ccc.PNG)

Height - Dataset after removing Outliers using IQR method:

![a24](https://user-images.githubusercontent.com/121418437/227319349-64a9bf3f-992e-4791-bfc7-001351b6cede.PNG)

Height - Shape of Dataset after removing Outliers using IQR method:

![a25](https://user-images.githubusercontent.com/121418437/227319810-d3cff45d-8791-401c-8f78-c437d5ba19db.PNG)

Height - Without Outliers using IQR method:

![a26](https://user-images.githubusercontent.com/121418437/227319881-42415eb6-8029-4ee7-bd80-27315bee1d9f.PNG)

Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.




