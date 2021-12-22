```python
import numpy as np
np.random.seed(123) 
m1 = np.random.randint(0, 100, size = 10)
m2 = np.random.randint(10, size=(3, 4))
print("The one-dimensional array looks like this:\n", m1)
print("The two-dimensional array looks like this:\n", m2)
```

    The one-dimensional array looks like this:
     [66 92 98 17 83 57 86 97 96 47]
    The two-dimensional array looks like this:
     [[9 0 0 9]
     [3 4 0 0]
     [4 1 7 3]]
    


```python
m1[0]
```




    66




```python
m1[-2]
```




    96




```python
m2[0, -1]
```




    9




```python
m1[1:7:2]
```




    array([92, 17, 57])




```python
m1[5:]
```




    array([57, 86, 97, 96, 47])




```python
m1[::2]
```




    array([66, 98, 83, 86, 96])




```python
m1[1::2]
```




    array([92, 17, 57, 97, 47])




```python
m1[::-1]
```




    array([47, 96, 97, 86, 57, 83, 17, 98, 92, 66])




```python
m2[:2, :3] 
```




    array([[9, 0, 0],
           [3, 4, 0]])




```python
m2[:, 0]
```




    array([9, 3, 4])




```python
m2[0, :]
m2[0]
```




    array([9, 0, 0, 9])




```python
m2[m2 > 1]
```




    array([9, 9, 3, 4, 4, 7, 3])




```python
grid = np.array([[1, 2, 3],
                 [4, 5, 6]])
np.concatenate([grid, grid])
```




    array([[1, 2, 3],
           [4, 5, 6],
           [1, 2, 3],
           [4, 5, 6]])




```python
np.vstack([grid, grid+1])
```




    array([[1, 2, 3],
           [4, 5, 6],
           [2, 3, 4],
           [5, 6, 7]])




```python
np.hstack([grid, grid+1])
```




    array([[1, 2, 3, 2, 3, 4],
           [4, 5, 6, 5, 6, 7]])




```python
import pandas as pd
s1 = pd.Series([0.25, 0.5, 0.75, 1.0],
                 index=['a', 'b', 'c', 'd'])
s1
```




    a    0.25
    b    0.50
    c    0.75
    d    1.00
    dtype: float64




```python
s1['b']
```




    0.5




```python
s1[1]
```




    0.5




```python
s1['a':'c']
```




    a    0.25
    b    0.50
    c    0.75
    dtype: float64




```python
s1[(s1 > 0.3) & (s1 < 0.8)]
```




    b    0.50
    c    0.75
    dtype: float64




```python
s2 = pd.Series(['a', 'b', 'c'], index=[1, 3, 5])
s2
```




    1    a
    3    b
    5    c
    dtype: object




```python
s2[1]
```




    'a'




```python
s2['1'] # This will return error because index `1` is stored as a number.
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    ~\Anaconda3\lib\site-packages\pandas\core\indexes\base.py in get_loc(self, key, method, tolerance)
       3079             try:
    -> 3080                 return self._engine.get_loc(casted_key)
       3081             except KeyError as err:
    

    pandas\_libs\index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas\_libs\index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas\_libs\index_class_helper.pxi in pandas._libs.index.Int64Engine._check_type()
    

    KeyError: '1'

    
    The above exception was the direct cause of the following exception:
    

    KeyError                                  Traceback (most recent call last)

    <ipython-input-26-64f508f524b1> in <module>
    ----> 1 s2['1'] # This will return error because index `1` is stored as a number.
    

    ~\Anaconda3\lib\site-packages\pandas\core\series.py in __getitem__(self, key)
        851 
        852         elif key_is_scalar:
    --> 853             return self._get_value(key)
        854 
        855         if is_hashable(key):
    

    ~\Anaconda3\lib\site-packages\pandas\core\series.py in _get_value(self, label, takeable)
        959 
        960         # Similar to Index.get_value, but we do not fall back to positional
    --> 961         loc = self.index.get_loc(label)
        962         return self.index._get_values_for_loc(self, loc, label)
        963 
    

    ~\Anaconda3\lib\site-packages\pandas\core\indexes\base.py in get_loc(self, key, method, tolerance)
       3080                 return self._engine.get_loc(casted_key)
       3081             except KeyError as err:
    -> 3082                 raise KeyError(key) from err
       3083 
       3084         if tolerance is not None:
    

    KeyError: '1'



```python
s2[1:3]
```




    3    b
    5    c
    dtype: object




```python
s2.loc[1:3]
```




    1    a
    3    b
    dtype: object




```python
s2.iloc[1:3]
```




    3    b
    5    c
    dtype: object




```python
ICEdata = pd.read_csv("ICE1_Data.csv")

