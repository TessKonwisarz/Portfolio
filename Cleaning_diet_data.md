```
import pandas as pd
```


```
diet_data = pd.read_csv('diet_data.csv')
```


```
#dataset imported from kaggle.com, calorie intake and exercise recorded in 2018 for one participant
diet_data.head()
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
      <th>Date</th>
      <th>Stone</th>
      <th>Pounds</th>
      <th>Ounces</th>
      <th>weight_oz</th>
      <th>calories</th>
      <th>cals_per_oz</th>
      <th>five_donuts</th>
      <th>walk</th>
      <th>run</th>
      <th>wine</th>
      <th>prot</th>
      <th>weight</th>
      <th>change</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7/30/2018</td>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
      <td>2726.0</td>
      <td>1950.0</td>
      <td>0.72</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>-30.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7/31/2018</td>
      <td>12.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>2696.0</td>
      <td>2600.0</td>
      <td>0.96</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8/1/2018</td>
      <td>12.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>2704.0</td>
      <td>2500.0</td>
      <td>0.92</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8/2/2018</td>
      <td>12.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>2704.0</td>
      <td>1850.0</td>
      <td>0.68</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>-40.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>8/3/2018</td>
      <td>11.0</td>
      <td>12.0</td>
      <td>8.0</td>
      <td>2664.0</td>
      <td>2900.0</td>
      <td>1.09</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>14.0</td>
    </tr>
  </tbody>
</table>
</div>




```
diet_data.tail()
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
      <th>Date</th>
      <th>Stone</th>
      <th>Pounds</th>
      <th>Ounces</th>
      <th>weight_oz</th>
      <th>calories</th>
      <th>cals_per_oz</th>
      <th>five_donuts</th>
      <th>walk</th>
      <th>run</th>
      <th>wine</th>
      <th>prot</th>
      <th>weight</th>
      <th>change</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>146</th>
      <td>12/23/2018</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>#DIV/0!</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>147</th>
      <td>12/24/2018</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>#DIV/0!</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>148</th>
      <td>12/25/2018</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>#DIV/0!</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>149</th>
      <td>12/26/2018</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>#DIV/0!</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>150</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```
#removing NaNs
diet_data = diet_data.dropna(how='any')
```


```
# adding new column to diet_data, transforming weight_oz column to weight_lb
diet_data["weight_lb"] = diet_data["weight_oz"]*0.0625
```


```
#adding new column to compare caloric intake and weight changes
diet_data['cals_per_lb'] = diet_data['calories']/ diet_data['weight_lb']
```


```
diet_data.head()
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
      <th>Date</th>
      <th>Stone</th>
      <th>Pounds</th>
      <th>Ounces</th>
      <th>weight_oz</th>
      <th>calories</th>
      <th>cals_per_oz</th>
      <th>five_donuts</th>
      <th>walk</th>
      <th>run</th>
      <th>wine</th>
      <th>prot</th>
      <th>weight</th>
      <th>change</th>
      <th>weight_lb</th>
      <th>cals_per_lb</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7/30/2018</td>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
      <td>2726.0</td>
      <td>1950.0</td>
      <td>0.72</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>-30.0</td>
      <td>170.375</td>
      <td>11.445341</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7/31/2018</td>
      <td>12.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>2696.0</td>
      <td>2600.0</td>
      <td>0.96</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>168.500</td>
      <td>15.430267</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8/1/2018</td>
      <td>12.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>2704.0</td>
      <td>2500.0</td>
      <td>0.92</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>169.000</td>
      <td>14.792899</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8/2/2018</td>
      <td>12.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>2704.0</td>
      <td>1850.0</td>
      <td>0.68</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>-40.0</td>
      <td>169.000</td>
      <td>10.946746</td>
    </tr>
    <tr>
      <th>4</th>
      <td>8/3/2018</td>
      <td>11.0</td>
      <td>12.0</td>
      <td>8.0</td>
      <td>2664.0</td>
      <td>2900.0</td>
      <td>1.09</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>14.0</td>
      <td>166.500</td>
      <td>17.417417</td>
    </tr>
  </tbody>
</table>
</div>




```
#setting the index
diet_data.set_index('Date', inplace=True)
```


```
#creating a column for difference between rows in a column (n2 - n1)
diet_data["weight_diff"] = diet_data["cals_per_lb"].diff()
```


```
#selecting data columns with relvant data for manipulation
diet_data[['weight_lb', 'calories', 'cals_per_lb', 'weight_diff','run','walk','wine']]
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
      <th>weight_lb</th>
      <th>calories</th>
      <th>cals_per_lb</th>
      <th>weight_diff</th>
      <th>run</th>
      <th>walk</th>
      <th>wine</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7/30/2018</th>
      <td>170.375</td>
      <td>1950.0</td>
      <td>11.445341</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>7/31/2018</th>
      <td>168.500</td>
      <td>2600.0</td>
      <td>15.430267</td>
      <td>3.984926</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>8/1/2018</th>
      <td>169.000</td>
      <td>2500.0</td>
      <td>14.792899</td>
      <td>-0.637368</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>8/2/2018</th>
      <td>169.000</td>
      <td>1850.0</td>
      <td>10.946746</td>
      <td>-3.846154</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>8/3/2018</th>
      <td>166.500</td>
      <td>2900.0</td>
      <td>17.417417</td>
      <td>6.470672</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>12/15/2018</th>
      <td>165.000</td>
      <td>5750.0</td>
      <td>34.848485</td>
      <td>20.951204</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>12/16/2018</th>
      <td>166.000</td>
      <td>2950.0</td>
      <td>17.771084</td>
      <td>-17.077401</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>12/17/2018</th>
      <td>166.000</td>
      <td>1950.0</td>
      <td>11.746988</td>
      <td>-6.024096</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>12/18/2018</th>
      <td>164.500</td>
      <td>1900.0</td>
      <td>11.550152</td>
      <td>-0.196836</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>12/19/2018</th>
      <td>164.250</td>
      <td>1500.0</td>
      <td>9.132420</td>
      <td>-2.417732</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
<p>140 rows × 7 columns</p>
</div>




```

```
