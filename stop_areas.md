```python
import pandas as pd
import numpy as np
```


```python
df304 = pd.read_csv(r"C:\Users\Jonas\Desktop\New folder\DSML_Project\Locations304.csv")
```


```python
df304.head()
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
      <th>@id</th>
      <th>@type</th>
      <th>@lat</th>
      <th>@lon</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2330248</td>
      <td>relation</td>
      <td>52.246945</td>
      <td>13.898032</td>
      <td>Philadelphia, Kreuzung</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2629927</td>
      <td>relation</td>
      <td>39.989910</td>
      <td>-75.249792</td>
      <td>Overbrook</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4744254</td>
      <td>relation</td>
      <td>39.956077</td>
      <td>-75.182208</td>
      <td>Philadelphia 30th Street Station</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7929726</td>
      <td>relation</td>
      <td>39.905348</td>
      <td>-75.173152</td>
      <td>NRG</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7929727</td>
      <td>relation</td>
      <td>39.951122</td>
      <td>-75.197078</td>
      <td>37th Street</td>
    </tr>
  </tbody>
</table>
</div>




```python
df121 = pd.read_csv(r"C:\Users\Jonas\Desktop\New folder\DSML_Project\Locations121.csv")
```

Fill missing values in both datasets with NaN


```python
merged_df = pd.merge(df304, df121, how='outer')
```


```python
merged_df.count()
```




    @id      422
    @type    422
    @lat     422
    @lon     422
    name     422
    dtype: int64



Drop duplicates in merged dataframe


```python
merged_df = merged_df.drop_duplicates()
```


```python
merged_df.nunique()
```




    @id      423
    @type      3
    @lat     421
    @lon     419
    name     317
    dtype: int64




```python
merged_df.dropna(how ='any', inplace=True)
```


```python
merged_df.count()
```




    @id      422
    @type    422
    @lat     422
    @lon     422
    name     422
    dtype: int64




```python
merged_df2 = pd.merge(df304, df121, on='name')
```


```python
filtered_df = merged_df.drop_duplicates(subset='name')
```


```python
filtered_df.count()
```




    @id      317
    @type    317
    @lat     317
    @lon     317
    name     317
    dtype: int64




```python
filtered_df.nunique()
```




    @id      317
    @type      3
    @lat     317
    @lon     317
    name     317
    dtype: int64




```python
merged_df2.count()
```




    @id_x      98
    @type_x    98
    @lat_x     98
    @lon_x     98
    name       98
    @id_y      98
    @type_y    98
    @lat_y     98
    @lon_y     98
    dtype: int64




```python
filtered_df.to_csv('stop_areas.csv', index=True)
```


```python

```