ICEdata
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
      <th>DBN</th>
      <th>Quality_Review_Score</th>
      <th>Progress_Rpt_10-11</th>
      <th>Student_Progress_10-11</th>
      <th>graduation 2010-11</th>
      <th>college enroll 2010-11</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01M292</td>
      <td>Developing</td>
      <td>C</td>
      <td>C</td>
      <td>0.563</td>
      <td>0.519</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01M448</td>
      <td>Developing</td>
      <td>C</td>
      <td>B</td>
      <td>0.707</td>
      <td>0.363</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01M450</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.716</td>
      <td>0.692</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01M509</td>
      <td>Proficient</td>
      <td>C</td>
      <td>C</td>
      <td>0.564</td>
      <td>0.477</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01M539</td>
      <td>Proficient</td>
      <td>A</td>
      <td>A</td>
      <td>0.953</td>
      <td>0.870</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>417</th>
      <td>10X696</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>A</td>
      <td>1.000</td>
      <td>0.936</td>
    </tr>
    <tr>
      <th>418</th>
      <td>13K430</td>
      <td>Proficient</td>
      <td>B</td>
      <td>B</td>
      <td>0.977</td>
      <td>0.867</td>
    </tr>
    <tr>
      <th>419</th>
      <td>10X445</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>A</td>
      <td>1.000</td>
      <td>0.994</td>
    </tr>
    <tr>
      <th>420</th>
      <td>14K449</td>
      <td>Well Developed</td>
      <td>B</td>
      <td>B</td>
      <td>0.914</td>
      <td>0.961</td>
    </tr>
    <tr>
      <th>421</th>
      <td>28Q687</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>1.000</td>
      <td>0.972</td>
    </tr>
  </tbody>
</table>
<p>422 rows × 6 columns</p>
</div>




```python
ICEdata['Quality_Review_Score']
```




    0          Developing
    1          Developing
    2      Well Developed
    3          Proficient
    4          Proficient
                ...      
    417    Well Developed
    418        Proficient
    419    Well Developed
    420    Well Developed
    421        Proficient
    Name: Quality_Review_Score, Length: 422, dtype: object




