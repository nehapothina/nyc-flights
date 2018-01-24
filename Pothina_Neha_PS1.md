
###### NYC FLIGHTS 2013 DATA SET EXPLORATORY ANALYSIS



```python

# Numpy is a library for working with Arrays
import numpy as np
print ("Numpy version:        %6.6s (need at least 1.7.1)" % np.__version__)

# SciPy implements many different numerical algorithms
import scipy as sp
print ("SciPy version:        %6.6s (need at least 0.12.0)" % sp.__version__)

# Pandas makes working with data tables easier
import pandas as pd
print ("Pandas version:       %6.6s (need at least 0.11.0)" % pd.__version__)

# Module for plotting
import matplotlib
print ("Mapltolib version:    %6.6s (need at least 1.2.1)" % matplotlib.__version__)

# SciKit Learn implements several Machine Learning algorithms
import sklearn
print ("Scikit-Learn version: %6.6s (need at least 0.13.1)" % sklearn.__version__)
```

    Numpy version:        1.11.3 (need at least 1.7.1)
    SciPy version:        0.18.1 (need at least 0.12.0)
    Pandas version:       0.19.2 (need at least 0.11.0)
    Mapltolib version:     2.0.0 (need at least 1.2.1)
    Scikit-Learn version: 0.18.1 (need at least 0.13.1)



```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```


```python
flights_df= pd.read_csv('flights.csv')
```


```python
print (flights_df.shape)
print (flights_df.columns)
print (flights_df.dtypes)
```

    (336776, 17)
    Index(['Unnamed: 0', 'year', 'month', 'day', 'dep_time', 'dep_delay',
           'arr_time', 'arr_delay', 'carrier', 'tailnum', 'flight', 'origin',
           'dest', 'air_time', 'distance', 'hour', 'minute'],
          dtype='object')
    Unnamed: 0      int64
    year            int64
    month           int64
    day             int64
    dep_time      float64
    dep_delay     float64
    arr_time      float64
    arr_delay     float64
    carrier        object
    tailnum        object
    flight          int64
    origin         object
    dest           object
    air_time      float64
    distance        int64
    hour          float64
    minute        float64
    dtype: object



```python
a = flights_df.dest.unique()
print(a)
flights_df.head(10)

```

    ['IAH' 'MIA' 'BQN' 'ATL' 'ORD' 'FLL' 'IAD' 'MCO' 'PBI' 'TPA' 'LAX' 'SFO'
     'DFW' 'BOS' 'LAS' 'MSP' 'DTW' 'RSW' 'SJU' 'PHX' 'BWI' 'CLT' 'BUF' 'DEN'
     'SNA' 'MSY' 'SLC' 'XNA' 'MKE' 'SEA' 'ROC' 'SYR' 'SRQ' 'RDU' 'CMH' 'JAX'
     'CHS' 'MEM' 'PIT' 'SAN' 'DCA' 'CLE' 'STL' 'MYR' 'JAC' 'MDW' 'HNL' 'BNA'
     'AUS' 'BTV' 'PHL' 'STT' 'EGE' 'AVL' 'PWM' 'IND' 'SAV' 'CAK' 'HOU' 'LGB'
     'DAY' 'ALB' 'BDL' 'MHT' 'MSN' 'GSO' 'CVG' 'BUR' 'RIC' 'GSP' 'GRR' 'MCI'
     'ORF' 'SAT' 'SDF' 'PDX' 'SJC' 'OMA' 'CRW' 'OAK' 'SMF' 'TUL' 'TYS' 'OKC'
     'PVD' 'DSM' 'PSE' 'BHM' 'CAE' 'HDN' 'BZN' 'MTJ' 'EYW' 'PSP' 'ACK' 'BGR'
     'ABQ' 'ILM' 'MVY' 'SBN' 'LEX' 'CHO' 'TVC' 'ANC' 'LGA']





