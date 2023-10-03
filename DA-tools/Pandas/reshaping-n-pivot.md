# Reshaping and Pivoting Data Tables


```python
import pandas as pd
```


```python
df2 = pd.DataFrame({
    'Date': ['2023-09-01', '2023-09-01', '2023-09-02', '2023-09-02'],
    'City': ['New York', 'Los Angeles', 'New York', 'Los Angeles'],
    'Temperature': [75, 82, 72, 79],
    'Humidity': [55, 60, 50, 65]
})

df2
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
      <th>City</th>
      <th>Temperature</th>
      <th>Humidity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2023-09-01</td>
      <td>New York</td>
      <td>75</td>
      <td>55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2023-09-01</td>
      <td>Los Angeles</td>
      <td>82</td>
      <td>60</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2023-09-02</td>
      <td>New York</td>
      <td>72</td>
      <td>50</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2023-09-02</td>
      <td>Los Angeles</td>
      <td>79</td>
      <td>65</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Pivoting with only one value
pivot_df = df2.pivot(index='Date', columns='City', values='Temperature')

pivot_df
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
      <th>City</th>
      <th>Los Angeles</th>
      <th>New York</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-09-01</th>
      <td>82</td>
      <td>75</td>
    </tr>
    <tr>
      <th>2023-09-02</th>
      <td>79</td>
      <td>72</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Pivot the DataFrame
pivot_df2 = df2.pivot(index='Date', columns='City')

pivot_df2
```




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
      <th colspan="2" halign="left">Temperature</th>
      <th colspan="2" halign="left">Humidity</th>
    </tr>
    <tr>
      <th>City</th>
      <th>Los Angeles</th>
      <th>New York</th>
      <th>Los Angeles</th>
      <th>New York</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-09-01</th>
      <td>82</td>
      <td>75</td>
      <td>60</td>
      <td>55</td>
    </tr>
    <tr>
      <th>2023-09-02</th>
      <td>79</td>
      <td>72</td>
      <td>65</td>
      <td>50</td>
    </tr>
  </tbody>
</table>
</div>




```python
# another way of pivoting a value
pivot_df2["Humidity"]
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
      <th>City</th>
      <th>Los Angeles</th>
      <th>New York</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-09-01</th>
      <td>60</td>
      <td>55</td>
    </tr>
    <tr>
      <th>2023-09-02</th>
      <td>65</td>
      <td>50</td>
    </tr>
  </tbody>
</table>
</div>



> Note: pivot() can only handle unique rows specified by index and columns. If you data contains duplicates, use pivot_table().


```python
import random

df = pd.DataFrame({
    'Date': pd.date_range(start='2023-01-01', periods=24, freq='D'),
    'Product': [random.choice(['Product A', 'Product B', 'Product C']) for _ in range(24)],
    'Region': [random.choice(['North', 'South', 'East', 'West']) for _ in range(24)],
    'Salesperson': [random.choice(['Alice', 'Bob', 'Charlie', 'David']) for _ in range(24)],
    'Quantity': [random.randint(1, 100) for _ in range(24)],
    'Revenue': [random.uniform(100, 1000) for _ in range(24)],
    'Discount': [random.uniform(0, 0.3) for _ in range(24)]
})