```python
ICEdata['collegeRate'] = ICEdata['college enroll 2010-11'] / ICEdata['graduation 2010-11']
ICEdata
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
      <th>DBN</th>
      <th>Quality_Review_Score</th>
      <th>Progress_Rpt_10-11</th>
      <th>Student_Progress_10-11</th>
      <th>graduation 2010-11</th>
      <th>college enroll 2010-11</th>
      <th>collegeRate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01M292</td>
      <td>Developing</td>
      <td>C</td>
      <td>C</td>
      <td>0.563</td>
      <td>0.519</td>
      <td>0.921847</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01M448</td>
      <td>Developing</td>
      <td>C</td>
      <td>B</td>
      <td>0.707</td>
      <td>0.363</td>
      <td>0.513437</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01M450</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.716</td>
      <td>0.692</td>
      <td>0.966480</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01M509</td>
      <td>Proficient</td>
      <td>C</td>
      <td>C</td>
      <td>0.564</td>
      <td>0.477</td>
      <td>0.845745</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01M539</td>
      <td>Proficient</td>
      <td>A</td>
      <td>A</td>
      <td>0.953</td>
      <td>0.870</td>
      <td>0.912907</td>
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
      <th>417</th>
      <td>10X696</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>A</td>
      <td>1.000</td>
      <td>0.936</td>
      <td>0.936000</td>
    </tr>
    <tr>
      <th>418</th>
      <td>13K430</td>
      <td>Proficient</td>
      <td>B</td>
      <td>B</td>
      <td>0.977</td>
      <td>0.867</td>
      <td>0.887410</td>
    </tr>
    <tr>
      <th>419</th>
      <td>10X445</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>A</td>
      <td>1.000</td>
      <td>0.994</td>
      <td>0.994000</td>
    </tr>
    <tr>
      <th>420</th>
      <td>14K449</td>
      <td>Well Developed</td>
      <td>B</td>
      <td>B</td>
      <td>0.914</td>
      <td>0.961</td>
      <td>1.051422</td>
    </tr>
    <tr>
      <th>421</th>
      <td>28Q687</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>1.000</td>
      <td>0.972</td>
      <td>0.972000</td>
    </tr>
  </tbody>
</table>
<p>422 rows × 7 columns</p>
</div>




```python
ICEdata.loc[0]
```




    DBN                           01M292
    Quality_Review_Score      Developing
    Progress_Rpt_10-11                 C
    Student_Progress_10-11             C
    graduation 2010-11             0.563
    college enroll 2010-11         0.519
    collegeRate                 0.921847
    Name: 0, dtype: object




```python
ICEdata.iloc[:3, :2]
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
      <th>DBN</th>
      <th>Quality_Review_Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01M292</td>
      <td>Developing</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01M448</td>
      <td>Developing</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01M450</td>
      <td>Well Developed</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata.loc[:20, :'Progress_Rpt_10-11']
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
      <th>DBN</th>
      <th>Quality_Review_Score</th>
      <th>Progress_Rpt_10-11</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01M292</td>
      <td>Developing</td>
      <td>C</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01M448</td>
      <td>Developing</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01M450</td>
      <td>Well Developed</td>
      <td>A</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01M509</td>
      <td>Proficient</td>
      <td>C</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01M539</td>
      <td>Proficient</td>
      <td>A</td>
    </tr>
    <tr>
      <th>5</th>
      <td>01M696</td>
      <td>Well Developed</td>
      <td>B</td>
    </tr>
    <tr>
      <th>6</th>
      <td>02M047</td>
      <td>Proficient</td>
      <td>C</td>
    </tr>
    <tr>
      <th>7</th>
      <td>02M288</td>
      <td>Proficient</td>
      <td>A</td>
    </tr>
    <tr>
      <th>8</th>
      <td>02M294</td>
      <td>Well Developed</td>
      <td>B</td>
    </tr>
    <tr>
      <th>9</th>
      <td>02M296</td>
      <td>Proficient</td>
      <td>A</td>
    </tr>
    <tr>
      <th>10</th>
      <td>02M298</td>
      <td>Well Developed</td>
      <td>A</td>
    </tr>
    <tr>
      <th>11</th>
      <td>02M300</td>
      <td>Proficient</td>
      <td>B</td>
    </tr>
    <tr>
      <th>12</th>
      <td>02M303</td>
      <td>Proficient</td>
      <td>B</td>
    </tr>
    <tr>
      <th>13</th>
      <td>02M305</td>
      <td>Proficient</td>
      <td>C</td>
    </tr>
    <tr>
      <th>14</th>
      <td>02M308</td>
      <td>Well Developed</td>
      <td>A</td>
    </tr>
    <tr>
      <th>15</th>
      <td>02M316</td>
      <td>Proficient</td>
      <td>B</td>
    </tr>
    <tr>
      <th>16</th>
      <td>02M374</td>
      <td>Proficient</td>
      <td>C</td>
    </tr>
    <tr>
      <th>17</th>
      <td>02M376</td>
      <td>Well Developed</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>02M392</td>
      <td>Proficient</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>02M393</td>
      <td>Proficient</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>02M399</td>
      <td>Proficient</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata[ICEdata['graduation 2010-11'] > 0.75]
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
      <th>DBN</th>
      <th>Quality_Review_Score</th>
      <th>Progress_Rpt_10-11</th>
      <th>Student_Progress_10-11</th>
      <th>graduation 2010-11</th>
      <th>college enroll 2010-11</th>
      <th>collegeRate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>01M539</td>
      <td>Proficient</td>
      <td>A</td>
      <td>A</td>
      <td>0.953</td>
      <td>0.870</td>
      <td>0.912907</td>
    </tr>
    <tr>
      <th>5</th>
      <td>01M696</td>
      <td>Well Developed</td>
      <td>B</td>
      <td>C</td>
      <td>0.976</td>
      <td>0.957</td>
      <td>0.980533</td>
    </tr>
    <tr>
      <th>7</th>
      <td>02M288</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.820</td>
      <td>0.627</td>
      <td>0.764634</td>
    </tr>
    <tr>
      <th>9</th>
      <td>02M296</td>
      <td>Proficient</td>
      <td>A</td>
      <td>A</td>
      <td>0.793</td>
      <td>0.560</td>
      <td>0.706179</td>
    </tr>
    <tr>
      <th>10</th>
      <td>02M298</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>A</td>
      <td>0.915</td>
      <td>0.796</td>
      <td>0.869945</td>
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
      <th>417</th>
      <td>10X696</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>A</td>
      <td>1.000</td>
      <td>0.936</td>
      <td>0.936000</td>
    </tr>
    <tr>
      <th>418</th>
      <td>13K430</td>
      <td>Proficient</td>
      <td>B</td>
      <td>B</td>
      <td>0.977</td>
      <td>0.867</td>
      <td>0.887410</td>
    </tr>
    <tr>
      <th>419</th>
      <td>10X445</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>A</td>
      <td>1.000</td>
      <td>0.994</td>
      <td>0.994000</td>
    </tr>
    <tr>
      <th>420</th>
      <td>14K449</td>
      <td>Well Developed</td>
      <td>B</td>
      <td>B</td>
      <td>0.914</td>
      <td>0.961</td>
      <td>1.051422</td>
    </tr>
    <tr>
      <th>421</th>
      <td>28Q687</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>1.000</td>
      <td>0.972</td>
      <td>0.972000</td>
    </tr>
  </tbody>
