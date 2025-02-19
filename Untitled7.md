```python
import numpy as np
import pandas as pd

# Import packages for data visualization
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
data = pd.read_csv(r"C:\Users\USER\Downloads\tiktok_dataset.csv")
```


```python
data.head()
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
      <th>#</th>
      <th>claim_status</th>
      <th>video_id</th>
      <th>video_duration_sec</th>
      <th>video_transcription_text</th>
      <th>verified_status</th>
      <th>author_ban_status</th>
      <th>video_view_count</th>
      <th>video_like_count</th>
      <th>video_share_count</th>
      <th>video_download_count</th>
      <th>video_comment_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>claim</td>
      <td>7017666017</td>
      <td>59</td>
      <td>someone shared with me that drone deliveries a...</td>
      <td>not verified</td>
      <td>under review</td>
      <td>343296.0</td>
      <td>19425.0</td>
      <td>241.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>claim</td>
      <td>4014381136</td>
      <td>32</td>
      <td>someone shared with me that there are more mic...</td>
      <td>not verified</td>
      <td>active</td>
      <td>140877.0</td>
      <td>77355.0</td>
      <td>19034.0</td>
      <td>1161.0</td>
      <td>684.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>claim</td>
      <td>9859838091</td>
      <td>31</td>
      <td>someone shared with me that american industria...</td>
      <td>not verified</td>
      <td>active</td>
      <td>902185.0</td>
      <td>97690.0</td>
      <td>2858.0</td>
      <td>833.0</td>
      <td>329.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>claim</td>
      <td>1866847991</td>
      <td>25</td>
      <td>someone shared with me that the metro of st. p...</td>
      <td>not verified</td>
      <td>active</td>
      <td>437506.0</td>
      <td>239954.0</td>
      <td>34812.0</td>
      <td>1234.0</td>
      <td>584.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>claim</td>
      <td>7105231098</td>
      <td>19</td>
      <td>someone shared with me that the number of busi...</td>
      <td>not verified</td>
      <td>active</td>
      <td>56167.0</td>
      <td>34987.0</td>
      <td>4110.0</td>
      <td>547.0</td>
      <td>152.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 19382 entries, 0 to 19381
    Data columns (total 12 columns):
     #   Column                    Non-Null Count  Dtype  
    ---  ------                    --------------  -----  
     0   #                         19382 non-null  int64  
     1   claim_status              19084 non-null  object 
     2   video_id                  19382 non-null  int64  
     3   video_duration_sec        19382 non-null  int64  
     4   video_transcription_text  19084 non-null  object 
     5   verified_status           19382 non-null  object 
     6   author_ban_status         19382 non-null  object 
     7   video_view_count          19084 non-null  float64
     8   video_like_count          19084 non-null  float64
     9   video_share_count         19084 non-null  float64
     10  video_download_count      19084 non-null  float64
     11  video_comment_count       19084 non-null  float64
    dtypes: float64(5), int64(3), object(4)
    memory usage: 1.8+ MB
    


```python
data.describe()
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
      <th>#</th>
      <th>video_id</th>
      <th>video_duration_sec</th>
      <th>video_view_count</th>
      <th>video_like_count</th>
      <th>video_share_count</th>
      <th>video_download_count</th>
      <th>video_comment_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>19382.000000</td>
      <td>1.938200e+04</td>
      <td>19382.000000</td>
      <td>19084.000000</td>
      <td>19084.000000</td>
      <td>19084.000000</td>
      <td>19084.000000</td>
      <td>19084.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>9691.500000</td>
      <td>5.627454e+09</td>
      <td>32.421732</td>
      <td>254708.558688</td>
      <td>84304.636030</td>
      <td>16735.248323</td>
      <td>1049.429627</td>
      <td>349.312146</td>
    </tr>
    <tr>
      <th>std</th>
      <td>5595.245794</td>
      <td>2.536440e+09</td>
      <td>16.229967</td>
      <td>322893.280814</td>
      <td>133420.546814</td>
      <td>32036.174350</td>
      <td>2004.299894</td>
      <td>799.638865</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.234959e+09</td>
      <td>5.000000</td>
      <td>20.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>4846.250000</td>
      <td>3.430417e+09</td>
      <td>18.000000</td>
      <td>4942.500000</td>
      <td>810.750000</td>
      <td>115.000000</td>
      <td>7.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>9691.500000</td>
      <td>5.618664e+09</td>
      <td>32.000000</td>
      <td>9954.500000</td>
      <td>3403.500000</td>
      <td>717.000000</td>
      <td>46.000000</td>
      <td>9.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>14536.750000</td>
      <td>7.843960e+09</td>
      <td>47.000000</td>
      <td>504327.000000</td>
      <td>125020.000000</td>
      <td>18222.000000</td>
      <td>1156.250000</td>
      <td>292.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>19382.000000</td>
      <td>9.999873e+09</td>
      <td>60.000000</td>
      <td>999817.000000</td>
      <td>657830.000000</td>
      <td>256130.000000</td>
      <td>14994.000000</td>
      <td>9599.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize=(5,1))
plt.title('video_duration_sec')
sns.boxplot(x=data['video_duration_sec']);
```


    
![png](output_5_0.png)
    



```python
plt.figure(figsize=(5,5))
plt.title('Video_duration_sec')
sns.histplot(data['video_duration_sec'], bins=range(1,61,5))
```




    <Axes: title={'center': 'Video_duration_sec'}, xlabel='video_duration_sec', ylabel='Count'>




    
![png](output_6_1.png)
    



```python
plt.figure(figsize=(5,1))
plt.title('video_view_count')
sns.boxplot(x=data['video_view_count'])
```




    <Axes: title={'center': 'video_view_count'}, xlabel='video_view_count'>




    
![png](output_7_1.png)
    



```python
plt.figure(figsize=(5,5))
plt.title('video views')
sns.histplot(data['video_view_count'], bins=range(0,(10**6+1),(10**5)))

