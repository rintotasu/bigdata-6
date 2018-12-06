# Pertemuan minggu ke 11
## Pandas Cookbook Bagian 3



```python
import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50
```


```python
college = pd.read_csv('data/college.csv')
```


```python
college.head()
```

### Hasil dari Source code diatas



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
      <th>INSTNM</th>
      <th>CITY</th>
      <th>STABBR</th>
      <th>HBCU</th>
      <th>MENONLY</th>
      <th>WOMENONLY</th>
      <th>RELAFFIL</th>
      <th>SATVRMID</th>
      <th>SATMTMID</th>
      <th>DISTANCEONLY</th>
      <th>UGDS</th>
      <th>UGDS_WHITE</th>
      <th>UGDS_BLACK</th>
      <th>UGDS_HISP</th>
      <th>UGDS_ASIAN</th>
      <th>UGDS_AIAN</th>
      <th>UGDS_NHPI</th>
      <th>UGDS_2MOR</th>
      <th>UGDS_NRA</th>
      <th>UGDS_UNKN</th>
      <th>PPTUG_EF</th>
      <th>CURROPER</th>
      <th>PCTPELL</th>
      <th>PCTFLOAN</th>
      <th>UG25ABV</th>
      <th>MD_EARN_WNE_P10</th>
      <th>GRAD_DEBT_MDN_SUPP</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alabama A &amp; M University</td>
      <td>Normal</td>
      <td>AL</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>424.0</td>
      <td>420.0</td>
      <td>0.0</td>
      <td>4206.0</td>
      <td>0.0333</td>
      <td>0.9353</td>
      <td>0.0055</td>
      <td>0.0019</td>
      <td>0.0024</td>
      <td>0.0019</td>
      <td>0.0000</td>
      <td>0.0059</td>
      <td>0.0138</td>
      <td>0.0656</td>
      <td>1</td>
      <td>0.7356</td>
      <td>0.8284</td>
      <td>0.1049</td>
      <td>30300</td>
      <td>33888</td>
    </tr>
    <tr>
      <th>1</th>
      <td>University of Alabama at Birmingham</td>
      <td>Birmingham</td>
      <td>AL</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>570.0</td>
      <td>565.0</td>
      <td>0.0</td>
      <td>11383.0</td>
      <td>0.5922</td>
      <td>0.2600</td>
      <td>0.0283</td>
      <td>0.0518</td>
      <td>0.0022</td>
      <td>0.0007</td>
      <td>0.0368</td>
      <td>0.0179</td>
      <td>0.0100</td>
      <td>0.2607</td>
      <td>1</td>
      <td>0.3460</td>
      <td>0.5214</td>
      <td>0.2422</td>
      <td>39700</td>
      <td>21941.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Amridge University</td>
      <td>Montgomery</td>
      <td>AL</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>291.0</td>
      <td>0.2990</td>
      <td>0.4192</td>
      <td>0.0069</td>
      <td>0.0034</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.2715</td>
      <td>0.4536</td>
      <td>1</td>
      <td>0.6801</td>
      <td>0.7795</td>
      <td>0.8540</td>
      <td>40100</td>
      <td>23370</td>
    </tr>
    <tr>
      <th>3</th>
      <td>University of Alabama in Huntsville</td>
      <td>Huntsville</td>
      <td>AL</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>595.0</td>
      <td>590.0</td>
      <td>0.0</td>
      <td>5451.0</td>
      <td>0.6988</td>
      <td>0.1255</td>
      <td>0.0382</td>
      <td>0.0376</td>
      <td>0.0143</td>
      <td>0.0002</td>
      <td>0.0172</td>
      <td>0.0332</td>
      <td>0.0350</td>
      <td>0.2146</td>
      <td>1</td>
      <td>0.3072</td>
      <td>0.4596</td>
      <td>0.2640</td>
      <td>45500</td>
      <td>24097</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alabama State University</td>
      <td>Montgomery</td>
      <td>AL</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>425.0</td>
      <td>430.0</td>
      <td>0.0</td>
      <td>4811.0</td>
      <td>0.0158</td>
      <td>0.9208</td>
      <td>0.0121</td>
      <td>0.0019</td>
      <td>0.0010</td>
      <td>0.0006</td>
      <td>0.0098</td>
      <td>0.0243</td>
      <td>0.0137</td>
      <td>0.0892</td>
      <td>1</td>
      <td>0.7347</td>
      <td>0.7554</td>
      <td>0.1270</td>
      <td>26600</td>
      <td>33118.5</td>
    </tr>
  </tbody>
