# What is the relationship between geolocation and weather metrics?
## Overview
OpenWeatherMap and Google Maps APIs are used to determine the relationship between the location of a random set of cities and current weather conditions in each of these cities on a particular day. The data is processed and visualised in a [jupyter notebook](https://github.com/rochiecuevas/WeatherPy/blob/master/WeatherPy.ipynb). Details and notes are found in the notebook.

## Procedure at a glance
There are three main steps in retrieving and in processing the data:
1. __Coordinate generation.__ 2000 random numbers are generated between -90 and 90 for latitude, and between -180 and 180 for longitude. The cities nearest to these coordinates are determined using Citipy. There are at least 500 cities identified.
2. __Geolocating cities.__ The coordinates of the cities are determined using Google Maps' Geocoding API. 
3. __Data cleaning.__ Cities with missing coordinates are dropped, as well as duplicates.
4. __Weather data retrieval.__ Weather metrics (wind speed, humidity, cloudiness, and temperature) are extracted from OpeanWeatherMap through its API.
5. __Visualisation.__ Scatterplots are used to visualise the extracted data.

## Is it cloudy with a chance of meatballs anywhere in the world on October 14th, 2018?
A set of 629 cities from all over the world were randomly selected out of 2000 coordinates. Plotting the cities on a grid of latitudes (y-axis) and longitudes (x-axis) revealed that the cities followed the general shapes of the different continents. It revealed that many cities follow the coastlines; inner parts of of Africa, of Australia, and of South America had empty regions. Perhaps, there were only a few cities in these regions; the chance of randomly selecting these 

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/city_positions_20181014.png)<br>
Fig. 1. Cities randomly selected (N = 629)

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/lat_temp_20181014.png)<br>
Fig. 2. Temperature readings (°F) across latitudes. Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/lat_hum_20181014.png)<br>
Fig. 3. Humidity (%) across latitudes. Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/lat_cloud_20181014.png)<br>
Fig. 4. Cloudiness (%) across latitudes. Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/lat_wind_20181014.png)<br>
Fig. 5. Wind speed (mph) across latitudes. Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/long_temp_20181014.png)<br>
Fig. 6. Temperature readings (°F) across longitudes. Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/long_hum_20181014.png)<br>
Fig. 7. Humidity (%) across longitudes. Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/long_cloud_20181014.png)<br>
Fig. 8. Cloudiness (%) across longitudes. Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/long_wind_20181014.png)<br>
Fig. 9. Wind speed (mph) across longitudes. Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/hum_wind_20181014.png)<br>
Fig. 10. Relationship between wind speed (mph) and humidity (%). Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/hum_cloud_20181014.png)<br>
Fig. 11. Relationship between cloudiness (%) and humidity (%). Data retrieved from OpenWeatherMap API on 2018-10-14.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/cloud_wind_20181014.png)<br>
Fig. 12. Relationship between cloudiness (%) and wind speed (mph). Data retrieved from OpenWeatherMap API on 2018-10-14.

