# EX-02  Outlier detection and removal

## AIM

 To do the following on the given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
    
 ## ALGORITHM
 
 ### Step 1
 
  Read the given data
  
 ### Step 2
  
  Remove outliers using IQR method
  
 ### Step 3
  
  Using zscore remove the outliers
  
 ### Step 4
  
  Read the next data
  
 ### Step 5
  
  Using IQR method detect the height and weight outliers and print them
  
 ### Step 6
  
  Save the cleaned data to the file
  
     
 ## CODE
 
import pandas as pd

df=pd.read_csv('/content/bhp.csv')

df.head()

Q1 = df['price_per_sqft'].quantile(0.25)

Q3 = df['price_per_sqft'].quantile(0.75)

IQR = Q3-Q1

df1=df[((df['price_per_sqft']>=Q1-1.5*IQR)&(df['price_per_sqft']<=Q3+1.5*IQR))]

df1.head()

from scipy import stats

import numpy as np

z=np.abs(stats.zscore(df['price_per_sqft']))

df1=df1[(z<3)]

df1.head()

import pandas as pd

df=pd.read_csv('/content/height_weight.csv')

df

Q1 = df['weight'].quantile(0.25)

Q3 = df['weight'].quantile(0.75)

IQR = Q3-Q1

df1=df[((df['weight']<=Q1-1.5*IQR)|(df['weight']>=Q3+1.5*IQR))]

df1

Q1 = df['height'].quantile(0.25)

Q3 = df['height'].quantile(0.75)

IQR = Q3-Q1

df1=df[((df['height']<=Q1-1.5*IQR)|(df['height']>=Q3+1.5*IQR))]

df1

## OUTPUT

![op1](https://user-images.githubusercontent.com/112301582/227751290-59d2ace2-c172-4ca2-8c7c-2896dc673629.png)

![op2](https://user-images.githubusercontent.com/112301582/227751297-5d66cbb7-9a0d-4e69-ab5b-e5d09e0b8a28.png)

![op3](https://user-images.githubusercontent.com/112301582/227751300-255ad96f-77b8-41ad-b479-8f77318e4212.png)

![op4](https://user-images.githubusercontent.com/112301582/227751303-fcf445d1-e239-47e8-a162-353f7d456593.png)

![op5](https://user-images.githubusercontent.com/112301582/227751304-8bc7f48f-e6b4-4baf-bd06-9cc91cf02860.png)

![op6](https://user-images.githubusercontent.com/112301582/227751307-6a4c3f49-2491-4320-885b-af4dd38ab7cb.png)

## RESULT 

Thus the outliers of the given data is handled and removed successfully.
