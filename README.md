
Exploring Financial Data using Nasdaq Data Link API
#importing necessary libraries together with the config.py file

import requests
import json
import pandas as pd
import config

# configuring the api_key
api_key = config.api_key
# base url

api_url='https://data.nasdaq.com/api/v3/datatables/MER/F1.json'

# our `parameters` dictionary

parameters = {
    'api_key': api_key,
    'qopts.per_page': 10  # Number of rows to fetch

}

# Fetching the data and converting it to json

json_data=requests.get(api_url, params=parameters).json()

# printing the json data

print(json_data)
{'datatable': {'data': [[2438, 1868192544, -1802, 10.481948, '2011-06-30', 'Q2', 'U', 'EUR', 'True', 'Deutsche Bank AG', 'Deutsche Bank AG', 'Active', 'DEU', 'Europe', 1159508, '5.1.1', 'DB', 'NYS', 'Taunusanlage 12', None, None, None, 'Frankfurt am Main', None, 'DEU', '60325', '(49) 69 910 00', '(49) 69 910 34 225', 'www.db.com', '2022-12-31', 'Accrued Expenses Turnover', 'Derived'], [2438, 1868216112, -1802, 8.161754, '2011-09-30', 'Q3', 'U', 'EUR', 'True', 'Deutsche Bank AG', 'Deutsche Bank AG', 'Active', 'DEU', 'Europe', 1159508, '5.1.1', 'DB', 'NYS', 'Taunusanlage 12', None, None, None, 'Frankfurt am Main', None, 'DEU', '60325', '(49) 69 910 00', '(49) 69 910 34 225', 'www.db.com', '2022-12-31', 'Accrued Expenses Turnover', 'Derived'], [2438, 1885063456, -1802, 10.788213, '2012-06-30', 'Q2', 'U', 'EUR', 'True', 'Deutsche Bank AG', 'Deutsche Bank AG', 'Active', 'DEU', 'Europe', 1159508, '5.1.1', 'DB', 'NYS', 'Taunusanlage 12', None, None, None, 'Frankfurt am Main', None, 'DEU', '60325', '(49) 69 910 00', '(49) 69 910 34 225', 'www.db.com', '2022-12-31', 'Accrued Expenses Turnover', 'Derived'], [2438, 1885087024, -1802, 9.437545, '2012-09-30', 'Q3', 'U', 'EUR', 'True', 'Deutsche Bank AG', 'Deutsche Bank AG', 'Active', 'DEU', 'Europe', 1159508, '5.1.1', 'DB', 'NYS', 'Taunusanlage 12', None, None, None, 'Frankfurt am Main', None, 'DEU', '60325', '(49) 69 910 00', '(49) 69 910 34 225', 'www.db.com', '2022-12-31', 'Accrued Expenses Turnover', 'Derived'], [2438, 1901934112, -1802, 8.755041, '2013-06-30', 'Q2', 'U', 'EUR', 'True', 'Deutsche Bank AG', 'Deutsche Bank AG', 'Active', 'DEU', 'Europe', 1159508, '5.1.1', 'DB', 'NYS', 'Taunusanlage 12', None, None, None, 'Frankfurt am Main', None, 'DEU', '60325', '(49) 69 910 00', '(49) 69 910 34 225', 'www.db.com', '2022-12-31', 'Accrued Expenses Turnover', 'Derived'], [2438, 1901957680, -1802, 8.109493, '2013-09-30', 'Q3', 'U', 'EUR', 'True', 'Deutsche Bank AG', 'Deutsche Bank AG', 'Active', 'DEU', 'Europe', 1159508, '5.1.1', 'DB', 'NYS', 'Taunusanlage 12', None, None, None, 'Frankfurt am Main', None, 'DEU', '60325', '(49) 69 910 00', '(49) 69 910 34 225', 'www.db.com', '2022-12-31', 'Accrued Expenses Turnover', 'Derived'], [2438, 1901981184, -7562, 7.047783, '2013-12-31', 'A', 'N', 'EUR', 'True', 'Deutsche Bank AG', 'Deutsche Bank AG', 'Active', 'DEU', 'Europe', 1159508, '5.1.1', 'DB', 'NYS', 'Taunusanlage 12', None, None, None, 'Frankfurt am Main', None, 'DEU', '60325', '(49) 69 910 00', '(49) 69 910 34 225', 'www.db.com', '2022-12-31', 'Cash Flow Per Share', 'Cash Flow'], [17630, 1851369024, -4524, 161000000.0, '2010-12-31', 'Q4', 'N', 'CAD', 'True', 'BCE Inc', 'BCE Inc', 'Active', 'CAN', 'North America', 718940, '6.1.2', 'BCE', 'NYS', '1 Carrefour Alexander-Graham-Bell', 'Building A', '8th Floor', None, 'Verdun', 'Quebec', 'CAN', 'H3E 3B3', '800 339-6353', '514 786-3970', 'www.bce.ca', '2022-12-31', 'Operating Income', 'Income Statement'], [17630, 1851369024, -5917, 3.440906, '2010-12-31', 'Q4', 'N', 'CAD', 'True', 'BCE Inc', 'BCE Inc', 'Active', 'CAN', 'North America', 718940, '6.1.2', 'BCE', 'NYS', '1 Carrefour Alexander-Graham-Bell', 'Building A', '8th Floor', None, 'Verdun', 'Quebec', 'CAN', 'H3E 3B3', '800 339-6353', '514 786-3970', 'www.bce.ca', '2022-12-31', 'Operating Margin', 'Derived'], [17630, 1868192544, -1016, 2.631808, '2011-06-30', 'Q2', 'U', 'CAD', 'True', 'BCE Inc', 'BCE Inc', 'Active', 'CAN', 'North America', 718940, '6.1.2', 'BCE', 'NYS', '1 Carrefour Alexander-Graham-Bell', 'Building A', '8th Floor', None, 'Verdun', 'Quebec', 'CAN', 'H3E 3B3', '800 339-6353', '514 786-3970', 'www.bce.ca', '2022-12-31', 'Interest Coverage', 'Derived']], 'columns': [{'name': 'compnumber', 'type': 'Integer'}, {'name': 'reportid', 'type': 'Integer'}, {'name': 'mapcode', 'type': 'Integer'}, {'name': 'amount', 'type': 'BigDecimal(36,14)'}, {'name': 'reportdate', 'type': 'Date'}, {'name': 'reporttype', 'type': 'String'}, {'name': 'auditorstatus', 'type': 'String'}, {'name': 'currency', 'type': 'String'}, {'name': 'consolidated', 'type': 'String'}, {'name': 'longname', 'type': 'String'}, {'name': 'shortname', 'type': 'String'}, {'name': 'status', 'type': 'String'}, {'name': 'countrycode', 'type': 'String'}, {'name': 'region', 'type': 'String'}, {'name': 'cik', 'type': 'Integer'}, {'name': 'mic', 'type': 'String'}, {'name': 'ticker', 'type': 'String'}, {'name': 'exchange', 'type': 'String'}, {'name': 'address1', 'type': 'String'}, {'name': 'address2', 'type': 'String'}, {'name': 'address3', 'type': 'String'}, {'name': 'address4', 'type': 'String'}, {'name': 'city', 'type': 'String'}, {'name': 'statecode', 'type': 'String'}, {'name': 'country', 'type': 'String'}, {'name': 'zipcode', 'type': 'String'}, {'name': 'phonenumber', 'type': 'String'}, {'name': 'faxnumber', 'type': 'String'}, {'name': 'website', 'type': 'String'}, {'name': 'fye', 'type': 'Date'}, {'name': 'indicator', 'type': 'String'}, {'name': 'statement', 'type': 'String'}]}, 'meta': {'next_cursor_id': 'djFfMTAyNTkwN18xNzA3NDk1ODgz'}}
Processing the JSON Data into a DataFrame
api_url = 'https://data.nasdaq.com/api/v3/datatables/MER/F1.json'
parameters = {
    'api_key': api_key,
    'qopts.per_page': 10000  

}
json_data=requests.get(api_url, params=parameters).json()