</table>
<p>135 rows × 7 columns</p>
</div>




```python
m2
```




    array([[9, 0, 0, 9],
           [3, 4, 0, 0],
           [4, 1, 7, 3]])




```python
m2 < 2
```




    array([[False,  True,  True, False],
           [False, False,  True,  True],
           [False,  True, False, False]])




```python
m2[m2 < 2]
```




    array([0, 0, 0, 0, 1])




```python
mask = (m2 > 2) & (m2 <5)
m2[mask]
```




    array([3, 4, 4, 3])




```python
ICEmask = (ICEdata['graduation 2010-11'] > 0.75) & (ICEdata['Progress_Rpt_10-11'] == 'A') & (ICEdata['Student_Progress_10-11'] == 'B')
ICEdata[ICEmask]
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
      <th>DBN</th>
      <th>Quality_Review_Score</th>
      <th>Progress_Rpt_10-11</th>
      <th>Student_Progress_10-11</th>
      <th>graduation 2010-11</th>
      <th>college enroll 2010-11</th>
      <th>collegeRate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7</th>
      <td>02M288</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.820</td>
      <td>0.627</td>
      <td>0.764634</td>
    </tr>
    <tr>
      <th>25</th>
      <td>02M412</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.964</td>
      <td>0.774</td>
      <td>0.802905</td>
    </tr>
    <tr>
      <th>75</th>
      <td>04M435</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.920</td>
      <td>0.757</td>
      <td>0.822826</td>
    </tr>
    <tr>
      <th>78</th>
      <td>04M610</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.984</td>
      <td>0.982</td>
      <td>0.997967</td>
    </tr>
    <tr>
      <th>85</th>
      <td>05M670</td>
      <td>Developing</td>
      <td>A</td>
      <td>B</td>
      <td>0.789</td>
      <td>0.559</td>
      <td>0.708492</td>
    </tr>
    <tr>
      <th>107</th>
      <td>07X548</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.866</td>
      <td>0.663</td>
      <td>0.765589</td>
    </tr>
    <tr>
      <th>108</th>
      <td>07X551</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.831</td>
      <td>0.605</td>
      <td>0.728039</td>
    </tr>
    <tr>
      <th>147</th>
      <td>09X543</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.765</td>
      <td>0.319</td>
      <td>0.416993</td>
    </tr>
    <tr>
      <th>149</th>
      <td>10X141</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.870</td>
      <td>0.784</td>
      <td>0.901149</td>
    </tr>
    <tr>
      <th>158</th>
      <td>10X374</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.939</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>161</th>
      <td>10X437</td>
      <td>Developing</td>
      <td>A</td>
      <td>B</td>
      <td>0.855</td>
      <td>0.325</td>
      <td>0.380117</td>
    </tr>
    <tr>
      <th>175</th>
      <td>11X275</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.762</td>
      <td>0.517</td>
      <td>0.678478</td>
    </tr>
    <tr>
      <th>206</th>
      <td>13K419</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.802</td>
      <td>0.399</td>
      <td>0.497506</td>
    </tr>
    <tr>
      <th>220</th>
      <td>14K478</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.847</td>
      <td>0.432</td>
      <td>0.510035</td>
    </tr>
    <tr>
      <th>251</th>
      <td>17K531</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.787</td>
      <td>0.433</td>
      <td>0.550191</td>
    </tr>
    <tr>
      <th>274</th>
      <td>19K404</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.855</td>
      <td>0.538</td>
      <td>0.629240</td>
    </tr>
    <tr>
      <th>305</th>
      <td>22K535</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.958</td>
      <td>0.862</td>
      <td>0.899791</td>
    </tr>
    <tr>
      <th>308</th>
      <td>23K514</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.769</td>
      <td>0.467</td>
      <td>0.607282</td>
    </tr>
    <tr>
      <th>334</th>
      <td>26Q430</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.875</td>
      <td>0.680</td>
      <td>0.777143</td>
    </tr>
    <tr>
      <th>336</th>
      <td>26Q495</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.862</td>
      <td>0.745</td>
      <td>0.864269</td>
    </tr>
    <tr>
      <th>356</th>
      <td>28Q440</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.844</td>
      <td>0.649</td>
      <td>0.768957</td>
    </tr>
    <tr>
      <th>357</th>
      <td>28Q505</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.756</td>
      <td>0.529</td>
      <td>0.699735</td>
    </tr>
    <tr>
      <th>358</th>
      <td>28Q620</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.877</td>
      <td>0.697</td>
      <td>0.794755</td>
    </tr>
    <tr>
      <th>383</th>
      <td>31R080</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>0.866</td>
      <td>0.817</td>
      <td>0.943418</td>
    </tr>
    <tr>
      <th>384</th>
      <td>31R440</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.756</td>
      <td>0.473</td>
      <td>0.625661</td>
    </tr>
    <tr>
      <th>413</th>
      <td>03M485</td>
      <td>Outstanding (only an option in 2007-8)</td>
      <td>A</td>
      <td>B</td>
      <td>0.982</td>
      <td>0.861</td>
      <td>0.876782</td>
    </tr>
    <tr>
      <th>415</th>
      <td>02M475</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.985</td>
      <td>0.854</td>
      <td>0.867005</td>
    </tr>
    <tr>
      <th>416</th>
      <td>05M692</td>
      <td>Well Developed</td>
      <td>A</td>
      <td>B</td>
      <td>0.982</td>
      <td>0.934</td>
      <td>0.951120</td>
    </tr>
    <tr>
      <th>421</th>
      <td>28Q687</td>
      <td>Proficient</td>
      <td>A</td>
      <td>B</td>
      <td>1.000</td>
      <td>0.972</td>
      <td>0.972000</td>
    </tr>
  </tbody>
</table>
</div>




```python
def make_df(cols, ind):
    data = {c: [str(c) + str(i) for i in ind]
            for c in cols}
    return pd.DataFrame(data, ind)