</table>
</div>




```python

```



```python
import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50
```


```python
college = pd.read_csv('data/college.csv')
```


```python
college.shape
```

### Hasil dari Source Code Diatas



    (7535, 27)




```python

```


```python
import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50
```


```python
college = pd.read_csv('data/college.csv')
```


```python
with pd.option_context('display.max_rows', 8):
    display(college.describe(include=[np.number]).T)
```
### Hasil dari source code diatas

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
  </thead>
  <tbody>
    <tr>
      <th>HBCU</th>
      <td>7164.0</td>
      <td>0.014238</td>
      <td>0.118478</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>MENONLY</th>
      <td>7164.0</td>
      <td>0.009213</td>
      <td>0.095546</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>WOMENONLY</th>
      <td>7164.0</td>
      <td>0.005304</td>
      <td>0.072642</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>RELAFFIL</th>
      <td>7535.0</td>
      <td>0.190975</td>
      <td>0.393096</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0</td>
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
      <td>...</td>
    </tr>
    <tr>
      <th>CURROPER</th>
      <td>7535.0</td>
      <td>0.923291</td>
      <td>0.266146</td>
      <td>0.0</td>
      <td>1.0000</td>
      <td>1.00000</td>
      <td>1.000000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>PCTPELL</th>
      <td>6849.0</td>
      <td>0.530643</td>
      <td>0.225544</td>
      <td>0.0</td>
      <td>0.3578</td>
      <td>0.52150</td>
      <td>0.712900</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>PCTFLOAN</th>
      <td>6849.0</td>
      <td>0.522211</td>
      <td>0.283616</td>
      <td>0.0</td>
      <td>0.3329</td>
      <td>0.58330</td>
      <td>0.745000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>UG25ABV</th>
      <td>6718.0</td>
      <td>0.410021</td>
      <td>0.228939</td>
      <td>0.0</td>
      <td>0.2415</td>
      <td>0.40075</td>
      <td>0.572275</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
<p>22 rows × 8 columns</p>
</div>



```python

```



```python
import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50
```


```python
college = pd.read_csv('data/college.csv')
```


```python
college.describe(include=[np.object, pd.Categorical]).T
```

### Hasil dari source code diatas


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
      <th>unique</th>
      <th>top</th>
      <th>freq</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>INSTNM</th>
      <td>7535</td>
      <td>7535</td>
      <td>Herkimer County BOCES-Practical Nursing Program</td>
      <td>1</td>
    </tr>
    <tr>
      <th>CITY</th>
      <td>7535</td>
      <td>2514</td>
      <td>New York</td>
      <td>87</td>
    </tr>
    <tr>
      <th>STABBR</th>
      <td>7535</td>
      <td>59</td>
      <td>CA</td>
      <td>773</td>
    </tr>
    <tr>
      <th>MD_EARN_WNE_P10</th>
      <td>6413</td>
      <td>598</td>
      <td>PrivacySuppressed</td>
      <td>822</td>
    </tr>
    <tr>
      <th>GRAD_DEBT_MDN_SUPP</th>
      <td>7503</td>
      <td>2038</td>
      <td>PrivacySuppressed</td>
      <td>1510</td>
    </tr>
  </tbody>
</table>
</div>




```python

```



```python
import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50
```


```python
college = pd.read_csv('data/college.csv')
```


```python
college.describe(include=[np.number]).T
```

