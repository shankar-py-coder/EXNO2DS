# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
df=pd.read_csv("/content/titanic_dataset.csv")
df

```

<img width="1505" height="533" alt="image" src="https://github.com/user-attachments/assets/5a03fca0-6953-4d3c-86c3-3eda82918910" />

```

df.info()


```

<img width="515" height="435" alt="image" src="https://github.com/user-attachments/assets/da164004-9e04-4de5-a245-1ce12e5cd7d8" />

```

df.shape

```

<img width="362" height="88" alt="image" src="https://github.com/user-attachments/assets/cdab9e87-ee1c-4d81-be4d-1da15087a190" />

```

print(df.columns)

```

<img width="892" height="152" alt="image" src="https://github.com/user-attachments/assets/d3e274a8-0fdd-4194-94d9-4c003d92d223" />

```
df.describe()

```

<img width="947" height="372" alt="image" src="https://github.com/user-attachments/assets/278040c2-8b0f-4e28-b2e3-2fe7950f786f" />

```

print ("Data Types:")
display(df.dtypes.to_frame("Data type"))

print("Missing Values:")
missing=pd.DataFrame({
    "Missing count":df.isna().sum(),
    "Missing %":(df.isna().mean()*100).round(2)
})
display(missing.sort_values("Missing %",ascending=False))
print("Exact duplicate rows:",df.duplicated().sum())
print("Numeric Summary:")
display(df.describe().T)

```

<img width="451" height="540" alt="image" src="https://github.com/user-attachments/assets/5ad38361-83b5-4698-a0c1-f1f90f5205ae" />
<img width="582" height="557" alt="image" src="https://github.com/user-attachments/assets/b36e09c3-ebdb-45d5-8053-0c8d9df3f1bd" />
<img width="812" height="342" alt="image" src="https://github.com/user-attachments/assets/625d27cd-a146-4d28-a8b9-a70b44f21d26" />

```
df.nunique()

```

<img width="392" height="543" alt="image" src="https://github.com/user-attachments/assets/8f1a26aa-a98f-4679-a207-347ff73a033c" />

```

df["Survived"].value_counts()

```

<img width="381" height="220" alt="image" src="https://github.com/user-attachments/assets/1aa4a7c9-cbdb-40f7-a245-aaa7a2cbd73b" />

```

per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per

```

<img width="381" height="225" alt="image" src="https://github.com/user-attachments/assets/35ed69f4-480a-43bf-8316-e553cba0fdcf" />

```

sns.countplot(data=df,x="Survived")

```

<img width="747" height="571" alt="image" src="https://github.com/user-attachments/assets/5a498fd3-bce0-4306-b985-061ff6624dd7" />

```

df

```

<img width="1476" height="495" alt="image" src="https://github.com/user-attachments/assets/f7b611b9-0075-4ed8-b0ef-bd5d0bbe8ec6" />


```

df.Pclass.unique()


```

<img width="547" height="97" alt="image" src="https://github.com/user-attachments/assets/a81976d3-7f06-473c-8c05-1360991be4da" />

```

df.rename(columns={"Sex":"Gender"},inplace=True)
df

```

<img width="1457" height="500" alt="image" src="https://github.com/user-attachments/assets/83bd5ab2-e817-426a-8f2b-eb95dfa50e1b" />

```

sns.catplot(x="Gender", col="Survived", kind="count", data=df, height=5, aspect=.7)

```

<img width="902" height="645" alt="image" src="https://github.com/user-attachments/assets/6532d4c8-c1c3-4184-b425-a22ebf40f634" />

```

sns.catplot(x='Survived', hue='Gender', data=df, kind='count')

```

<img width="827" height="643" alt="image" src="https://github.com/user-attachments/assets/e31ed29a-a5e6-4341-91c9-8acc07d9cf69" />

```

df.boxplot(column="Age", by="Survived")

```

<img width="720" height="593" alt="image" src="https://github.com/user-attachments/assets/ceed3b81-4feb-40ab-b67c-2a3737700d9c" />

```

sns.scatterplot(x=df["Age"], y=df["Fare"])

```

<img width="732" height="570" alt="image" src="https://github.com/user-attachments/assets/6fad2b35-1220-4d67-ab9a-00ebad9174ae" />

```

sns.jointplot(x="Age", y="Fare", data=df)

```

<img width="738" height="698" alt="image" src="https://github.com/user-attachments/assets/08f6e1d6-d653-4c7e-85e3-563c4d50d8c5" />

```

fig, ax1 = plt.subplots(figsize=(8,5))
pt = sns.boxplot(ax=ax1, x='Pclass', y='Age', hue='Gender', data=df)

```

<img width="858" height="557" alt="image" src="https://github.com/user-attachments/assets/ebc4f837-dd3f-4100-b4b6-b0302637bf67" />

```

sns.catplot(data=df, col="Survived", x="Gender", hue="Pclass", kind="count")

```

<img width="1325" height="643" alt="image" src="https://github.com/user-attachments/assets/2e6e6eac-9c82-4452-9431-26b34261669a" />

```

corr = df.corr(numeric_only=True)
sns.heatmap(corr, annot=True)

```

<img width="756" height="626" alt="image" src="https://github.com/user-attachments/assets/a0318463-62a0-4e6e-9c08-15d5946cb9c2" />

```

sns.pairplot(df)

```

<img width="1653" height="673" alt="image" src="https://github.com/user-attachments/assets/c6ee7340-cb87-4c17-8d60-1ec9ba79edae" />


# RESULT

Thus python program to perform Exploratory Data Analysis on the given data set is executed.
