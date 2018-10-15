## What is WeatherPy?
WeatherPy is a nifty tool that creates scatterplots of weather metrics by geolocation for more than 500 randomly selected cities. 

The coordinates of these cities are determined using Google Maps' Geocoding API. Weather data for each city is extracted from OpenWeatherMap API. Each time the script is run, a different number and set of cities will be generated. Weather changes on a day-to-day basis, leading to different results. Outputs generated from the script are date-stamped, making it easy to differentiate results obtained on different dates.

__Note:__ As an example of outputs from WeatherPy, weather data was extracted on October 14th. Insights about geolocation and weather data are included in this report. 

## Procedure at a glance
There are five main steps in retrieving and in processing the data:
1. __Coordinate generation.__ 2000 random numbers are generated between -90 and 90 for latitude, and between -180 and 180 for longitude. The cities nearest to these coordinates are determined using Citipy. There are at least 500 cities identified.
2. __Geolocating cities.__ The coordinates of the cities are determined using Google Maps' Geocoding API. 
3. __Data cleaning.__ Cities with missing coordinates are dropped, as well as duplicates.
4. __Weather data retrieval.__ Weather metrics (wind speed, humidity, cloudiness, and temperature) are extracted from OpeanWeatherMap through its API.
5. __Visualisation.__ Scatterplots are used to find trends in the extracted data.

![Alt text](https://g.gravizo.com/svg?digraph%20G%20%7B%0A...%20%20%20%20%20size%20%3D%224%2C4%22%3B%0A...%20%20%20%20%20main%20%5Bshape%3Dbox%5D%3B%0A...%20%20%20%20%20main%20-%3E%20parse%20%5Bweight%3D8%5D%3B%0A...%20%20%20%20%20parse%20-%3E%20execute%3B%0A...%20%20%20%20%20main%20-%3E%20init%20%5Bstyle%3Ddotted%5D%3B%0A...%20%20%20%20%20main%20-%3E%20cleanup%3B%0A...%20%20%20%20%20execute%20-%3E%20%7B%20make_string%3B%20printf%7D%0A...%20%20%20%20%20init%20-%3E%20make_string%3B%0A...%20%20%20%20%20edge%20%5Bcolor%3Dred%5D%3B%0A...%20%20%20%20%20main%20-%3E%20printf%20%5Bstyle%3Dbold%2Clabel%3D%22100%20times%22%5D%3B%0A...%20%20%20%20%20make_string%20%5Blabel%3D%22make%20a%20string%22%5D%3B%0A...%20%20%20%20%20node%20%5Bshape%3Dbox%2Cstyle%3Dfilled%2Ccolor%3D%22.7%20.3%201.0%22%5D%3B%0A...%20%20%20%20%20execute%20-%3E%20compare%3B%0A...%20%20%20%7D)

## October 14th, 2018: Cloudy with a chance of meatballs?
A set of 629 cities from all over the world were randomly selected out of 2000 coordinates. Plotting the cities on a grid of latitudes (y-axis) and longitudes (x-axis) revealed that the cities followed the general shapes of the different continents. It revealed that many cities follow the coastlines; inner parts of of Africa, of Australia, and of South America had empty regions. The sparse region in Australia is most likely the desert [Outback](http://www.ga.gov.au/scientific-topics/national-location-information/landforms/deserts). In South America, the empty regions could include the [Patagonian Steppe](https://www.britannica.com/place/Patagonia-region-Argentina) (Argentina), [La Guajira desert](https://www.cnn.com/travel/article/colombia-desert-la-guajira/index.html) (Colombia), and the [Amazon rainforest](https://www.britannica.com/place/Amazon-Rainforest). More cities were selected south of the equator in Africa; the northern part of the continent is dominated by the [Sahara desert](https://www.livescience.com/23140-sahara-desert.html). It was notable that cities from small island nations in the Pacific were included in the random selection.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/city_positions_20181014.png)<br>
Fig. 1. Cities randomly selected (N = 629)<br><br>

Temperatures recorded on October 14, 2018 indicate that cities between the Equator and the 20th parallel north registered the warmest conditions. As cities grew farther north from the Equator, the temperature dropped. Likewise, the temperatures observed in the cities below the Equator went lower as they approached the South Pole. It was also observed that the temperatures were lower in the cities between the 40th and the 60th parallel north than in the cities between the 40th and the 60th parallel south. [Winter](https://sciencing.com/differences-between-northern-southern-hemisphere-8260091.html) is coming to the Northern Hemisphere but summer is approaching in the Southern Hemisphere.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/lat_temp_20181014.png)<br>
Fig. 2. Temperature readings (°F) across latitudes.<br><br>

[Humidity](https://www.nationalgeographic.org/encyclopedia/humidity/) is the concentration of moisture in the air. Unlike temperature which has a recognisable pattern, the data for humidity suggests that there is no direct linear relationship between humidity and latitude. However, cities in the [tropics](https://www.nationalgeographic.org/encyclopedia/tropics/) (between -23.5° and 23.5°) tended to have less variation in humidity than cities in the [temperate regions](http://www.polaris.iastate.edu/NorthStar/Unit5/unit5_sub1.htm) (north: 23.5–66.5° and south: -23.5– -66.5°). At the polar north, the cities tended to have humidiy readings close to 100%. 

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/lat_hum_20181014.png)<br>
Fig. 3. Humidity (%) across latitudes.<br><br>

There was no noticeable pattern between cloudiness and latitude. 

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/lat_cloud_20181014.png)<br>
Fig. 4. Cloudiness (%) across latitudes.<br><br>

Wind speeds indicate that there were no active typhoons or hurricanes in the randomly selected cities because the wind speed records were below [74 mph](https://www.nhc.noaa.gov/aboutsshws.php). On the other hand, winds had more uniform speeds in cities located near the Equator and the speeds became more varied the farther north or south the cities were. In the Southern Hemisphere, the area around 40 and 50° latitude is known as the ["Roaring Forties"](https://oceanservice.noaa.gov/facts/roaring-forties.html) because of [gale force winds](https://en.wikipedia.org/wiki/Gale). But on this particular day, the wind was relatively weak, with only one city registering wind at around 34 mph. Near the Equator, the winds are typically [calm](https://oceanservice.noaa.gov/facts/doldrums.html) because the air in here tend to go upwards, which causes low movement of air on the surface.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/lat_wind_20181014.png)<br>
Fig. 5. Wind speed (mph) across latitudes.<br><br>

There was no apparent relation between longitude and temperature.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/long_temp_20181014.png)<br>
Fig. 6. Temperature readings (°F) across longitudes.<br><br>

There was no observable trend between longitude and humidity either.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/long_hum_20181014.png)<br>
Fig. 7. Humidity (%) across longitudes.<br><br>

The amount of cloud cover also did not appear to be related with the distance of each city from the Prime Meridian.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/long_cloud_20181014.png)<br>
Fig. 8. Cloudiness (%) across longitudes.<br><br>