df
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
      <th>Product</th>
      <th>Region</th>
      <th>Salesperson</th>
      <th>Quantity</th>
      <th>Revenue</th>
      <th>Discount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2023-01-01</td>
      <td>Product C</td>
      <td>West</td>
      <td>Alice</td>
      <td>94</td>
      <td>113.605019</td>
      <td>0.005939</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2023-01-02</td>
      <td>Product B</td>
      <td>South</td>
      <td>Bob</td>
      <td>43</td>
      <td>270.812185</td>
      <td>0.260673</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2023-01-03</td>
      <td>Product C</td>
      <td>East</td>
      <td>Charlie</td>
      <td>46</td>
      <td>379.921093</td>
      <td>0.289651</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2023-01-04</td>
      <td>Product A</td>
      <td>West</td>
      <td>Charlie</td>
      <td>91</td>
      <td>308.300418</td>
      <td>0.186368</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2023-01-05</td>
      <td>Product C</td>
      <td>North</td>
      <td>Bob</td>
      <td>99</td>
      <td>148.329768</td>
      <td>0.286213</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2023-01-06</td>
      <td>Product B</td>
      <td>North</td>
      <td>Alice</td>
      <td>30</td>
      <td>444.536551</td>
      <td>0.192599</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2023-01-07</td>
      <td>Product B</td>
      <td>North</td>
      <td>Charlie</td>
      <td>78</td>
      <td>475.805539</td>
      <td>0.055592</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2023-01-08</td>
      <td>Product C</td>
      <td>West</td>
      <td>Alice</td>
      <td>31</td>
      <td>689.752691</td>
      <td>0.277317</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2023-01-09</td>
      <td>Product A</td>
      <td>North</td>
      <td>David</td>
      <td>36</td>
      <td>473.341889</td>
      <td>0.224978</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2023-01-10</td>
      <td>Product A</td>
      <td>South</td>
      <td>Alice</td>
      <td>20</td>
      <td>556.972303</td>
      <td>0.083827</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2023-01-11</td>
      <td>Product C</td>
      <td>South</td>
      <td>Charlie</td>
      <td>28</td>
      <td>431.154195</td>
      <td>0.288060</td>
    </tr>
    <tr>
      <th>11</th>
      <td>2023-01-12</td>
      <td>Product B</td>
      <td>West</td>
      <td>Alice</td>
      <td>12</td>
      <td>267.823341</td>
      <td>0.291188</td>
    </tr>
    <tr>
      <th>12</th>
      <td>2023-01-13</td>
      <td>Product B</td>
      <td>West</td>
      <td>Bob</td>
      <td>88</td>
      <td>806.599805</td>
      <td>0.000061</td>
    </tr>
    <tr>
      <th>13</th>
      <td>2023-01-14</td>
      <td>Product A</td>
      <td>North</td>
      <td>Bob</td>
      <td>9</td>
      <td>758.139224</td>
      <td>0.296536</td>
    </tr>
    <tr>
      <th>14</th>
      <td>2023-01-15</td>
      <td>Product A</td>
      <td>South</td>
      <td>Charlie</td>
      <td>69</td>
      <td>491.656987</td>
      <td>0.198526</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2023-01-16</td>
      <td>Product C</td>
      <td>East</td>
      <td>David</td>
      <td>34</td>
      <td>259.989669</td>
      <td>0.129658</td>
    </tr>
    <tr>
      <th>16</th>
      <td>2023-01-17</td>
      <td>Product B</td>
      <td>South</td>
      <td>Alice</td>
      <td>4</td>
      <td>442.904812</td>
      <td>0.210089</td>
    </tr>
    <tr>
      <th>17</th>
      <td>2023-01-18</td>
      <td>Product C</td>
      <td>East</td>
      <td>Bob</td>
      <td>61</td>
      <td>492.508169</td>
      <td>0.150000</td>
    </tr>
    <tr>
      <th>18</th>
      <td>2023-01-19</td>
      <td>Product A</td>
      <td>South</td>
      <td>David</td>
      <td>42</td>
      <td>977.251296</td>
      <td>0.074186</td>
    </tr>
    <tr>
      <th>19</th>
      <td>2023-01-20</td>
      <td>Product B</td>
      <td>North</td>
      <td>Bob</td>
      <td>77</td>
      <td>120.836222</td>
      <td>0.269793</td>
    </tr>
    <tr>
      <th>20</th>
      <td>2023-01-21</td>
      <td>Product B</td>
      <td>West</td>
      <td>Charlie</td>
      <td>88</td>
      <td>813.512123</td>
      <td>0.295050</td>
    </tr>
    <tr>
      <th>21</th>
      <td>2023-01-22</td>
      <td>Product C</td>
      <td>South</td>
      <td>David</td>
      <td>79</td>
      <td>951.435654</td>
      <td>0.187863</td>
    </tr>
    <tr>
      <th>22</th>
      <td>2023-01-23</td>
      <td>Product B</td>
      <td>East</td>
      <td>David</td>
      <td>34</td>
      <td>548.791728</td>
      <td>0.138378</td>
    </tr>
    <tr>
      <th>23</th>
      <td>2023-01-24</td>
      <td>Product C</td>
      <td>West</td>
      <td>David</td>
      <td>88</td>
      <td>828.828762</td>
      <td>0.262360</td>
    </tr>
  </tbody>
</table>
</div>