<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
      <th>dep_time</th>
      <th>dep_delay</th>
      <th>arr_time</th>
      <th>arr_delay</th>
      <th>carrier</th>
      <th>tailnum</th>
      <th>flight</th>
      <th>origin</th>
      <th>dest</th>
      <th>air_time</th>
      <th>distance</th>
      <th>hour</th>
      <th>minute</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>517.0</td>
      <td>2.0</td>
      <td>830.0</td>
      <td>11.0</td>
      <td>UA</td>
      <td>N14228</td>
      <td>1545</td>
      <td>EWR</td>
      <td>IAH</td>
      <td>227.0</td>
      <td>1400</td>
      <td>5.0</td>
      <td>17.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>533.0</td>
      <td>4.0</td>
      <td>850.0</td>
      <td>20.0</td>
      <td>UA</td>
      <td>N24211</td>
      <td>1714</td>
      <td>LGA</td>
      <td>IAH</td>
      <td>227.0</td>
      <td>1416</td>
      <td>5.0</td>
      <td>33.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>542.0</td>
      <td>2.0</td>
      <td>923.0</td>
      <td>33.0</td>
      <td>AA</td>
      <td>N619AA</td>
      <td>1141</td>
      <td>JFK</td>
      <td>MIA</td>
      <td>160.0</td>
      <td>1089</td>
      <td>5.0</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>544.0</td>
      <td>-1.0</td>
      <td>1004.0</td>
      <td>-18.0</td>
      <td>B6</td>
      <td>N804JB</td>
      <td>725</td>
      <td>JFK</td>
      <td>BQN</td>
      <td>183.0</td>
      <td>1576</td>
      <td>5.0</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>554.0</td>
      <td>-6.0</td>
      <td>812.0</td>
      <td>-25.0</td>
      <td>DL</td>
      <td>N668DN</td>
      <td>461</td>
      <td>LGA</td>
      <td>ATL</td>
      <td>116.0</td>
      <td>762</td>
      <td>5.0</td>
      <td>54.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>554.0</td>
      <td>-4.0</td>
      <td>740.0</td>
      <td>12.0</td>
      <td>UA</td>
      <td>N39463</td>
      <td>1696</td>
      <td>EWR</td>
      <td>ORD</td>
      <td>150.0</td>
      <td>719</td>
      <td>5.0</td>
      <td>54.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>555.0</td>
      <td>-5.0</td>
      <td>913.0</td>
      <td>19.0</td>
      <td>B6</td>
      <td>N516JB</td>
      <td>507</td>
      <td>EWR</td>
      <td>FLL</td>
      <td>158.0</td>
      <td>1065</td>
      <td>5.0</td>
      <td>55.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>557.0</td>
      <td>-3.0</td>
      <td>709.0</td>
      <td>-14.0</td>
      <td>EV</td>
      <td>N829AS</td>
      <td>5708</td>
      <td>LGA</td>
      <td>IAD</td>
      <td>53.0</td>
      <td>229</td>
      <td>5.0</td>
      <td>57.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>557.0</td>
      <td>-3.0</td>
      <td>838.0</td>
      <td>-8.0</td>
      <td>B6</td>
      <td>N593JB</td>
      <td>79</td>
      <td>JFK</td>
      <td>MCO</td>
      <td>140.0</td>
      <td>944</td>
      <td>5.0</td>
      <td>57.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>2013</td>
      <td>1</td>
      <td>1</td>
      <td>558.0</td>
      <td>-2.0</td>
      <td>753.0</td>
      <td>8.0</td>
      <td>AA</td>
      <td>N3ALAA</td>
      <td>301</td>
      <td>LGA</td>
      <td>ORD</td>
      <td>138.0</td>
      <td>733</td>
      <td>5.0</td>
      <td>58.0</td>
    </tr>
  </tbody>
</table>
</div>



I explored flights from NYC to Seattle. Used the flights dataset to answer the following questions.

(a) How many flights were there from NYC airports to Seattle in 2013?


```python

flights_df1=flights_df[ flights_df.dest=='SEA']
flights_df1.shape[0]
```




    3923



(b) How many airlines fly from NYC to Seattle?