data = json_data['datatable']['data']
columns = [col['name'] for col in json_data['datatable']['columns']]

# Create DataFrame from a list of list
df_metric = pd.DataFrame(data, columns=columns)
df_metric.head()
compnumber	reportid	mapcode	amount	reportdate	reporttype	auditorstatus	currency	consolidated	longname	...	city	statecode	country	zipcode	phonenumber	faxnumber	website	fye	indicator	statement
0	2438	1868192544	-1802	10.481948	2011-06-30	Q2	U	EUR	True	Deutsche Bank AG	...	Frankfurt am Main	None	DEU	60325	(49) 69 910 00	(49) 69 910 34 225	www.db.com	2022-12-31	Accrued Expenses Turnover	Derived
1	2438	1868216112	-1802	8.161754	2011-09-30	Q3	U	EUR	True	Deutsche Bank AG	...	Frankfurt am Main	None	DEU	60325	(49) 69 910 00	(49) 69 910 34 225	www.db.com	2022-12-31	Accrued Expenses Turnover	Derived
2	2438	1885063456	-1802	10.788213	2012-06-30	Q2	U	EUR	True	Deutsche Bank AG	...	Frankfurt am Main	None	DEU	60325	(49) 69 910 00	(49) 69 910 34 225	www.db.com	2022-12-31	Accrued Expenses Turnover	Derived
3	2438	1885087024	-1802	9.437545	2012-09-30	Q3	U	EUR	True	Deutsche Bank AG	...	Frankfurt am Main	None	DEU	60325	(49) 69 910 00	(49) 69 910 34 225	www.db.com	2022-12-31	Accrued Expenses Turnover	Derived
4	2438	1901934112	-1802	8.755041	2013-06-30	Q2	U	EUR	True	Deutsche Bank AG	...	Frankfurt am Main	None	DEU	60325	(49) 69 910 00	(49) 69 910 34 225	www.db.com	2022-12-31	Accrued Expenses Turnover	Derived
5 rows × 32 columns

