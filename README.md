{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd\n",
    "import numpy as np"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {},
   "outputs": [],
   "source": [
    "# 1.Some values in the the FlightNumber column are missing.\n",
    "#  These numbers are meant to increase by 10 with each row so 10055 and 10075 need to be put in place.\n",
    "#  Fill in these missing numbers and make the column an integer column (instead of a float column)."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [],
   "source": [
    "df = pd.DataFrame({'From_To': ['LoNDon_paris', 'MAdrid_miLAN', 'londON_StockhOlm',\n",
    "'Budapest_PaRis', 'Brussels_londOn'], 'FlightNumber': [10045, np.nan, 10065, np.nan, 10085], 'RecentDelays': [[23, 47], [], [24, 43, 87], [13], [67, 32]],\n",
    "'Airline': ['KLM(!)', '<Air France> (12)', '(British Airways. )', '12. Air France', '\"Swiss Air\"']})"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [],
   "source": [
    "for i in range(1, df['FlightNumber'].count() + 1):\n",
    "      if pd.isnull(df.loc[i,'FlightNumber']):\n",
    "          df.loc[i, 'FlightNumber'] = df.loc[i-1, 'FlightNumber'] + 10"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>From_To</th>\n",
       "      <th>FlightNumber</th>\n",
       "      <th>RecentDelays</th>\n",
       "      <th>Airline</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>LoNDon_paris</td>\n",
       "      <td>10045.0</td>\n",
       "      <td>[23, 47]</td>\n",
       "      <td>KLM(!)</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>MAdrid_miLAN</td>\n",
       "      <td>10055.0</td>\n",
       "      <td>[]</td>\n",
       "      <td>&lt;Air France&gt; (12)</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>londON_StockhOlm</td>\n",
       "      <td>10065.0</td>\n",
       "      <td>[24, 43, 87]</td>\n",
       "      <td>(British Airways. )</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Budapest_PaRis</td>\n",
       "      <td>10075.0</td>\n",
       "      <td>[13]</td>\n",
       "      <td>12. Air France</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Brussels_londOn</td>\n",
       "      <td>10085.0</td>\n",
       "      <td>[67, 32]</td>\n",
       "      <td>\"Swiss Air\"</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            From_To  FlightNumber  RecentDelays              Airline\n",
       "0      LoNDon_paris       10045.0      [23, 47]               KLM(!)\n",
       "1      MAdrid_miLAN       10055.0            []    <Air France> (12)\n",
       "2  londON_StockhOlm       10065.0  [24, 43, 87]  (British Airways. )\n",
       "3    Budapest_PaRis       10075.0          [13]       12. Air France\n",
       "4   Brussels_londOn       10085.0      [67, 32]          \"Swiss Air\""
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "From_To         object\n",
       "FlightNumber     int64\n",
       "RecentDelays    object\n",
       "Airline         object\n",
       "dtype: object"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df['FlightNumber'] = df['FlightNumber'].astype(int)\n",
    "df.dtypes"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [],
   "source": [
    "# 2. The From_To column would be better as two separate columns!\n",
    "#    Split each string on the underscore delimiter _ to give a new temporary DataFrame with the correct values.\n",
    "#.   Assign the correct column names to this temporary DataFrame."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [],
   "source": [
    "dftemporary=df.copy()             #make a copy"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "dftemporary[['From','To']]=dftemporary.From_To.str.split('_',expand=True)       #split the string and give the columns name"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>From_To</th>\n",
       "      <th>FlightNumber</th>\n",
       "      <th>RecentDelays</th>\n",
       "      <th>Airline</th>\n",
       "      <th>From</th>\n",
       "      <th>To</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>LoNDon_paris</td>\n",
       "      <td>10045</td>\n",
       "      <td>[23, 47]</td>\n",
       "      <td>KLM(!)</td>\n",
       "      <td>LoNDon</td>\n",
       "      <td>paris</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>MAdrid_miLAN</td>\n",
       "      <td>10055</td>\n",
       "      <td>[]</td>\n",
       "      <td>&lt;Air France&gt; (12)</td>\n",
       "      <td>MAdrid</td>\n",
       "      <td>miLAN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>londON_StockhOlm</td>\n",
       "      <td>10065</td>\n",
       "      <td>[24, 43, 87]</td>\n",
       "      <td>(British Airways. )</td>\n",
       "      <td>londON</td>\n",
       "      <td>StockhOlm</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Budapest_PaRis</td>\n",
       "      <td>10075</td>\n",
       "      <td>[13]</td>\n",
       "      <td>12. Air France</td>\n",
       "      <td>Budapest</td>\n",
       "      <td>PaRis</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Brussels_londOn</td>\n",
       "      <td>10085</td>\n",
       "      <td>[67, 32]</td>\n",
       "      <td>\"Swiss Air\"</td>\n",
       "      <td>Brussels</td>\n",
       "      <td>londOn</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            From_To  FlightNumber  RecentDelays              Airline  \\\n",
       "0      LoNDon_paris         10045      [23, 47]               KLM(!)   \n",
       "1      MAdrid_miLAN         10055            []    <Air France> (12)   \n",
       "2  londON_StockhOlm         10065  [24, 43, 87]  (British Airways. )   \n",
       "3    Budapest_PaRis         10075          [13]       12. Air France   \n",
       "4   Brussels_londOn         10085      [67, 32]          \"Swiss Air\"   \n",
       "\n",
       "       From         To  \n",
       "0    LoNDon      paris  \n",
       "1    MAdrid      miLAN  \n",
       "2    londON  StockhOlm  \n",
       "3  Budapest      PaRis  \n",
       "4  Brussels     londOn  "
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "dftemporary"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [],
   "source": [
    "df1=dftemporary"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [],
   "source": [
    "# 3. Notice how the capitalisation of the city names is all mixed up in this temporary DataFrame.\n",
    "#.   Standardise the strings so that only the first letter is uppercase (e.g. \"londON\" should become \"London\".)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>From_To</th>\n",
       "      <th>FlightNumber</th>\n",
       "      <th>RecentDelays</th>\n",
       "      <th>Airline</th>\n",
       "      <th>From</th>\n",
       "      <th>To</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>LoNDon_paris</td>\n",
       "      <td>10045</td>\n",
       "      <td>[23, 47]</td>\n",
       "      <td>KLM(!)</td>\n",
       "      <td>London</td>\n",
       "      <td>paris</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>MAdrid_miLAN</td>\n",
       "      <td>10055</td>\n",
       "      <td>[]</td>\n",
       "      <td>&lt;Air France&gt; (12)</td>\n",
       "      <td>Madrid</td>\n",
       "      <td>miLAN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>londON_StockhOlm</td>\n",
       "      <td>10065</td>\n",
       "      <td>[24, 43, 87]</td>\n",
       "      <td>(British Airways. )</td>\n",
       "      <td>London</td>\n",
       "      <td>StockhOlm</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Budapest_PaRis</td>\n",
       "      <td>10075</td>\n",
       "      <td>[13]</td>\n",
       "      <td>12. Air France</td>\n",
       "      <td>Budapest</td>\n",
       "      <td>PaRis</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Brussels_londOn</td>\n",
       "      <td>10085</td>\n",
       "      <td>[67, 32]</td>\n",
       "      <td>\"Swiss Air\"</td>\n",
       "      <td>Brussels</td>\n",
       "      <td>londOn</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            From_To  FlightNumber  RecentDelays              Airline  \\\n",
       "0      LoNDon_paris         10045      [23, 47]               KLM(!)   \n",
       "1      MAdrid_miLAN         10055            []    <Air France> (12)   \n",
       "2  londON_StockhOlm         10065  [24, 43, 87]  (British Airways. )   \n",
       "3    Budapest_PaRis         10075          [13]       12. Air France   \n",
       "4   Brussels_londOn         10085      [67, 32]          \"Swiss Air\"   \n",
       "\n",
       "       From         To  \n",
       "0    London      paris  \n",
       "1    Madrid      miLAN  \n",
       "2    London  StockhOlm  \n",
       "3  Budapest      PaRis  \n",
       "4  Brussels     londOn  "
      ]
     },
     "execution_count": 13,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df1.From=dftemporary.From.str.capitalize()\n",
    "df1"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>From_To</th>\n",
       "      <th>FlightNumber</th>\n",
       "      <th>RecentDelays</th>\n",
       "      <th>Airline</th>\n",
       "      <th>From</th>\n",
       "      <th>To</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>London_paris</td>\n",
       "      <td>10045</td>\n",
       "      <td>[23, 47]</td>\n",
       "      <td>KLM(!)</td>\n",
       "      <td>London</td>\n",
       "      <td>Paris</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Madrid_milan</td>\n",
       "      <td>10055</td>\n",
       "      <td>[]</td>\n",
       "      <td>&lt;Air France&gt; (12)</td>\n",
       "      <td>Madrid</td>\n",
       "      <td>Milan</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>London_stockholm</td>\n",
       "      <td>10065</td>\n",
       "      <td>[24, 43, 87]</td>\n",
       "      <td>(British Airways. )</td>\n",
       "      <td>London</td>\n",
       "      <td>Stockholm</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Budapest_paris</td>\n",
       "      <td>10075</td>\n",
       "      <td>[13]</td>\n",
       "      <td>12. Air France</td>\n",
       "      <td>Budapest</td>\n",
       "      <td>Paris</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Brussels_london</td>\n",
       "      <td>10085</td>\n",
       "      <td>[67, 32]</td>\n",
       "      <td>\"Swiss Air\"</td>\n",
       "      <td>Brussels</td>\n",
       "      <td>London</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            From_To  FlightNumber  RecentDelays              Airline  \\\n",
       "0      London_paris         10045      [23, 47]               KLM(!)   \n",
       "1      Madrid_milan         10055            []    <Air France> (12)   \n",
       "2  London_stockholm         10065  [24, 43, 87]  (British Airways. )   \n",
       "3    Budapest_paris         10075          [13]       12. Air France   \n",
       "4   Brussels_london         10085      [67, 32]          \"Swiss Air\"   \n",
       "\n",
       "       From         To  \n",
       "0    London      Paris  \n",
       "1    Madrid      Milan  \n",
       "2    London  Stockholm  \n",
       "3  Budapest      Paris  \n",
       "4  Brussels     London  "
      ]
     },
     "execution_count": 18,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df1.From_To=df1.From_To.str.capitalize()\n",
    "df1"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [],
   "source": [
    "# 4. Delete the From_To column from df and attach the temporary DataFrame from the previous questions"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [],
   "source": [
    "df['From_To']=df1['From_To']"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>FlightNumber</th>\n",
       "      <th>RecentDelays</th>\n",
       "      <th>Airline</th>\n",
       "      <th>From_To</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>10045</td>\n",
       "      <td>[23, 47]</td>\n",
       "      <td>KLM(!)</td>\n",
       "      <td>London_paris</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>10055</td>\n",
       "      <td>[]</td>\n",
       "      <td>&lt;Air France&gt; (12)</td>\n",
       "      <td>Madrid_milan</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>10065</td>\n",
       "      <td>[24, 43, 87]</td>\n",
       "      <td>(British Airways. )</td>\n",
       "      <td>London_stockholm</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>10075</td>\n",
       "      <td>[13]</td>\n",
       "      <td>12. Air France</td>\n",
       "      <td>Budapest_paris</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>10085</td>\n",
       "      <td>[67, 32]</td>\n",
       "      <td>\"Swiss Air\"</td>\n",
       "      <td>Brussels_london</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   FlightNumber  RecentDelays              Airline           From_To\n",
       "0         10045      [23, 47]               KLM(!)      London_paris\n",
       "1         10055            []    <Air France> (12)      Madrid_milan\n",
       "2         10065  [24, 43, 87]  (British Airways. )  London_stockholm\n",
       "3         10075          [13]       12. Air France    Budapest_paris\n",
       "4         10085      [67, 32]          \"Swiss Air\"   Brussels_london"
      ]
     },
     "execution_count": 23,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "#5.In the RecentDelays column, the values have been entered into the DataFrame as a list. We would like each first value in its own column, each\n",
    "#.  second value in its own column, and so on. If there isn't an Nth value, the value should be NaN.\n",
    "#.  Expand the Series of lists into a DataFrame named delays, rename the columns delay_1, delay_2, etc. and replace the unwanted RecentDelays column in df with delays."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.3"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
