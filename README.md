# python-api-challenge
---
## Description
The goal of this project is to showcase and make use of API and Geocoding skills. There are two parts, namely WeatherPy and VacationPy. In WeatherPy, geographic data is collected on a randomly generated list of cities for which weather conditions are then recorded for analysis to uncover any trends. In VacationPy, cities with desirable weather conditions are short listed, hotels within the city are searched for, then the cities are plotted on a map along with hotel names if available.

### WeatherPy
This part is mainly carried out within a jupyter notebook in the following steps:
- A list of random latitude and longitude coordinates is generated using a random number generator
- Using the module citypy and a loop, any city near each coordinate is found and added to a list, provided it has not already been added
- API calls are made to the OpenWeatherMap API to retrieve exact coordinates, maximum temperature, humidity, cloudiness and wind speed for each city
- This information is stored in a Pandas DataFrame which is also exported to a CSV file in the 'Output Data' folder
- Using the matplotlib module scatter plots of latitude vs the various weather parameters collected are created and the images are saved in 'Output Data'
- The data is split into two DataFrames, one for the Southern Hemisphere and one for the Northern Hemisphere
- Linear regression models are generated for latitude vs each weather parameter for each hemisphere using a defined function
- Analysis is carried out on the regression models and added to the jupyter notebook

### VacationPy
This part is also carried out within a jupyter notebook, in the following steps:
- The data on cities and weather is read in from the previously generated CSV
- Using the hvPlot API a map is generated showing each city in the data as a point with the size corresponding to the humidity
- The data is shortlisted using the Pandas loc function to include only cities with ideal weather conditions, any rows with null values are also dropped
- An empty 'Hotel Name' column is created and the rows are looped through to find the first hotel within 10000 metres of each city via the Geoapify API
- The hotel names are appended to the empty column if found
- An hvPlot map is generated showing each of the ideal cities as a point with the name of the hotel showing up in the hover message
