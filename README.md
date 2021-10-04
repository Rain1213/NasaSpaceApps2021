# NasaSpaceApps2021

### UNIVERSAL EVENT
### CHALLENGE: **Warning: Things are heating up!**
### TEAM: **HEWA MAP**

</br>

This repository contains various directories, each containing different datasets and .ipynb files. Our vision is to use them to create a wonderful and an interactive web app that would allow users to see areas with the most forecasted heat risk 7 days out, and recommend actions for users to prepare for an oncoming heatwave.

This Readme File would explain the reasoning behind each directories:
</br>
</br>

### <mark>**Wet Bulb Temperature**</mark>
This contains a dot .ipynb file where an API is created that takes in either 'Latitude-Logitude' or 'Zip-Code' values and presents the user with Forecast Temperature and Relative Humidity Values. A function equates the value of 'Wet Bulb Temperature' using the 2 values. Since the values are being forecasted (6 hours gap for 7 days), we can get Wet Bulb Temperature Forecast values and can effectively predict Heatwaves.

</br>

### <mark>**Google Trends**</mark>
TrendsByState.ipynb uses Plotly library to plot Choropleth from the data extracted from Google Trends. The following .ipynb is plotting the intensity of search results via state-to-state in the United States. Plotly only accepts 2-letter state code or FIPS values to plot Choropleth Maps of State or Counties respectively. The /geoMapState.csv file is a csv file with Names of States converted into State Codes. Rest of the csv files(time and place) will be available to you at  ```/Other Trend Dataset``` directory.


</br>

### <mark>**Drought Area**</mark>
The ```/DroughtOverTime.csv``` dataset is processed form of the dataset downloaded from [Drought Monitor Website](https://droughtmonitor.unl.edu/DmData/DataDownload/ComprehensiveStatistics.aspx). This dataset was fed to IBM Watson's AutoAI Service.

To access the API in python, you can follow the below code:
```
import requests

# NOTE: you must manually set API_KEY below using information retrieved from your IBM Cloud account.
API_KEY = "<your API key>"
token_response = requests.post('https://iam.cloud.ibm.com/identity/token', data={"apikey": API_KEY, "grant_type": 'urn:ibm:params:oauth:grant-type:apikey'})
mltoken = token_response.json()["access_token"]

header = {'Content-Type': 'application/json', 'Authorization': 'Bearer ' + mltoken}

# NOTE: manually define and pass the array(s) of values to be scored in the next line
payload_scoring = {"input_data": [{"fields": [array_of_input_fields], "values": [array_of_values_to_be_scored, another_array_of_values_to_be_scored]}]}

response_scoring = requests.post('https://us-south.ml.cloud.ibm.com/ml/v4/deployments/757b711d-3253-4533-86e7-ac9cc7533812/predictions?version=2021-10-04&version=2021-10-04', json=payload_scoring, headers={'Authorization': 'Bearer ' + mltoken})
print("Scoring response")
print(response_scoring.json())

```


</br>
</br>

The Main Idea behind this Project was to combine all three factors:
- Wet Bulb Temperature
- Google Trend Data
- Drought Area

and develop a 3 level Heatwave warning system that would display warning levels in 3 colour values:

- Green: Safe
- Yellow: Moderate Heatwave
- Red: Severe Heatwave

</br>

## **FLOWCHART**


<center><img align="center" alt="detailPage" src="https://raw.githubusercontent.com/Rain1213/NasaSpaceApps2021/main/images/NasaSpaceApps2021.png" /></center>