### Hasil dari source code diatas


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
  </thead>
  <tbody>
    <tr>
      <th>HBCU</th>
      <td>7164.0</td>
      <td>0.014238</td>
      <td>0.118478</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>MENONLY</th>
      <td>7164.0</td>
      <td>0.009213</td>
      <td>0.095546</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>WOMENONLY</th>
      <td>7164.0</td>
      <td>0.005304</td>
      <td>0.072642</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>RELAFFIL</th>
      <td>7535.0</td>
      <td>0.190975</td>
      <td>0.393096</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>SATVRMID</th>
      <td>1185.0</td>
      <td>522.819409</td>
      <td>68.578862</td>
      <td>290.0</td>
      <td>475.000000</td>
      <td>510.00000</td>
      <td>555.000000</td>
      <td>765.0000</td>
    </tr>
    <tr>
      <th>SATMTMID</th>
      <td>1196.0</td>
      <td>530.765050</td>
      <td>73.469767</td>
      <td>310.0</td>
      <td>482.000000</td>
      <td>520.00000</td>
      <td>565.000000</td>
      <td>785.0000</td>
    </tr>
    <tr>
      <th>DISTANCEONLY</th>
      <td>7164.0</td>
      <td>0.005583</td>
      <td>0.074519</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>UGDS</th>
      <td>6874.0</td>
      <td>2356.837940</td>
      <td>5474.275871</td>
      <td>0.0</td>
      <td>117.000000</td>
      <td>412.50000</td>
      <td>1929.500000</td>
      <td>151558.0000</td>
    </tr>
    <tr>
      <th>UGDS_WHITE</th>
      <td>6874.0</td>
      <td>0.510207</td>
      <td>0.286958</td>
      <td>0.0</td>
      <td>0.267500</td>
      <td>0.55570</td>
      <td>0.747875</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>UGDS_BLACK</th>
      <td>6874.0</td>
      <td>0.189997</td>
      <td>0.224587</td>
      <td>0.0</td>
      <td>0.036125</td>
      <td>0.10005</td>
      <td>0.257700</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>UGDS_HISP</th>
      <td>6874.0</td>
      <td>0.161635</td>
      <td>0.221854</td>
      <td>0.0</td>
      <td>0.027600</td>
      <td>0.07140</td>
      <td>0.198875</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>UGDS_ASIAN</th>
      <td>6874.0</td>
      <td>0.033544</td>
      <td>0.073777</td>
      <td>0.0</td>
      <td>0.002500</td>
      <td>0.01290</td>
      <td>0.032700</td>
      <td>0.9727</td>
    </tr>
    <tr>
      <th>UGDS_AIAN</th>
      <td>6874.0</td>
      <td>0.013813</td>
      <td>0.070196</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.00260</td>
      <td>0.007300</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>UGDS_NHPI</th>
      <td>6874.0</td>
      <td>0.004569</td>
      <td>0.033125</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.002500</td>
      <td>0.9983</td>
    </tr>
    <tr>
      <th>UGDS_2MOR</th>
      <td>6874.0</td>
      <td>0.023950</td>
      <td>0.031288</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.01750</td>
      <td>0.033900</td>
      <td>0.5333</td>
    </tr>
    <tr>
      <th>UGDS_NRA</th>
      <td>6874.0</td>
      <td>0.016086</td>
      <td>0.050172</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.011700</td>
      <td>0.9286</td>
    </tr>
    <tr>
      <th>UGDS_UNKN</th>
      <td>6874.0</td>
      <td>0.045181</td>
      <td>0.093440</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.01430</td>
      <td>0.045400</td>
      <td>0.9027</td>
    </tr>
    <tr>
      <th>PPTUG_EF</th>
      <td>6853.0</td>
      <td>0.226639</td>
      <td>0.246470</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.15040</td>
      <td>0.376900</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>CURROPER</th>
      <td>7535.0</td>
      <td>0.923291</td>
      <td>0.266146</td>
      <td>0.0</td>
      <td>1.000000</td>
      <td>1.00000</td>
      <td>1.000000</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>PCTPELL</th>
      <td>6849.0</td>
      <td>0.530643</td>
      <td>0.225544</td>
      <td>0.0</td>
      <td>0.357800</td>
      <td>0.52150</td>
      <td>0.712900</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>PCTFLOAN</th>
      <td>6849.0</td>
      <td>0.522211</td>
      <td>0.283616</td>
      <td>0.0</td>
      <td>0.332900</td>
      <td>0.58330</td>
      <td>0.745000</td>
      <td>1.0000</td>
    </tr>
    <tr>
      <th>UG25ABV</th>
      <td>6718.0</td>
      <td>0.410021</td>
      <td>0.228939</td>
      <td>0.0</td>
      <td>0.241500</td>
      <td>0.40075</td>
      <td>0.572275</td>
      <td>1.0000</td>
    </tr>
  </tbody>
</table>
</div>




```python

```



```python
import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50
```


```python
college = pd.read_csv('data/college.csv')
```


```python
college.describe(include=[np.object, pd.Categorical]).T
```