make_df('ABC', range(3))
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A0</td>
      <td>B0</td>
      <td>C0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A1</td>
      <td>B1</td>
      <td>C1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>A2</td>
      <td>B2</td>
      <td>C2</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = make_df('AB', [1, 2])
df2 = make_df('AB', [3, 4])
print(df1, "\n\n\n")
print(df2, "\n\n\n")
print(pd.concat([df1, df2]))
```

        A   B
    1  A1  B1
    2  A2  B2 
    
    
    
        A   B
    3  A3  B3
    4  A4  B4 
    
    
    
        A   B
    1  A1  B1
    2  A2  B2
    3  A3  B3
    4  A4  B4
    


```python
df3 = make_df('ABC', [1, 2])
df4 = make_df('BCD', [3, 4])
print(df3, "\n\n\n")
print(df4, "\n\n\n")
print(pd.concat([df3, df4]))
```

        A   B   C
    1  A1  B1  C1
    2  A2  B2  C2 
    
    
    
        B   C   D
    3  B3  C3  D3
    4  B4  C4  D4 
    
    
    
         A   B   C    D
    1   A1  B1  C1  NaN
    2   A2  B2  C2  NaN
    3  NaN  B3  C3   D3
    4  NaN  B4  C4   D4
    


```python
pd.concat([df3, df4], join = 'inner')
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
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>B1</td>
      <td>C1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>B2</td>
      <td>C2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>B3</td>
      <td>C3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>B4</td>
      <td>C4</td>
    </tr>
  </tbody>
</table>
</div>




```python
df5 = pd.DataFrame({'employee': ['Bob', 'Jake', 'Lisa', 'Sue'],
                    'group': ['Accounting', 'Engineering', 'Engineering', 'HR']})
df6 = pd.DataFrame({'employee': ['Lisa', 'Bob', 'Jake', 'Sue'],
                    'hire_date': [2004, 2008, 2012, 2014]})
dfm = pd.merge(df5, df6)

print(df5, "\n\n\n")
print(df6, "\n\n\n")
print(dfm)
```

      employee        group
    0      Bob   Accounting
    1     Jake  Engineering
    2     Lisa  Engineering
    3      Sue           HR 
    
    
    
      employee  hire_date
    0     Lisa       2004
    1      Bob       2008
    2     Jake       2012
    3      Sue       2014 
    
    
    
      employee        group  hire_date
    0      Bob   Accounting       2008
    1     Jake  Engineering       2012
    2     Lisa  Engineering       2004
    3      Sue           HR       2014
    