```




    <Axes: title={'center': 'video views'}, xlabel='video_view_count', ylabel='Count'>




    
![png](output_8_1.png)
    



```python
plt.figure(figsize=(5,1))
plt.title('video_like_count')
sns.boxplot(x=data['video_like_count'])

```




    <Axes: title={'center': 'video_like_count'}, xlabel='video_like_count'>




    
![png](output_9_1.png)
    



```python
plt.figure(figsize=(5,3))
plt.title('distribution of video like count')
bin_width = 100000
max_likes = data['video_like_count'].max()
bins = np.arange(0,max_likes + bin_width, bin_width)
sns.histplot(data['video_like_count'], bins = bins)
labels = [0] + [str(i) + 'k' for i in range(100,701,100)]
tick_positions = np.arange(0, 700001, 100000)
plt.xticks(tick_positions, labels)
plt.show()

```


    
![png](output_10_0.png)
    



```python
plt.figure(figsize=(5,1))
plt.title('video_comment_count')
sns.boxplot(x= data['video_comment_count'])

```




    <Axes: title={'center': 'video_comment_count'}, xlabel='video_comment_count'>




    
![png](output_11_1.png)
    



```python
plt.figure(figsize=(5,3))
plt.title('distribution of video comment count')
bin_width = 100
bins = np.arange(0,4001, bin_width)
sns.histplot(data['video_comment_count'], bins=bins)
plt.show()
```


    
![png](output_12_0.png)
    



```python
plt.figure(figsize=(5,1))
plt.title('video_share_count')
sns.boxplot(x = data['video_share_count'])
plt.show()
```


    
![png](output_13_0.png)
    



```python
plt.figure(figsize=(5,3))
plt.title('Distribution of video share count')
bin_width = 10000
sns.histplot(data['video_share_count'], bins=range(0,(25*10**4+1),bin_width))
```




    <Axes: title={'center': 'Distribution of video share count'}, xlabel='video_share_count', ylabel='Count'>




    
![png](output_14_1.png)
    



```python
plt.figure(figsize=(5,1))
plt.title('video download count')
sns.boxplot(x = data['video_download_count'])
plt.show()
```


    
![png](output_15_0.png)
    



```python
plt.figure(figsize=(5,3))
plt.title('Distribution of video download count')
sns.histplot(data['video_download_count'], bins=range(0,8001,500))

```




    <Axes: title={'center': 'Distribution of video download count'}, xlabel='video_download_count', ylabel='Count'>




    
![png](output_16_1.png)
    



```python
plt.figure(figsize=(7,3))
sns.histplot(data = data,
            x = 'claim_status',
            hue = 'verified_status',
            multiple = 'dodge',
            shrink = 0.9)

plt.title('Claim_by_verification_status')
plt.show()

```


    
![png](output_17_0.png)
    



```python
plt.figure(figsize=(7,3))
sns.histplot(data = data,
            x = 'claim_status',
            hue = 'author_ban_status',
            multiple = 'dodge',
            hue_order = ['active', 'under review', 'banned'],
            palette = {'active':'green', 'under review':'yellow', 'banned':'red'},
            alpha = 0.5,
            shrink = 0.9)
plt.title('claim status by author ban status')
plt.show()
```


    
![png](output_18_0.png)
    



```python
plt.figure(figsize=(5,3))
ban_status_counts = data.groupby(['author_ban_status']).median(
    numeric_only=True).reset_index()
sns.barplot(data = ban_status_counts,
            x = 'author_ban_status',
            y = 'video_view_count',
            hue = 'author_ban_status',
            legend= False,
            palette = {'active':'green', 'under review':'yellow', 'banned':'red'},
            alpha = 0.5,)
plt.show()
```


    
![png](output_19_0.png)
    



```python
data.groupby('claim_status')['video_view_count'].median()
```


```python
plt.figure(figsize=(5,5))
plt.pie(data.groupby('claim_status')['video_view_count'].sum(), labels=['claim', 'opinion'])
plt.title('total views by claim status')
plt.show()
```


    
![png](output_21_0.png)
    


## Check for outliers


```python
data_columns = ['video_view_count',
               'video_like_count',
               'video_comment_count',
               'video_share_count',
               'video_download_count',
               'video_duration_sec']
for columns in data_columns:
    q1 = data[columns].quantile(0.25)
    q3 = data[columns].quantile(0.75)
    median = data[columns].median()
    iqr = q3 - q1
    outlier_threshold = median + 1.5*iqr

    outlier_count = (data[columns]>outlier_threshold).sum()
    print(f'number of outliers,{columns}:', outlier_count)

    
        
```

    number of outliers,video_view_count: 2343
    number of outliers,video_like_count: 3468
    number of outliers,video_comment_count: 3882
    number of outliers,video_share_count: 3732
    number of outliers,video_download_count: 3733
    number of outliers,video_duration_sec: 0
    


```python
sns.scatterplot(x = data['video_view_count'], y=data['video_like_count'],
               hue= data['claim_status'],
               alpha = .3,
               s = 10)
```




    <Axes: xlabel='video_view_count', ylabel='video_like_count'>




    
![png](output_24_1.png)
    



```python
opinion_data = data[data['claim_status']=='opinion']
sns.scatterplot(x = opinion_data['video_view_count'], y = opinion_data['video_like_count'],
               s=10,
               alpha = 0.3)
```




    <Axes: xlabel='video_view_count', ylabel='video_like_count'>




    
![png](output_25_1.png)
    



```python

```
