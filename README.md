**Weather and Vacation Planning API Challenge**

This project is divided into two sub-challenges: WeatherPy and VacationPy. The first sub-challenge, WeatherPy, focuses on retrieving weather data from the OpenWeatherMap API for around 500 cities in the world. The second sub-challenge, VacationPy, uses the weather data from the CSV generated in WeatherPy to help plan a vacation by locating nearby hotels using the Geoapify API.

**WeatherPy: Retrieving Weather Data**

**1. Data Collection**
The Citipy library is used to obtain a random selection of longitude and latitude coordinates, and the nearest city to each coordinate.
For each identified city, the weather data is fetched from the OpenWeatherMap API, and the following information is collected:
Latitude
Longitude
Maximum Temperature
Humidity
Cloud Cover
Wind Speed
City Country
Date
The weather data is stored in a list called city_data.

**2. Data Storage**
A pandas DataFrame is created from the city_data list, and this DataFrame is saved as a CSV file, which will be used in the VacationPy task.

**3. Scatter Plots**
Scatter plots are generated using the collected weather data to visualize relationships between different variables:
Latitude vs. Temperature (°C)
Latitude vs. Humidity (%)
Latitude vs. Cloudiness (%)
Latitude vs. Wind Speed (m/s)
A function is implemented to generate the scatter plots with dynamic titles and labels, minimizing repetitive code.

**4. Linear Regression**
The DataFrame is split into two subsets: Northern Hemisphere and Southern Hemisphere.
A function is created to compute linear regression for each of the following relationships:
Northern Hemisphere: Temperature vs. Latitude
Southern Hemisphere: Temperature vs. Latitude
Northern Hemisphere: Humidity vs. Latitude
Southern Hemisphere: Humidity vs. Latitude
Northern Hemisphere: Cloudiness vs. Latitude
Southern Hemisphere: Cloudiness vs. Latitude
Northern Hemisphere: Wind Speed vs. Latitude
Southern Hemisphere: Wind Speed vs. Latitude
For each plot, the linear regression line and equation are displayed.

**VacationPy: Vacation Planning**

**1. Plotting Cities on a World Map**
Using the CSV file generated in WeatherPy, the cities are plotted on a world map using hvplot.
The size of each marker is determined by the city's humidity level.
Each city is colored differently for clarity.

**2. Filtering Cities**
To reduce the number of cities displayed, several conditions are applied:
Temperature should be between 0°C and 12°C.
Cloudiness should be not more than 90%.
This filtered dataset is renamed to hotel_df, which contains the following columns:
City
Country
Longitude
Latitude
Humidity
Hotel Name (empty column added to store hotel data)

**3. Finding Hotels**
Using the Geoapify API, the nearest hotel to each city in the hotel_df is located:
The hotel must be within 10 km of the city's latitude and longitude.
The name of the hotel is added to the Hotel Name column of the hotel_df.
Cities without a nearby hotel are filtered out.

**4. Plotting the Final Map**
A final world map is generated showing cities that met the filtering conditions.
Each point on the map includes the city’s Hotel Name and Country in the hover message.

**Technologies Used**

**OpenWeatherMap API:** For retrieving weather data.
**Geoapify API:** For locating nearby hotels.
**Citipy:** For finding the nearest city based on random coordinates.
**Pandas:** For data manipulation and storage in CSV format.
**Matplotlib/Seaborn:** For creating scatter plots.
**hvplot:** For plotting data on world maps.