```python
df7 = pd.DataFrame({'group': ['Accounting', 'Engineering', 'HR'],
                    'supervisor': ['Carly', 'Guido', 'Steve']})

dfm = pd.merge(df5, df7)
print(df7, "\n\n\n")

print(dfm)
```

             group supervisor
    0   Accounting      Carly
    1  Engineering      Guido
    2           HR      Steve 
    
    
    
      employee        group supervisor
    0      Bob   Accounting      Carly
    1     Jake  Engineering      Guido
    2     Lisa  Engineering      Guido
    3      Sue           HR      Steve
    


```python
pd.merge(df5, df6, on='employee')
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
      <th>employee</th>
      <th>group</th>
      <th>hire_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bob</td>
      <td>Accounting</td>
      <td>2008</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jake</td>
      <td>Engineering</td>
      <td>2012</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Lisa</td>
      <td>Engineering</td>
      <td>2004</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Sue</td>
      <td>HR</td>
      <td>2014</td>
    </tr>
  </tbody>
</table>
</div>




```python
df8 = pd.DataFrame({'name': ['Bob', 'Jake', 'Lisa', 'Sue'],
                    'salary': [70000, 80000, 120000, 90000]})
pd.merge(df5, df8, left_on = 'employee', right_on = 'name')
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
      <th>employee</th>
      <th>group</th>
      <th>name</th>
      <th>salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bob</td>
      <td>Accounting</td>
      <td>Bob</td>
      <td>70000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jake</td>
      <td>Engineering</td>
      <td>Jake</td>
      <td>80000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Lisa</td>
      <td>Engineering</td>
      <td>Lisa</td>
      <td>120000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Sue</td>
      <td>HR</td>
      <td>Sue</td>
      <td>90000</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(df5, df8, left_on = 'employee', right_on = 'name').drop('name', axis=1)
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
      <th>employee</th>
      <th>group</th>
      <th>salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bob</td>
      <td>Accounting</td>
      <td>70000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jake</td>
      <td>Engineering</td>
      <td>80000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Lisa</td>
      <td>Engineering</td>
      <td>120000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Sue</td>
      <td>HR</td>
      <td>90000</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata.describe(include = 'all')
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
      <th>DBN</th>
      <th>Quality_Review_Score</th>
      <th>Progress_Rpt_10-11</th>
      <th>Student_Progress_10-11</th>
      <th>graduation 2010-11</th>
      <th>college enroll 2010-11</th>
      <th>collegeRate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>422</td>
      <td>368</td>
      <td>310</td>
      <td>310</td>
      <td>310.000000</td>
      <td>291.000000</td>
      <td>291.000000</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>422</td>
      <td>6</td>
      <td>5</td>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>top</th>
      <td>13K265</td>
      <td>Proficient</td>
      <td>A</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>1</td>
      <td>186</td>
      <td>109</td>
      <td>93</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.737977</td>
      <td>0.531196</td>
      <td>0.707836</td>
    </tr>
    <tr>
      <th>std</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.143356</td>
      <td>0.193129</td>
      <td>0.168986</td>
    </tr>
    <tr>
      <th>min</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.412000</td>
      <td>0.141000</td>
      <td>0.262570</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.625250</td>
      <td>0.391000</td>
      <td>0.589317</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.726000</td>
      <td>0.489000</td>
      <td>0.707569</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.850750</td>
      <td>0.656000</td>
      <td>0.838918</td>
    </tr>
    <tr>
      <th>max</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.101227</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata.mean()