```python

carriersN_to_seattle = flights_df1.carrier.unique()
print(carriersN_to_seattle)
```

    ['AS' 'DL' 'UA' 'B6' 'AA']


(c) How many unique air planes fly from NYC to Seattle?


```python

flights_df1['tailnum'].nunique()

```




    935



(d) What is the average arrival delay for flights from NC to Seattle?


```python

flights_df1['arr_delay'].mean()
```




    -1.0990990990990992



(e) What proportion of flights to Seattle come from each NYC airport? Provide multiple ways of answering the question.


```python

# Find unique origins
nyc_origins = flights_df1['origin'].unique()
print(nyc_origins)

```

    ['EWR' 'JFK']


## Exploring delay patterns
Flights are often delayed. I considered the following questions exploring delay patterns.

(a) Which date has the largest average departure delay? Which date has the largest average arrival delay?


```python
from datetime import datetime
flights_df['date'] = pd.to_datetime(flights_df.year*10000+flights_df.month*100+flights_df.day,format='%Y%m%d')

grouped_data = flights_df.groupby('date').mean()
print("\nLargest avg arr_delay")
print(grouped_data[grouped_data['arr_delay']==grouped_data.arr_delay.max()])
print("\nLargest avg dep_delay")
print(grouped_data[grouped_data['dep_delay']==grouped_data.dep_delay.max()])

```

    
    Largest avg arr_delay
                Unnamed: 0    year  month  day     dep_time  dep_delay  \
    date                                                                 
    2013-03-08    143267.0  2013.0    3.0  8.0  1416.659574  83.536921   
    
                   arr_time  arr_delay       flight    air_time     distance  \
    date                                                                       
    2013-03-08  1503.931078  85.862155  2013.537283  153.746867  1002.540347   
    
                     hour     minute  
    date                              
    2013-03-08  13.867334  29.926158  
    
    Largest avg dep_delay
                Unnamed: 0    year  month  day     dep_time  dep_delay  \
    date                                                                 
    2013-03-08    143267.0  2013.0    3.0  8.0  1416.659574  83.536921   
    
                   arr_time  arr_delay       flight    air_time     distance  \
    date                                                                       
    2013-03-08  1503.931078  85.862155  2013.537283  153.746867  1002.540347   
    
                     hour     minute  
    date                              
    2013-03-08  13.867334  29.926158  


The date with the largest average departure as well as arrival delay was March 8th 2013.

(b) What was the worst day to fly out of NYC in 2013 if you dislike delayed flights?



```python
grouped_data_1 = flights_df[flights_df.dep_delay > 0].groupby('date').dep_delay.count().sort_values(ascending = False)
grouped_data_1.head(1)
```




    date
    2013-12-23    674
    Name: dep_delay, dtype: int64



The worst day to fly out of NYC in 2013 if I dislike delayed flights was ['12-23-2013'] since the number of delayed flights for the day was :674

(c) Are there any seasonal patterns in departure delays for flights from NYC?


```python
flights_df.groupby('month').dep_delay.mean().plot(title = "Average Departure Delays by Month")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11d2dd630>



On an average summer months seem to have greater departure delays than other times of the year. There is also another peak in December, which could probably be due to the holiday season.

(d) On average, how do departure delays vary over the course of a day?


```python
flights_df.groupby('hour').dep_delay.mean().plot(title = "Average Departure Delays by hour")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11d2dd630>



Departure delays are the higheset betwen 12am and 3am, that is the early morning flights, and then the departure delays have a steep decline at 4 am and continue to slowly rise from 4 am to 8pm before increasing rapidly again and forming a small peak around 11 pm before declining at 12 pm.

Which flight departing NYC in 2013 flew the fastest?


