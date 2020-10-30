import pandas as pd
import numpy as np

# 1.Some values in the the FlightNumber column are missing.
#  These numbers are meant to increase by 10 with each row so 10055 and 10075 need to be put in place.
#  Fill in these missing numbers and make the column an integer column (instead of a float column).
In [3]:
df = pd.DataFrame({'From_To': ['LoNDon_paris', 'MAdrid_miLAN', 'londON_StockhOlm',
'Budapest_PaRis', 'Brussels_londOn'], 'FlightNumber': [10045, np.nan, 10065, np.nan, 10085], 'RecentDelays': [[23, 47], [], [24, 43, 87], [13], [67, 32]],
'Airline': ['KLM(!)', '<Air France> (12)', '(British Airways. )', '12. Air France', '"Swiss Air"']})
In [4]:
for i in range(1, df['FlightNumber'].count() + 1):
      if pd.isnull(df.loc[i,'FlightNumber']):
          df.loc[i, 'FlightNumber'] = df.loc[i-1, 'FlightNumber'] + 10
In [5]:
df
Out[5]:
From_To	FlightNumber	RecentDelays	Airline
0	LoNDon_paris	10045.0	[23, 47]	KLM(!)
1	MAdrid_miLAN	10055.0	[]	<Air France> (12)
2	londON_StockhOlm	10065.0	[24, 43, 87]	(British Airways. )
3	Budapest_PaRis	10075.0	[13]	12. Air France
4	Brussels_londOn	10085.0	[67, 32]	"Swiss Air"
In [6]:
df['FlightNumber'] = df['FlightNumber'].astype(int)
df.dtypes
Out[6]:
From_To         object
FlightNumber     int64
RecentDelays    object
Airline         object
dtype: object
In [ ]:

In [ ]:

In [7]:
# 2. The From_To column would be better as two separate columns!
#    Split each string on the underscore delimiter _ to give a new temporary DataFrame with the correct values.
#.   Assign the correct column names to this temporary DataFrame.
In [8]:
dftemporary=df.copy()             #make a copy
In [9]:
dftemporary[['From','To']]=dftemporary.From_To.str.split('_',expand=True)       #split the string and give the columns name
In [10]:
dftemporary
Out[10]:
From_To	FlightNumber	RecentDelays	Airline	From	To
0	LoNDon_paris	10045	[23, 47]	KLM(!)	LoNDon	paris
1	MAdrid_miLAN	10055	[]	<Air France> (12)	MAdrid	miLAN
2	londON_StockhOlm	10065	[24, 43, 87]	(British Airways. )	londON	StockhOlm
3	Budapest_PaRis	10075	[13]	12. Air France	Budapest	PaRis
4	Brussels_londOn	10085	[67, 32]	"Swiss Air"	Brussels	londOn
In [11]:
df1=dftemporary
In [ ]:

In [ ]:

In [12]:
# 3. Notice how the capitalisation of the city names is all mixed up in this temporary DataFrame.
#.   Standardise the strings so that only the first letter is uppercase (e.g. "londON" should become "London".)
In [13]:
df1.From=dftemporary.From.str.capitalize()
df1
Out[13]:
From_To	FlightNumber	RecentDelays	Airline	From	To
0	LoNDon_paris	10045	[23, 47]	KLM(!)	London	paris
1	MAdrid_miLAN	10055	[]	<Air France> (12)	Madrid	miLAN
2	londON_StockhOlm	10065	[24, 43, 87]	(British Airways. )	London	StockhOlm
3	Budapest_PaRis	10075	[13]	12. Air France	Budapest	PaRis
4	Brussels_londOn	10085	[67, 32]	"Swiss Air"	Brussels	londOn
In [18]:
df1.From_To=df1.From_To.str.capitalize()
df1
Out[18]:
From_To	FlightNumber	RecentDelays	Airline	From	To
0	London_paris	10045	[23, 47]	KLM(!)	London	Paris
1	Madrid_milan	10055	[]	<Air France> (12)	Madrid	Milan
2	London_stockholm	10065	[24, 43, 87]	(British Airways. )	London	Stockholm
3	Budapest_paris	10075	[13]	12. Air France	Budapest	Paris
4	Brussels_london	10085	[67, 32]	"Swiss Air"	Brussels	London
In [ ]:

In [15]:
# 4. Delete the From_To column from df and attach the temporary DataFrame from the previous questions
In [22]:
df['From_To']=df1['From_To']
In [23]:
df
Out[23]:
FlightNumber	RecentDelays	Airline	From_To
0	10045	[23, 47]	KLM(!)	London_paris
1	10055	[]	<Air France> (12)	Madrid_milan
2	10065	[24, 43, 87]	(British Airways. )	London_stockholm
3	10075	[13]	12. Air France	Budapest_paris
4	10085	[67, 32]	"Swiss Air"	Brussels_london