```




    graduation 2010-11        0.737977
    college enroll 2010-11    0.531196
    collegeRate               0.707836
    dtype: float64




```python
ICEdata['graduation 2010-11'].max()
```




    1.0




```python
ICEdata.groupby('Quality_Review_Score')
```




    <pandas.core.groupby.generic.DataFrameGroupBy object at 0x00000261C53001C0>




```python
ICEdata.groupby('Quality_Review_Score').mean()
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
      <th>graduation 2010-11</th>
      <th>college enroll 2010-11</th>
      <th>collegeRate</th>
    </tr>
    <tr>
      <th>Quality_Review_Score</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Developing</th>
      <td>0.633019</td>
      <td>0.402830</td>
      <td>0.641309</td>
    </tr>
    <tr>
      <th>Outstanding (only an option in 2007-8)</th>
      <td>0.864333</td>
      <td>0.747667</td>
      <td>0.864183</td>
    </tr>
    <tr>
      <th>Proficient</th>
      <td>0.729554</td>
      <td>0.521208</td>
      <td>0.703604</td>
    </tr>
    <tr>
      <th>Underdeveloped</th>
      <td>0.549667</td>
      <td>0.350167</td>
      <td>0.631451</td>
    </tr>
    <tr>
      <th>Underdeveloped with Proficient Features (only an option in 2007-8, 2008-9 and 2009-10)</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Well Developed</th>
      <td>0.823367</td>
      <td>0.625871</td>
      <td>0.752696</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata.groupby('Quality_Review_Score')['graduation 2010-11'].describe()
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
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>Quality_Review_Score</th>
      <th></th>
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
      <th>Developing</th>
      <td>53.0</td>
      <td>0.633019</td>
      <td>0.107199</td>
      <td>0.457</td>
      <td>0.56300</td>
      <td>0.615</td>
      <td>0.69800</td>
      <td>0.947</td>
    </tr>
    <tr>
      <th>Outstanding (only an option in 2007-8)</th>
      <td>3.0</td>
      <td>0.864333</td>
      <td>0.102051</td>
      <td>0.800</td>
      <td>0.80550</td>
      <td>0.811</td>
      <td>0.89650</td>
      <td>0.982</td>
    </tr>
    <tr>
      <th>Proficient</th>
      <td>157.0</td>
      <td>0.729554</td>
      <td>0.135946</td>
      <td>0.412</td>
      <td>0.63000</td>
      <td>0.722</td>
      <td>0.81100</td>
      <td>1.000</td>
    </tr>
    <tr>
      <th>Underdeveloped</th>
      <td>6.0</td>
      <td>0.549667</td>
      <td>0.061805</td>
      <td>0.457</td>
      <td>0.51525</td>
      <td>0.554</td>
      <td>0.59350</td>
      <td>0.624</td>
    </tr>
    <tr>
      <th>Underdeveloped with Proficient Features (only an option in 2007-8, 2008-9 and 2009-10)</th>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Well Developed</th>
      <td>90.0</td>
      <td>0.823367</td>
      <td>0.121570</td>
      <td>0.545</td>
      <td>0.72775</td>
      <td>0.833</td>
      <td>0.91875</td>
      <td>1.000</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata.groupby(['Quality_Review_Score', 'Progress_Rpt_10-11']).count().unstack()
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
      <th colspan="5" halign="left">DBN</th>
      <th colspan="5" halign="left">Student_Progress_10-11</th>
      <th>...</th>
      <th colspan="5" halign="left">college enroll 2010-11</th>
      <th colspan="5" halign="left">collegeRate</th>
    </tr>
    <tr>
      <th>Progress_Rpt_10-11</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>...</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
    <tr>
      <th>Quality_Review_Score</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
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
      <th>Developing</th>
      <td>4.0</td>
      <td>11.0</td>
      <td>19.0</td>
      <td>16.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>11.0</td>
      <td>19.0</td>
      <td>16.0</td>
      <td>3.0</td>
      <td>...</td>
      <td>3.0</td>
      <td>11.0</td>
      <td>16.0</td>
      <td>15.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>11.0</td>
      <td>16.0</td>
      <td>15.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>Outstanding (only an option in 2007-8)</th>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Proficient</th>
      <td>48.0</td>
      <td>65.0</td>
      <td>39.0</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>48.0</td>
      <td>65.0</td>
      <td>39.0</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>45.0</td>
      <td>63.0</td>
      <td>37.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>45.0</td>
      <td>63.0</td>
      <td>37.0</td>
      <td>4.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Underdeveloped</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>Well Developed</th>
      <td>53.0</td>
      <td>26.0</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>53.0</td>
      <td>26.0</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>48.0</td>
      <td>26.0</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>48.0</td>
      <td>26.0</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 25 columns</p>
</div>




