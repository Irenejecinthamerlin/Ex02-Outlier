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
Program developed by : R.Irene Jecintha Merlin

Register number : 21222104008

import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/bhp.csv")

df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)

q3 = df['price_per_sqft'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]

df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)
(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))

df2 = df[(z<3)]

df2

print(df2.shape)

sns.boxplot(x="price_per_sqft",data=df2)
(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/height_weight - Sheet1.csv")

df

df.head()

df.info()

df.describe()

df.isnull().sum()

df.shape

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['weight']>=ll)&(df['weight']<=ul))]

df1

df1.shape

sns.boxplot(x="weight",data=df1)
(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
sns.boxplot(x="height",data=df)

q1 = df['height'].quantile(0.25)

q3 = df['height'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df2 =df[((df['height']>=ll)&(df['height']<=ul))]

df2

df2.shape

sns.boxplot(x="height",data=df2)
## Output:
(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
## Dataset:
### ![image](https://user-images.githubusercontent.com/128350225/227582942-e87c2fb0-152b-4279-97c2-2dc2620123a2.png)
## Dataset Head :
### ![image](https://user-images.githubusercontent.com/128350225/227583070-97960c84-d7d4-4034-8163-b5992dfdbabf.png)
## Dataset Info :
### ![image](https://user-images.githubusercontent.com/128350225/227583228-4b1780f6-e06f-44d1-b085-353d7b3bb1de.png)
## Dataset Describe:
### ![image](https://user-images.githubusercontent.com/128350225/227583321-fe65a08c-31c5-477d-a404-d4985d03dd22.png)
## Null Values:
### ![image](https://user-images.githubusercontent.com/128350225/227583436-06b9cb28-6908-4a6f-88c5-94dd8051060f.png)
## Dataset Shape:
### ![image](https://user-images.githubusercontent.com/128350225/227583667-1d23eb30-d12e-4969-9ae4-ea53fcfbb35e.png)
## Box plot of price_per_sqft column with outliers:
### ![image](https://user-images.githubusercontent.com/128350225/227583881-c8afc5bb-a9a5-475c-a813-a0546d00db02.png)
## price_per_sqft - Dataset after removing outliers:
### ![image](https://user-images.githubusercontent.com/128350225/227584844-04802e8a-0ce9-45e3-a8ca-d629e298b979.png)
## price_per_sqft - Shape of Dataset after removing outliers :
### ![image](https://user-images.githubusercontent.com/128350225/227584959-f82cb780-e269-4e8b-aaed-0730bbba5ab2.png)
## Box Plot of price_per_sqft column without outliers:
### ![image](https://user-images.githubusercontent.com/128350225/227585103-87c48bdd-697e-4e04-ab9a-ee8cd4e09064.png)
(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.
## Dataset after removal of outlier using z score:
### ![image](https://user-images.githubusercontent.com/128350225/227586075-156238c3-80af-4093-a3ce-5ebd2db0ab85.png)
## Shape of Dataset after removal of outlier using z score:
### ![image](https://user-images.githubusercontent.com/128350225/227586436-decf51e2-6535-4c2f-bb5d-34259bf7a127.png)
(4) For the data set height_weight.csv detect weight and height outliers using IQR method:
## Dataset:
### ![image](https://user-images.githubusercontent.com/128350225/227586581-e9ac9f06-a9e2-4f47-9aa8-f71dbf5bd3e3.png)
## Dataset Head:
### ![image](https://user-images.githubusercontent.com/128350225/227586750-a4abcdca-74eb-4ff1-a35c-af08e13289a8.png)
## Dataset Info:
### ![image](https://user-images.githubusercontent.com/128350225/227586845-ecdd71cf-3439-45bb-a1ed-d26d0e4d6ba7.png)
## Dataset Describe:
### ![image](https://user-images.githubusercontent.com/128350225/227587008-82bdb5d6-b17a-4826-8420-551b30c68803.png)
## Null Values:
### ![image](https://user-images.githubusercontent.com/128350225/227587110-2e16a58f-e923-4ef5-a85b-ca4b75493f7b.png)
## Dataset Shape:
### ![image](https://user-images.githubusercontent.com/128350225/227587233-20b1b0d2-31a7-4aa7-ab95-3210676d8b1b.png)
## Weight - With outliers:
### ![image](https://user-images.githubusercontent.com/128350225/227587415-f1a012de-f9c1-4103-9529-1ebb8c8102da.png)
## Weight - Dataset after removing Outliers using IQR method:
### ![image](https://user-images.githubusercontent.com/128350225/227587547-947140f8-1b00-428f-bbd2-56eaba503887.png)
## Weight - Shape of Dataset after removing Outliers using IQR method:
### ![image](https://user-images.githubusercontent.com/128350225/227587687-c24d9893-26cd-4670-a1e4-b5e2c174d8d3.png)
## Weight - Without Outliers using IQR method:
### ![image](https://user-images.githubusercontent.com/128350225/227587807-f6e20ac0-0487-4059-bfe0-8cda55f5a888.png)
## Height - With outliers:
### ![image](https://user-images.githubusercontent.com/128350225/227587915-894fc8af-547c-4514-b6a4-10e75c873a8b.png)
## Height - Dataset after removing Outliers using IQR method:
### ![image](https://user-images.githubusercontent.com/128350225/227588158-1cf5f323-4fa1-4983-a13f-cef1d1ad5f57.png)
## Height - Shape of Dataset after removing Outliers using IQR method:
### ![image](https://user-images.githubusercontent.com/128350225/227588287-b5c41a77-1151-4304-9ec2-134e5346fbb2.png)
## Height - Without Outliers using IQR method:
### ![image](https://user-images.githubusercontent.com/128350225/227588444-3d6e00d8-a4b7-4674-b1eb-1bda605c6590.png)
## Result:
### Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