```python
flights_df['speed'] = flights_df.distance / flights_df.air_time
flights_df.sort_values('speed', ascending=False).head(1) 
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
      <th>dep_time</th>
      <th>dep_delay</th>
      <th>arr_time</th>
      <th>arr_delay</th>
      <th>carrier</th>
      <th>tailnum</th>
      <th>flight</th>
      <th>origin</th>
      <th>dest</th>
      <th>air_time</th>
      <th>distance</th>
      <th>hour</th>
      <th>minute</th>
      <th>date</th>
      <th>speed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>216447</th>
      <td>216448</td>
      <td>2013</td>
      <td>5</td>
      <td>25</td>
      <td>1709.0</td>
      <td>9.0</td>
      <td>1923.0</td>
      <td>-14.0</td>
      <td>DL</td>
      <td>N666DN</td>
      <td>1499</td>
      <td>LGA</td>
      <td>ATL</td>
      <td>65.0</td>
      <td>762</td>
      <td>17.0</td>
      <td>9.0</td>
      <td>2013-05-25</td>
      <td>11.723077</td>
    </tr>
  </tbody>
</table>
</div>



The fastest flight departing NYC was flight 1499, which departed from LGA towards ATL.


Which flights (i.e. carrier + flight + dest) happen every day? Where do they fly to?


```python
flights_df['combination'] = flights_df.carrier +"-"+ flights_df.flight.astype('str') +"-"+ flights_df.dest
flights_df.groupby(['combination']).date.nunique()[flights_df.groupby(['combination']).date.nunique()==365]

```




    combination
    AA-119-LAX     365
    AA-1357-SJU    365
    AA-1611-MIA    365
    AA-181-LAX     365
    AA-59-SFO      365
    B6-1783-MCO    365
    B6-219-CLT     365
    B6-359-BUR     365
    B6-371-FLL     365
    B6-431-SRQ     365
    B6-703-SJU     365
    DL-2159-MCO    365
    DL-2391-TPA    365
    EV-5712-IAD    365
    UA-15-HNL      365
    VX-251-LAS     365
    VX-407-LAX     365
    VX-413-LAX     365
    Name: date, dtype: int64



The above flights happen every day, wherein the last three letters of the combination provide information on the destination of the flight. 


Who were the best carriers to take if you wanted to fly out of New York to Seattle in 2013 ?



```python
sea_df = flights_df[flights_df.dest == "SEA"]
sea_df.groupby(['carrier','month']).dep_delay.mean().unstack('carrier').plot(title = "Average departure delays")
sea_df.groupby(['carrier','month']).arr_delay.mean().unstack('carrier').plot(title = "Average Arrival delays")

```




    <matplotlib.axes._subplots.AxesSubplot at 0x12995f438>



For the most part, Alaska Airlines had a low average arrival and departure delay. United Airlines consistently had a higher departure delay and Jet Blue had a consistently high arrival delay. American Airlines, had moderate to high average departure and arrival delays. Looking at the two graphs, Alaskan Airlines and Delta Airlines would have been a good bet to travel in, in 2013 from NYC to Seattle. 


What weather conditions are associated with flight delays leaving NYC? Use graphics to explore.


```python
weather_df = pd.read_csv("weather.csv")
merged_data = pd.merge(flights_df, weather_df, on=['year','month','day','hour','origin'], how='inner')
merged_data.groupby('month').dep_delay.mean().plot(title = "Average Departure Delays by Month")

```




    <matplotlib.axes._subplots.AxesSubplot at 0x12995f438>




```python
merged_data.groupby('month').humid.mean().plot(title = "Average humidity by Month")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x12995f438>




```python
merged_data.groupby('month').wind_speed.mean().plot(title = "Average Wind Speed by Month")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x12995f438>




```python
merged_data.groupby('month').visib.mean().plot(title = "Average Visibility by Month")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x12995f438>




```python
merged_data.groupby('month').dewp.mean().plot(title = "Average Dew Point by Month")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x12995f438>




```python
merged_data.groupby('visib').dep_delay.mean().plot(title = "Average Departure Delay to Visibility")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x12995f438>



From the above graphs we see that the delay of flights is affected by visibility - i.e. when visibility decreases there is an increase in the average delay of flights. The delay of flights also seems to be affected by humidity to some extent but not by wind speed. To prove that when visibility decreases there is an increase in the average delay of flights, we plot visibility and average departure delays together we see that low visibility indeed leads to high number of departure delays.