```python
ICEdata.groupby('Quality_Review_Score').aggregate(['median', 'min', 'max'])
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
      <th colspan="3" halign="left">graduation 2010-11</th>
      <th colspan="3" halign="left">college enroll 2010-11</th>
      <th colspan="3" halign="left">collegeRate</th>
    </tr>
    <tr>
      <th></th>
      <th>median</th>
      <th>min</th>
      <th>max</th>
      <th>median</th>
      <th>min</th>
      <th>max</th>
      <th>median</th>
      <th>min</th>
      <th>max</th>
    </tr>
    <tr>
      <th>Quality_Review_Score</th>
      <th></th>
      <th></th>
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
      <th>Developing</th>
      <td>0.615</td>
      <td>0.457</td>
      <td>0.947</td>
      <td>0.4030</td>
      <td>0.165</td>
      <td>0.658</td>
      <td>0.647416</td>
      <td>0.271829</td>
      <td>1.048622</td>
    </tr>
    <tr>
      <th>Outstanding (only an option in 2007-8)</th>
      <td>0.811</td>
      <td>0.800</td>
      <td>0.982</td>
      <td>0.6920</td>
      <td>0.690</td>
      <td>0.861</td>
      <td>0.862500</td>
      <td>0.853268</td>
      <td>0.876782</td>
    </tr>
    <tr>
      <th>Proficient</th>
      <td>0.722</td>
      <td>0.412</td>
      <td>1.000</td>
      <td>0.4900</td>
      <td>0.183</td>
      <td>0.990</td>
      <td>0.699735</td>
      <td>0.296503</td>
      <td>1.101227</td>
    </tr>
    <tr>
      <th>Underdeveloped</th>
      <td>0.554</td>
      <td>0.457</td>
      <td>0.624</td>
      <td>0.3715</td>
      <td>0.141</td>
      <td>0.465</td>
      <td>0.712859</td>
      <td>0.262570</td>
      <td>0.756567</td>
    </tr>
    <tr>
      <th>Underdeveloped with Proficient Features (only an option in 2007-8, 2008-9 and 2009-10)</th>
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
    <tr>
      <th>Well Developed</th>
      <td>0.833</td>
      <td>0.545</td>
      <td>1.000</td>
      <td>0.5920</td>
      <td>0.268</td>
      <td>1.000</td>
      <td>0.765269</td>
      <td>0.388970</td>
      <td>1.051422</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata.groupby(['Quality_Review_Score', 'Progress_Rpt_10-11'])['graduation 2010-11'].aggregate('mean').unstack()
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
      <th>Progress_Rpt_10-11</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
    <tr>
      <th>Quality_Review_Score</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Developing</th>
      <td>0.716500</td>
      <td>0.654545</td>
      <td>0.639474</td>
      <td>0.613812</td>
      <td>0.504333</td>
    </tr>
    <tr>
      <th>Outstanding (only an option in 2007-8)</th>
      <td>0.864333</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Proficient</th>
      <td>0.817083</td>
      <td>0.722077</td>
      <td>0.660333</td>
      <td>0.526400</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Underdeveloped</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.556333</td>
      <td>0.457000</td>
      <td>0.586000</td>
    </tr>
    <tr>
      <th>Well Developed</th>
      <td>0.862472</td>
      <td>0.791000</td>
      <td>0.711455</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata.pivot_table('graduation 2010-11', index='Quality_Review_Score', columns='Progress_Rpt_10-11')
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
      <th>Progress_Rpt_10-11</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
    <tr>
      <th>Quality_Review_Score</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Developing</th>
      <td>0.716500</td>
      <td>0.654545</td>
      <td>0.639474</td>
      <td>0.613812</td>
      <td>0.504333</td>
    </tr>
    <tr>
      <th>Outstanding (only an option in 2007-8)</th>
      <td>0.864333</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Proficient</th>
      <td>0.817083</td>
      <td>0.722077</td>
      <td>0.660333</td>
      <td>0.526400</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Underdeveloped</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.556333</td>
      <td>0.457000</td>
      <td>0.586000</td>
    </tr>
    <tr>
      <th>Well Developed</th>
      <td>0.862472</td>
      <td>0.791000</td>
      <td>0.711455</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
ICEdata.pivot_table('graduation 2010-11',
                    index='Quality_Review_Score',
                    columns='Progress_Rpt_10-11',
                   aggfunc = 'median')
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
      <th>Progress_Rpt_10-11</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>F</th>
    </tr>
    <tr>
      <th>Quality_Review_Score</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Developing</th>
      <td>0.702</td>
      <td>0.6290</td>
      <td>0.587</td>
      <td>0.615</td>
      <td>0.506</td>
    </tr>
    <tr>
      <th>Outstanding (only an option in 2007-8)</th>
      <td>0.811</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Proficient</th>
      <td>0.806</td>
      <td>0.7150</td>
      <td>0.662</td>
      <td>0.531</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Underdeveloped</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.537</td>
      <td>0.457</td>
      <td>0.586</td>
    </tr>
    <tr>
      <th>Well Developed</th>
      <td>0.879</td>
      <td>0.8145</td>
      <td>0.676</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


