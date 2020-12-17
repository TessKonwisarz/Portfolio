# Comparing groupby & pivot_table functions

> Both functions are used to aggregate a DataFrame from a dataset, however, they use 
> slightly different functions/methods/arguments to organize a dataset in an identical manner.


```python
#Import packages
import numpy as np
import pandas as pd
```

## Example 1: fitness dataset


```python
#Read in csv file
fitness = pd.read_csv('25.csv')
```


```python
#To view the first five rows of the dataset
fitness.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>step_count</th>
      <th>mood</th>
      <th>calories_burned</th>
      <th>hours_of_sleep</th>
      <th>bool_of_active</th>
      <th>weight_kg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-10-06</td>
      <td>5464</td>
      <td>200</td>
      <td>181</td>
      <td>5</td>
      <td>0</td>
      <td>66</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-10-07</td>
      <td>6041</td>
      <td>100</td>
      <td>197</td>
      <td>8</td>
      <td>0</td>
      <td>66</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-10-08</td>
      <td>25</td>
      <td>100</td>
      <td>0</td>
      <td>5</td>
      <td>0</td>
      <td>66</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-10-09</td>
      <td>5461</td>
      <td>100</td>
      <td>174</td>
      <td>4</td>
      <td>0</td>
      <td>66</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-10-10</td>
      <td>6915</td>
      <td>200</td>
      <td>223</td>
      <td>5</td>
      <td>500</td>
      <td>66</td>
    </tr>
  </tbody>
</table>
</div>




```python
#To view the last five rows of the dataset
fitness.tail(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>step_count</th>
      <th>mood</th>
      <th>calories_burned</th>
      <th>hours_of_sleep</th>
      <th>bool_of_active</th>
      <th>weight_kg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>91</th>
      <td>2018-01-05</td>
      <td>133</td>
      <td>100</td>
      <td>4</td>
      <td>2</td>
      <td>0</td>
      <td>64</td>
    </tr>
    <tr>
      <th>92</th>
      <td>2018-01-06</td>
      <td>153</td>
      <td>300</td>
      <td>0</td>
      <td>8</td>
      <td>0</td>
      <td>64</td>
    </tr>
    <tr>
      <th>93</th>
      <td>2018-01-07</td>
      <td>500</td>
      <td>200</td>
      <td>0</td>
      <td>5</td>
      <td>500</td>
      <td>64</td>
    </tr>
    <tr>
      <th>94</th>
      <td>2018-01-08</td>
      <td>2127</td>
      <td>200</td>
      <td>0</td>
      <td>5</td>
      <td>0</td>
      <td>64</td>
    </tr>
    <tr>
      <th>95</th>
      <td>2018-01-09</td>
      <td>2203</td>
      <td>300</td>
      <td>0</td>
      <td>5</td>
      <td>500</td>
      <td>64</td>
    </tr>
  </tbody>
</table>
</div>



> **groupby:** fitness DataFrame


```python
#Displaying the data to note potential influential variables in the data, 
#grouping by a categorical variable (i.e. 'mood')
print("Table 1: Displaying fitness data using groupby")
fitness.groupby('mood').mean()
```

    Table 1: Displaying fitness data using groupby





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>step_count</th>
      <th>calories_burned</th>
      <th>hours_of_sleep</th>
      <th>bool_of_active</th>
      <th>weight_kg</th>
    </tr>
    <tr>
      <th>mood</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>2103.068966</td>
      <td>67.724138</td>
      <td>5.034483</td>
      <td>68.965517</td>
      <td>64.724138</td>
    </tr>
    <tr>
      <th>200</th>
      <td>3153.777778</td>
      <td>98.703704</td>
      <td>4.666667</td>
      <td>259.259259</td>
      <td>64.185185</td>
    </tr>
    <tr>
      <th>300</th>
      <td>3392.725000</td>
      <td>108.550000</td>
      <td>5.725000</td>
      <td>300.000000</td>
      <td>64.025000</td>
    </tr>
  </tbody>
</table>
</div>



> **pivot_table:** fitness DataFrame


```python
#Creating a pivot table with the same dataset to compare its functions
#When using a pivot table, the function automatically orders the variables alphabetically
#and extracts the mean values unless specified
print("Table 2: Displaying fitness data using pivot table")
fit_pt = pd.pivot_table(fitness,index=["mood"])
col_order= ["step_count", "calories_burned","hours_of_sleep","bool_of_active","weight_kg"]
fit_pt.reindex(col_order, axis=1)
```

    Table 2: Displaying fitness data using pivot table





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>step_count</th>
      <th>calories_burned</th>
      <th>hours_of_sleep</th>
      <th>bool_of_active</th>
      <th>weight_kg</th>
    </tr>
    <tr>
      <th>mood</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>2103.068966</td>
      <td>67.724138</td>
      <td>5.034483</td>
      <td>68.965517</td>
      <td>64.724138</td>
    </tr>
    <tr>
      <th>200</th>
      <td>3153.777778</td>
      <td>98.703704</td>
      <td>4.666667</td>
      <td>259.259259</td>
      <td>64.185185</td>
    </tr>
    <tr>
      <th>300</th>
      <td>3392.725000</td>
      <td>108.550000</td>
      <td>5.725000</td>
      <td>300.000000</td>
      <td>64.025000</td>
    </tr>
  </tbody>
</table>
</div>



## Example 2: student performance dataset


```python
#Using new dataset to better explore function
#Read in Student exam performance dataset
sp = pd.read_csv('StudentsPerformance.csv')
```


```python
#to view information about the dataset (i.e. columns and # of entries)
sp.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1000 entries, 0 to 999
    Data columns (total 8 columns):
     #   Column                       Non-Null Count  Dtype 
    ---  ------                       --------------  ----- 
     0   gender                       1000 non-null   object
     1   race/ethnicity               1000 non-null   object
     2   parental level of education  1000 non-null   object
     3   lunch                        1000 non-null   object
     4   test preparation course      1000 non-null   object
     5   math score                   1000 non-null   int64 
     6   reading score                1000 non-null   int64 
     7   writing score                1000 non-null   int64 
    dtypes: int64(3), object(5)
    memory usage: 62.6+ KB



```python
#We can use groupby to group multiple columns to group the table based on unique 
#terms within the dataset, organizing a table into categories
#With groupby you can specify the columns to be displayed in the dataframe with 
#double square brackets after the df variable
#To get the table formatting output, you must specify a method to apply to the data (e.g., .mean(), .unique(), etc.)
print("Table 3: Student performance data using groupby")
sp[['gender','race/ethnicity','test preparation course','math score','reading score']].groupby(['gender','race/ethnicity','test preparation course']).mean()
```

    Table 3: Student performance data using groupby





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th>math score</th>
      <th>reading score</th>
    </tr>
    <tr>
      <th>gender</th>
      <th>race/ethnicity</th>
      <th>test preparation course</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="10" valign="top">female</th>
      <th rowspan="2" valign="top">group A</th>
      <th>completed</th>
      <td>67.750000</td>
      <td>77.000000</td>
    </tr>
    <tr>
      <th>none</th>
      <td>53.916667</td>
      <td>65.000000</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group B</th>
      <th>completed</th>
      <td>62.628571</td>
      <td>74.514286</td>
    </tr>
    <tr>
      <th>none</th>
      <td>60.782609</td>
      <td>69.333333</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group C</th>
      <th>completed</th>
      <td>66.101449</td>
      <td>77.304348</td>
    </tr>
    <tr>
      <th>none</th>
      <td>59.504505</td>
      <td>68.612613</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group D</th>
      <th>completed</th>
      <td>67.727273</td>
      <td>77.340909</td>
    </tr>
    <tr>
      <th>none</th>
      <td>63.964706</td>
      <td>72.341176</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group E</th>
      <th>completed</th>
      <td>75.750000</td>
      <td>82.000000</td>
    </tr>
    <tr>
      <th>none</th>
      <td>68.177778</td>
      <td>72.555556</td>
    </tr>
    <tr>
      <th rowspan="10" valign="top">male</th>
      <th rowspan="2" valign="top">group A</th>
      <th>completed</th>
      <td>68.578947</td>
      <td>67.263158</td>
    </tr>
    <tr>
      <th>none</th>
      <td>61.029412</td>
      <td>58.647059</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group B</th>
      <th>completed</th>
      <td>72.030303</td>
      <td>71.090909</td>
    </tr>
    <tr>
      <th>none</th>
      <td>62.132075</td>
      <td>57.716981</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group C</th>
      <th>completed</th>
      <td>69.500000</td>
      <td>68.416667</td>
    </tr>
    <tr>
      <th>none</th>
      <td>66.615385</td>
      <td>63.846154</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group D</th>
      <th>completed</th>
      <td>72.184211</td>
      <td>70.447368</td>
    </tr>
    <tr>
      <th>none</th>
      <td>68.305263</td>
      <td>64.410526</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group E</th>
      <th>completed</th>
      <td>78.555556</td>
      <td>73.111111</td>
    </tr>
    <tr>
      <th>none</th>
      <td>74.885714</td>
      <td>67.400000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Similar to table 3, instead using pivot tables for data maipulation,
#pivot_tables has the aggfunc argument to adjust the mean function default
print("Table 4: Student performance dataset using pivot table")
pd.pivot_table(sp, index=['gender','race/ethnicity', 'test preparation course'], 
               values=['math score','reading score'], aggfunc=np.sum)
```

    Table 4: Student performance dataset using pivot table





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th>math score</th>
      <th>reading score</th>
    </tr>
    <tr>
      <th>gender</th>
      <th>race/ethnicity</th>
      <th>test preparation course</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="10" valign="top">female</th>
      <th rowspan="2" valign="top">group A</th>
      <th>completed</th>
      <td>813</td>
      <td>924</td>
    </tr>
    <tr>
      <th>none</th>
      <td>1294</td>
      <td>1560</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group B</th>
      <th>completed</th>
      <td>2192</td>
      <td>2608</td>
    </tr>
    <tr>
      <th>none</th>
      <td>4194</td>
      <td>4784</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group C</th>
      <th>completed</th>
      <td>4561</td>
      <td>5334</td>
    </tr>
    <tr>
      <th>none</th>
      <td>6605</td>
      <td>7616</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group D</th>
      <th>completed</th>
      <td>2980</td>
      <td>3403</td>
    </tr>
    <tr>
      <th>none</th>
      <td>5437</td>
      <td>6149</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group E</th>
      <th>completed</th>
      <td>1818</td>
      <td>1968</td>
    </tr>
    <tr>
      <th>none</th>
      <td>3068</td>
      <td>3265</td>
    </tr>
    <tr>
      <th rowspan="10" valign="top">male</th>
      <th rowspan="2" valign="top">group A</th>
      <th>completed</th>
      <td>1303</td>
      <td>1278</td>
    </tr>
    <tr>
      <th>none</th>
      <td>2075</td>
      <td>1994</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group B</th>
      <th>completed</th>
      <td>2377</td>
      <td>2346</td>
    </tr>
    <tr>
      <th>none</th>
      <td>3293</td>
      <td>3059</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group C</th>
      <th>completed</th>
      <td>3336</td>
      <td>3284</td>
    </tr>
    <tr>
      <th>none</th>
      <td>6062</td>
      <td>5810</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group D</th>
      <th>completed</th>
      <td>2743</td>
      <td>2677</td>
    </tr>
    <tr>
      <th>none</th>
      <td>6489</td>
      <td>6119</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group E</th>
      <th>completed</th>
      <td>2828</td>
      <td>2632</td>
    </tr>
    <tr>
      <th>none</th>
      <td>2621</td>
      <td>2359</td>
    </tr>
  </tbody>
</table>
</div>




```python
#To represent the data in a multiindex format using groupby, 
#the order of grouping determines which variable will define the column 
#categories (i.e. notice 'gender' is stated at the very end of columns to group the data by)
print("Table 5: Multi-index DataFrame using groupby")
sp[['gender','race/ethnicity','test preparation course','math score','reading score']].groupby(['race/ethnicity','test preparation course','gender']).mean().unstack()
```

    Table 5: Multi-index DataFrame using groupby





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th colspan="2" halign="left">math score</th>
      <th colspan="2" halign="left">reading score</th>
    </tr>
    <tr>
      <th></th>
      <th>gender</th>
      <th>female</th>
      <th>male</th>
      <th>female</th>
      <th>male</th>
    </tr>
    <tr>
      <th>race/ethnicity</th>
      <th>test preparation course</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">group A</th>
      <th>completed</th>
      <td>67.750000</td>
      <td>68.578947</td>
      <td>77.000000</td>
      <td>67.263158</td>
    </tr>
    <tr>
      <th>none</th>
      <td>53.916667</td>
      <td>61.029412</td>
      <td>65.000000</td>
      <td>58.647059</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group B</th>
      <th>completed</th>
      <td>62.628571</td>
      <td>72.030303</td>
      <td>74.514286</td>
      <td>71.090909</td>
    </tr>
    <tr>
      <th>none</th>
      <td>60.782609</td>
      <td>62.132075</td>
      <td>69.333333</td>
      <td>57.716981</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group C</th>
      <th>completed</th>
      <td>66.101449</td>
      <td>69.500000</td>
      <td>77.304348</td>
      <td>68.416667</td>
    </tr>
    <tr>
      <th>none</th>
      <td>59.504505</td>
      <td>66.615385</td>
      <td>68.612613</td>
      <td>63.846154</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group D</th>
      <th>completed</th>
      <td>67.727273</td>
      <td>72.184211</td>
      <td>77.340909</td>
      <td>70.447368</td>
    </tr>
    <tr>
      <th>none</th>
      <td>63.964706</td>
      <td>68.305263</td>
      <td>72.341176</td>
      <td>64.410526</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group E</th>
      <th>completed</th>
      <td>75.750000</td>
      <td>78.555556</td>
      <td>82.000000</td>
      <td>73.111111</td>
    </tr>
    <tr>
      <th>none</th>
      <td>68.177778</td>
      <td>74.885714</td>
      <td>72.555556</td>
      <td>67.400000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#To do the same using the pivot table function, the groups can be indicated in 
#the index argument, while the columns are chose by the values argument. 
#Pivot tables, however, do not require a function and will automatically average the columns for each category.
print("Multi-index DataFrame using pivot table")
pd.pivot_table(sp, index=['race/ethnicity', 'test preparation course'], columns= 'gender',values=['math score','reading score'])
```

    Multi-index DataFrame using pivot table





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th colspan="2" halign="left">math score</th>
      <th colspan="2" halign="left">reading score</th>
    </tr>
    <tr>
      <th></th>
      <th>gender</th>
      <th>female</th>
      <th>male</th>
      <th>female</th>
      <th>male</th>
    </tr>
    <tr>
      <th>race/ethnicity</th>
      <th>test preparation course</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">group A</th>
      <th>completed</th>
      <td>67.750000</td>
      <td>68.578947</td>
      <td>77.000000</td>
      <td>67.263158</td>
    </tr>
    <tr>
      <th>none</th>
      <td>53.916667</td>
      <td>61.029412</td>
      <td>65.000000</td>
      <td>58.647059</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group B</th>
      <th>completed</th>
      <td>62.628571</td>
      <td>72.030303</td>
      <td>74.514286</td>
      <td>71.090909</td>
    </tr>
    <tr>
      <th>none</th>
      <td>60.782609</td>
      <td>62.132075</td>
      <td>69.333333</td>
      <td>57.716981</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group C</th>
      <th>completed</th>
      <td>66.101449</td>
      <td>69.500000</td>
      <td>77.304348</td>
      <td>68.416667</td>
    </tr>
    <tr>
      <th>none</th>
      <td>59.504505</td>
      <td>66.615385</td>
      <td>68.612613</td>
      <td>63.846154</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group D</th>
      <th>completed</th>
      <td>67.727273</td>
      <td>72.184211</td>
      <td>77.340909</td>
      <td>70.447368</td>
    </tr>
    <tr>
      <th>none</th>
      <td>63.964706</td>
      <td>68.305263</td>
      <td>72.341176</td>
      <td>64.410526</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">group E</th>
      <th>completed</th>
      <td>75.750000</td>
      <td>78.555556</td>
      <td>82.000000</td>
      <td>73.111111</td>
    </tr>
    <tr>
      <th>none</th>
      <td>68.177778</td>
      <td>74.885714</td>
      <td>72.555556</td>
      <td>67.400000</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