### Hasil dari source code diatas

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
      <th>unique</th>
      <th>top</th>
      <th>freq</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>INSTNM</th>
      <td>7535</td>
      <td>7535</td>
      <td>Herkimer County BOCES-Practical Nursing Program</td>
      <td>1</td>
    </tr>
    <tr>
      <th>CITY</th>
      <td>7535</td>
      <td>2514</td>
      <td>New York</td>
      <td>87</td>
    </tr>
    <tr>
      <th>STABBR</th>
      <td>7535</td>
      <td>59</td>
      <td>CA</td>
      <td>773</td>
    </tr>
    <tr>
      <th>MD_EARN_WNE_P10</th>
      <td>6413</td>
      <td>598</td>
      <td>PrivacySuppressed</td>
      <td>822</td>
    </tr>
    <tr>
      <th>GRAD_DEBT_MDN_SUPP</th>
      <td>7503</td>
      <td>2038</td>
      <td>PrivacySuppressed</td>
      <td>1510</td>
    </tr>
  </tbody>
</table>
</div>




```python

```



```python
import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50
```


```python
college = pd.read_csv('data/college.csv')
```


```python
with pd.option_context('display.max_rows', 5):
    display(college.describe(include=[np.number], 
                 percentiles=[.01, .05, .10, .25, .5, .75, .9, .95, .99]).T)
```
### Hasil dari source code diatas

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
      <th>1%</th>
      <th>5%</th>
      <th>10%</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>90%</th>
      <th>95%</th>
      <th>99%</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>HBCU</th>
      <td>7164.0</td>
      <td>0.014238</td>
      <td>0.118478</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.000000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>MENONLY</th>
      <td>7164.0</td>
      <td>0.009213</td>
      <td>0.095546</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.0</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>PCTFLOAN</th>
      <td>6849.0</td>
      <td>0.522211</td>
      <td>0.283616</td>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.3329</td>
      <td>0.58330</td>
      <td>0.745000</td>
      <td>0.84752</td>
      <td>0.89792</td>
      <td>0.986368</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>UG25ABV</th>
      <td>6718.0</td>
      <td>0.410021</td>
      <td>0.228939</td>
      <td>0.0</td>
      <td>0.0025</td>
      <td>0.0374</td>
      <td>0.0899</td>
      <td>0.2415</td>
      <td>0.40075</td>
      <td>0.572275</td>
      <td>0.72666</td>
      <td>0.80000</td>
      <td>0.917383</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
<p>22 rows × 14 columns</p>
</div>



```python

```



```python
import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50
```


```python
college = pd.read_csv('data/college.csv')
```


```python
college.info()
```

### Hasil dari source code diatas

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 7535 entries, 0 to 7534
    Data columns (total 27 columns):
    INSTNM                7535 non-null object
    CITY                  7535 non-null object
    STABBR                7535 non-null object
    HBCU                  7164 non-null float64
    MENONLY               7164 non-null float64
    WOMENONLY             7164 non-null float64
    RELAFFIL              7535 non-null int64
    SATVRMID              1185 non-null float64
    SATMTMID              1196 non-null float64
    DISTANCEONLY          7164 non-null float64
    UGDS                  6874 non-null float64
    UGDS_WHITE            6874 non-null float64
    UGDS_BLACK            6874 non-null float64
    UGDS_HISP             6874 non-null float64
    UGDS_ASIAN            6874 non-null float64
    UGDS_AIAN             6874 non-null float64
    UGDS_NHPI             6874 non-null float64
    UGDS_2MOR             6874 non-null float64
    UGDS_NRA              6874 non-null float64
    UGDS_UNKN             6874 non-null float64
    PPTUG_EF              6853 non-null float64
    CURROPER              7535 non-null int64
    PCTPELL               6849 non-null float64
    PCTFLOAN              6849 non-null float64
    UG25ABV               6718 non-null float64
    MD_EARN_WNE_P10       6413 non-null object
    GRAD_DEBT_MDN_SUPP    7503 non-null object
    dtypes: float64(20), int64(2), object(5)
    memory usage: 1.6+ MB



```python

```



```python
import pandas as pd
import numpy as np
from IPython.display import display
```


```python
college_dd = pd.read_csv('data/college_data_dictionary.csv')
```


```python
with pd.option_context('display.max_rows', 8):
    display(college_dd)
```

### Hasil dari source code diatas

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
      <th>column_name</th>
      <th>description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>INSTNM</td>
      <td>Institution Name</td>
    </tr>
    <tr>
      <th>1</th>
      <td>CITY</td>
      <td>City Location</td>
    </tr>
    <tr>
      <th>2</th>
      <td>STABBR</td>
      <td>State Abbreviation</td>
    </tr>
    <tr>
      <th>3</th>
      <td>HBCU</td>
      <td>Historically Black College or University</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>23</th>
      <td>PCTFLOAN</td>
      <td>Percent Students with federal loan</td>
    </tr>
    <tr>
      <th>24</th>
      <td>UG25ABV</td>
      <td>Percent Students Older than 25</td>
    </tr>
    <tr>
      <th>25</th>
      <td>MD_EARN_WNE_P10</td>
      <td>Median Earnings 10 years after enrollment</td>
    </tr>
    <tr>
      <th>26</th>
      <td>GRAD_DEBT_MDN_SUPP</td>
      <td>Median debt of completers</td>
    </tr>
  </tbody>
