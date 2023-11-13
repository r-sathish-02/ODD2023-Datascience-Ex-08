# EX-08 Data Visualization 1
### AIM:
To Perform Data Visualization on a complex dataset and save the data to a file.
### EXPLANATION:
Data visualization is graphical representation of information and data.By using visual elements like charts,graphs,and maps,data visualization tools provide an accessible way to see and understand trends, outliers,and patterns in data.
### ALGORITHM:
- Step1: Read the given Data.
- Step2: Clean the Data Set using Data Cleaning Process.
- Step3: Apply Feature generation and selection techniques to all features of data set.
- Step4: Apply data visualization techniques to identify the patterns of the data.
### CODE:  
```python
Developed by : SATHISH R
Register No : 212222230138
```
<table>
  <tr>
    <td>

```Python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
``` 
  </td>  
<td>

 **Ouptut:**  
 
  ![A](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/f0e12ff0-efaf-408b-82b8-5a176e2ac429)![B](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/12f43e2e-a3e3-4702-b27f-01a7fe4b981d)


  </td>
</tr>  
</table>

![Screenshot 2023-11-07 192420](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/b83e5544-ba34-40b9-a006-04b928ccf3a7)

#### 1. Segment with Highest Sales:
<table>
<tr>
<td>

```Python
plt.title("Segment vs Sales ->LinePlot")
sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales ->BarPlot")
sns.barplot(x="Segment",y="Sales",data=df)
plt.show()
```  
</td>  
<td>
  
  ![download](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/f915f572-a375-4d37-938c-eed25b998e18)
</td>
</tr>  
</table>

#### 2. City with Highest Profit:
<table>
<tr>
<td width=40%>
  
```Python
df1 = df[(df.Profit >= 300)]
st=df1.loc[:,["City","Profit"]]
st=st.groupby(by=["City"]).sum()
          .sort_values(by="Profit")
sns.barplot(x=st.index,y="Profit",data=st)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()
```
</td>  
<td>

![download](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/4faff60a-1f27-4e8f-b588-4beab6fb5366)

</td>
</tr>  
</table>

#### 3. Profitable Ship Mode:
<table>
<tr>
<td>
  
```Python
sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.title("ShipMode vs Profit Barplot")
sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.title("ShipMode vs Profit Lineplot")
plt.show()
```
</td>  
<td>

<img height=80% width=100% src="https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/72b4a504-fa5f-4398-a62f-b92467180b87">  
</td>
</tr>  
</table>

#### 4. Sales of the Product Based on the Region:

<table>
<tr>
<td>
  
```Python
st=df.loc[:,["Region","Sales"]]
st=st.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=st.index,y="Sales",data=st)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.title("Region vs Sales BarPlot")
plt.show()
```
</td>  
<td>

<img height=49% width=70% src="https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/2d5a1c0a-2d47-4c09-a9ec-fcb405bd87e2">
</td>
</tr>  
</table>

#### 5. Relation Between Sales and Profit.

<table>
<tr>
<td>
  
```Python
df.groupby(['Region']).sum().plot(kind='pie',y='Sales',
      figsize=(3,6),pctdistance=.5,labeldistance=1.2)
df["Sales"].corr(df["Profit"])
df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()
sns.pairplot(df_corr, kind="scatter")
plt.show()
```
</td>  
<td>

<img height=49% width=49% src="https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/da5050b3-8396-4857-851f-e1d0fd534617"><img height=49% width=49% src="https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/a10da9a1-1b21-4970-8c95-33997bf45b05">

</td>
</tr>  
</table>

#### 5. Relation Between Sales and Profit Based on.
- **Segment:**
  <table>
  <tr>
  <td>

  ```Python
  gd=df.groupby('Segment')[['Sales', 'Profit']].mean()
  ax.bar(gd.index,gd['Sales'],label='Sales')
  ax.bar(gd.index,gd['Profit'],bottom=gd['Sales'],label='Profit')
  ax.set_xlabel('Segment')
  ax.set_ylabel('Value')
  plt.title("Based on Segments")
  ax.legend()
  plt.show()
  ```
  </td>  
  <td>
   
   ![download](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/98bdc7f0-eaaa-4da2-93b2-8533ced0a62a)
 
  </td>
  </tr>  
  </table>
  
- **City:**
  <table>
  <tr>
  <td>
  
  ```Python
  gd=df.groupby('City')[['Sales','Profit']].mean()
  ax.bar(gd.index,gd['Sales'],label='Sales')
  ax.bar(gd.index,gd['Profit'],bottom=gd['Sales'],label='Profit')
  ax.set_xlabel('City')
  ax.set_ylabel('Value')
  plt.title("Based on City")
  ax.legend()
  plt.show()
  ```
  </td>  
  <td>
  
  ![download](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/a0360307-f180-47e7-8182-b24f4dbc0b1c)
  </td>
  </tr>  
  </table>

- **States:**
  <table>
  <tr>
  <td>
  
  ```Python
  gd = df.groupby('State')[['Sales', 'Profit']].mean()
  fig,ax=plt.subplots(figsize=(3,3))
  ax.bar(gd.index,gd['Sales'],label='Sales')
  ax.bar(gd.index,gd['Profit'],bottom=gd['Sales'],label='Profit')
  ax.set_xlabel('State')
  ax.set_ylabel('Value')
  plt.title("Based on States")
  ax.legend()
  plt.show()
  ```
  </td>  
  <td>
  
  ![download](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/9f38de6d-9cf2-4ce3-83bd-74d0758d2605)

  </td>
  </tr>  
  </table>

- **Segment and Ship Mode:**
  <table>
  <tr>
  <td>
  
  ```Python
  gd=df.groupby(['Segment','Ship Mode'])[['Sales','Profit']].mean()
  pp=gd.reset_index().pivot(index='Segment',
    columns='Ship Mode',values=['Sales','Profit'])
  fig,ax=plt.subplots(figsize=(5,5))
  pd.plot(kind='bar',ax=ax)
  ax.set_xlabel('Segment')
  ax.set_ylabel('Value')
  plt.title("Segment And Ship")
  plt.legend()
  plt.show()
  ```
  </td>  
  <td>
  
  ![download](https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/91498ff5-46ff-4fb5-8cf5-3bf8b182d79a)
  </td>
  </tr>  
  </table>

- **Segment,Ship mode and Region**
    <table>
  <tr>
  <td>
  
  ```Python
  gd=df.groupby(['Segment','Ship Mode','Region'])
      [['Sales','Profit']].mean()
  pd=gd.reset_index().pivot(index=['Segment','Ship Mode'
          ],columns='Region',values= ['Sales','Profit'])
  sns.set_style("whitegrid")
  sns.set_palette("Set1")
  pd.plot(kind='bar',stacked=True,figsize=(10,5))
  plt.xlabel('Ship Mode')
  plt.ylabel('Value')
  plt.legend(title='Region')
  plt.show()
  ```
  </td>  
  <td>
  
  <img height=50% width=95% src="https://github.com/ROHITJAIND/EX-08-DATA-VISUALIZATION-1/assets/118707073/98cba7a4-2d1a-4e0f-9944-d1f08b6be8fa">
  </td>
  </tr>  
  </table>

### RESULT:
Hence the data visualization method for the given dataset applied successfully.

  