Understanding the Dataset
necessary_columns=['reportid','reportdate','reporttype','amount','longname','country','region','indicator','statement']
Filtering the DataFrame for Analysis
df_metric=df_metric[necessary_columns]
filtered_df=df_metric[df_metric['indicator']=='Accrued Expenses Turnover']
filtered_df['indicator'].describe()
count                           139
unique                            1
top       Accrued Expenses Turnover
freq                            139
Name: indicator, dtype: object
Enhancing the DataFrame
def update_country_name(name):
    if name=='USA':
        name='United State of America'
    elif name=='JPN':
        name='Japan'
    elif name=='CYM':
        name='Cayman Islands'
    elif name=='BHS':
        name='Bahamas'
    elif name=='DEU':
        name='Germany'
    else:
        name='Ireland'
    
    return name
filtered_df=filtered_df.copy()
filtered_df['country_name']=filtered_df['country'].apply(update_country_name)
filtered_df.columns=['report_id','report_date','report_type',
                   'amount','company_name','country','region',
                   'indicator','statement','country_name']
updated_df=filtered_df.copy()
updated_df['country_name'].value_counts()
United State of America    31
Ireland                    29
Japan                      27
Cayman Islands             27
Bahamas                    19
Germany                     6
Name: country_name, dtype: int64
understanding financial trends over time
import matplotlib.pyplot as plt


# # Filter for the time period 2010 to 2015
updated_df['report_date'] = pd.to_datetime(updated_df['report_date'])
updated_df = updated_df[(updated_df['report_date'].dt.year >= 2010) & (updated_df['report_date'].dt.year <= 2015)]

# Selecting relevant columns. Assuming 'company_name' is the column with company names.
# Replace 'company_name', 'reportdate', and 'metric_value_column' with actual column names.
relevant_data = updated_df[['company_name', 'report_date', 'amount']].copy()

# Plotting the trend
plt.figure(figsize=(12, 6))

for company in relevant_data['company_name'].unique():
    company_data = relevant_data[relevant_data['company_name'] == company]
    plt.plot(company_data['report_date'], company_data['amount'], label=company)

plt.title('Trend Analysis of Accrued Expenses Turnover (2010-2015)')
plt.xlabel('Report Date')
plt.ylabel('Accrued Expenses Turnover')
plt.xticks(rotation=45)
plt.legend(title='Company', bbox_to_anchor=(1.05, 1), loc='upper left')
plt.tight_layout()
plt.show()

Geographical Region Analysis
country_avg = updated_df.groupby('country_name')['amount'].mean()
# Plotting for Geographical Region Analysis
plt.figure(figsize=(12, 6))
country_avg.sort_values(ascending=False).plot(kind='bar')
plt.title('Average Financial Metric by Country')
plt.xlabel('Country')
plt.ylabel('Average Amount')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
