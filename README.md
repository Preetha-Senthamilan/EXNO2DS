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
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/titanic_dataset.csv")
df
```
![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/bfa04142-41e0-40fc-b1f1-6ba16deda5c7)

df.info()

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/e6d761d7-c1db-4ed9-aa95-18e80af75e09)

df.set_index("PassengerId",inplace =True)
df.shape

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/e317f2e0-363b-427a-8c71-3175d39a1054)


df.nunique()

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/e9cdf9b3-07ce-4ef3-97a0-488b0ffcd434)

df["Survived"].value_counts()

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/379a9e2e-fdda-4802-a5b7-8e70506d58aa)

per=(df['Survived'].value_counts()/df.shape[0]*100).round(2)
per

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/4b346711-6eba-407d-a2fa-c5dae252b798)

sns.countplot(data=df,x="Survived")


![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/cf3bb6e8-1e03-4741-965b-435a6d7b16ad)

fig, ax1 = plt.subplots(figsize=(5,5))
graph=sns.countplot(ax=ax1,x= 'Survived', data=df)
graph.set_xticklabels (graph.get_xticklabels (), rotation=90)
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2., height + 0.1, height,ha="center")


![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/789630c5-796e-4c8e-a8d1-1880b7686853)


df.Pclass.unique()

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/c3c52a2a-38fb-4ed6-81cc-d3e3bb051051)

df.rename(columns = {'Sex':"Gender"},inplace=True)
df

sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)


![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/a6e5b0c3-c596-4448-8be5-95482104b40d)

sns.catplot(x="Survived",hue="Gender",data=df,kind="count")

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/50c64ed2-f10a-4faf-8483-86d29f1a7ecc)

fig, ax1 = plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=df,x="Survived", hue="Pclass", palette="rainbow")
graph.set_xticklabels (graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height+ 20.8, height,ha="left")


![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/ceb1905d-e2bf-41c2-bf6a-dc8269bd4df5)


df.boxplot(column="Age",by="Survived")

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/f70380d2-cd62-4417-be8c-d06ae23d0eb4)

sns.scatterplot(x=df["Age"],y=df["Fare"])


![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/184dce3a-0895-49d2-a715-a3f54608e2b2)

sns.jointplot(x="Age",y="Fare",data=df)

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/c0ff903d-a265-4d7a-8161-db2b0bcd5b4d)


fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue="Gender",data=df)

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/d07a48f7-4271-4c20-8c40-95ee3cb2add2)

  sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")


![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/e24f580f-5304-436e-a74d-f71f9247c632)

g= sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass", kind = "count", legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax =g.facet_axis(0,0)
for p in ax.patches:
ax.text(p.get_x()-0.01,p.get_height()*1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/bf9e027f-3b1b-48f1-a804-03b5efa20608)


corr=df.corr()
sns.heatmap(corr,annot=True)

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/63d6a839-798e-49ac-9691-bbfc54f6534d)

sns.pairplot(df)

![image](https://github.com/Preetha-Senthamilan/EXNO2DS/assets/119390282/57811c5a-f510-47de-a32e-0e555ce915df)


## RESULT
        
Thus, the outputs verifies that the data set has been applied the EDA process and methods.