</table>
<p>27 rows × 2 columns</p>
</div>



```python

```


```python
import pandas as pd
import numpy as np
from IPython.display import display
```


```python
college = pd.read_csv('data/college.csv')
different_cols = ['RELAFFIL', 'SATMTMID', 'CURROPER', 'INSTNM', 'STABBR']
col2 = college.loc[:, different_cols]
col2.head()
```

### Hasil source code diatas


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
      <th>RELAFFIL</th>
      <th>SATMTMID</th>
      <th>CURROPER</th>
      <th>INSTNM</th>
      <th>STABBR</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>420.0</td>
      <td>1</td>
      <td>Alabama A &amp; M University</td>
      <td>AL</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>565.0</td>
      <td>1</td>
      <td>University of Alabama at Birmingham</td>
      <td>AL</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>NaN</td>
      <td>1</td>
      <td>Amridge University</td>
      <td>AL</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>590.0</td>
      <td>1</td>
      <td>University of Alabama in Huntsville</td>
      <td>AL</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>430.0</td>
      <td>1</td>
      <td>Alabama State University</td>
      <td>AL</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python

```


```python
import pandas as pd
import numpy as np
from IPython.display import display
```


```python
college = pd.read_csv('data/college.csv')
different_cols = ['RELAFFIL', 'SATMTMID', 'CURROPER', 'INSTNM', 'STABBR']
col2 = college.loc[:, different_cols]
col2.dtypes
```
### Hasil dari source code diatas




    RELAFFIL      int64
    SATMTMID    float64
    CURROPER      int64
    INSTNM       object
    STABBR       object
    dtype: object




```python

```


```python

```


```python
import pandas as pd
import numpy as np
from IPython.display import display

```


```python

college = pd.read_csv('data/college.csv')
different_cols = ['RELAFFIL', 'SATMTMID', 'CURROPER', 'INSTNM', 'STABBR']
col2 = college.loc[:, different_cols]
original_mem = col2.memory_usage(deep=True)
original_mem
```

### Hasil dari source code diatas


    Index           80
    RELAFFIL     60280
    SATMTMID     60280
    CURROPER     60280
    INSTNM      660240
    STABBR      444565
    dtype: int64




```python

```


```python
import pandas as pd
import numpy as np
from IPython.display import display
```


```python
college = pd.read_csv('data/college.csv')
different_cols = ['RELAFFIL', 'SATMTMID', 'CURROPER', 'INSTNM', 'STABBR']
col2 = college.loc[:, different_cols]
col2['RELAFFIL'] = col2['RELAFFIL'].astype(np.int8)
col2.dtypes
```

### Hasil dari source code diatas


    RELAFFIL       int8
    SATMTMID    float64
    CURROPER      int64
    INSTNM       object
    STABBR       object
    dtype: object




```python

```


```python

```


```python
import pandas as pd
import numpy as np
from IPython.display import display
```


```python
college = pd.read_csv('data/college.csv')
different_cols = ['RELAFFIL', 'SATMTMID', 'CURROPER', 'INSTNM', 'STABBR']
col2 = college.loc[:, different_cols]
col2['RELAFFIL'] = col2['RELAFFIL'].astype(np.int8)
col2.select_dtypes(include=['object']).nunique()
```

### Hasil dari source code diatas



    INSTNM    7535
    STABBR      59
    dtype: int64




```python

```


```python

```



```python
import pandas as pd
import numpy as np
from IPython.display import display
```


```python
college = pd.read_csv('data/college.csv')
different_cols = ['RELAFFIL', 'SATMTMID', 'CURROPER', 'INSTNM', 'STABBR']
col2 = college.loc[:, different_cols]
col2['STABBR'] = col2['STABBR'].astype('category')
col2.dtypes
```


### Hasil dari source code diatas 

    RELAFFIL       int64
    SATMTMID     float64
    CURROPER       int64
    INSTNM        object
    STABBR      category
    dtype: object




```python

```