From east to west, the winds in the selected cities were mostly slow-moving. Based on the scatterplot, wind speeds tended to vary more at longitudes that coincide with longer landmasses (north to south). With the range largely uniform, the plot indicates that the variation is on the distance from the Equator rather than the distance from the Prime Meridian.  

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/long_wind_20181014.png)<br>
Fig. 9. Wind speed (mph) across longitudes.<br><br>

There was no obvious relationship between wind speed and humidity. But this graph indicates that most of the cities included in the study had 60–100% humidity. This indicates that more human settlements are found in more humid areas than in arid deserts, supporting the presumption that the sparse areas inside landmass outlines in the latitude-longitude matrix are deserts. And with the cities dotting the coastline, it is just expected to observe the predominance of humid cities.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/hum_wind_20181014.png)<br>
Fig. 10. Relationship between wind speed (mph) and humidity (%). <br><br>

Though cities with humidity ranging from 0 to 100% could have 0% cloudiness, it was observed that the range of cloudiness tended to increase with humidity. 

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/hum_cloud_20181014.png)<br>
Fig. 11. Relationship between cloudiness (%) and humidity (%).<br><br>

Cloudiness did not seem to be related with wind speed.

![alt text](https://github.com/rochiecuevas/WeatherPy/blob/master/Images/cloud_wind_20181014.png)<br>
Fig. 12. Relationship between cloudiness (%) and wind speed (mph).<br><br>

