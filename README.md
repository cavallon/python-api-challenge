# python-api-challenge

WeatherPy has all solution files, and the api_keys.py file. 
output_data has the required csv and image files from running the code. 

Please read the following for both WeatherPy.ipynb and VacationPy.ipynb: 

For WeatherPy.ipynb

    The main url that was used for this file was: https://api.openweathermap.org/data/2.5/weather?
    In order to pull the information I needed to complete this code, the following parameters were used:
        lat - this is a required parameter and stands for Latitude. 
        lon - this is a required paramter and stands for Longitude.
        appid - equates to the API key needed to make the API call. Set to my personal API for OpenWeather.
        units - this is an optional parameter that I used in order to convert the temperature to Celsius. 
        q - this is a required parameter that is used to get city name, state code, and country code. 

    After verifying the parameters needed from OpenWeather, I combined the main url with the parameters in order to make the api call and retrieve the data needed for this project. The output was formatted as json. 

    From the json output, I parsed out the data in the following way:
        "coord" contains "lon", "lat, short for Longitude and Latitude 

        "main" contains "temp_max" and "humidity, which defines the current maximum temperature and the humidity level as a percentage. 

        "clouds" contains "all", which gives me a value for cloudiness as a percentage. 

        "wind" contains "speed", which provides a value for the wind speed as meters per second. 

        "sys" contains "country", which provides a country code. 

        "dt" provides the time of data calculation as unix, UTC. 

    Once all of these items were finalized, I was able to move through the project and complete the required calculations, as well as plot the necessary charts to calculate the final results. 


For VacationPy.ipynb

    In the first part of this project I used hvplot to create the map with different point sizes based on humidity levels. The larger the size of the point, the higher the humidity. After this I narrowed down the data frame to find my ideal weather condition. I then added a blank column for Hotel Names. In order to search for a hotel within 10,000 meters of each coordinate I used my Geoapify API. 

    The base url that I used was: https://api.geoapify.com/v2/places
    In addition to the base url, I also needed to add parameters to the url in order to get the required data for this project. 
    
    The initial parameters I used were:
        Radius set to 10,000 metres (to be used with "filter").

        "categories" which contains a comma separated list of place categories. Of these categories I selected "accommodation.hotel" in order to get the name of only hotels within the required distance. 

        "apikey" which equals my API key for accessing the data. 

        "limit" set to 20 as a maximum number of results per page. 

    After setting the intial parameters, I included the "filter" and "bias" parameters within the subsequent loop, to be added to the initial params dictionary. 

        "filter" is able to filter places by bounds, circle, geometry, or countries. I used the bounds and the radius with this. 

        "bias" enables the program to search first near the location, and if nothing is found, it will search farther and farther away until it finds something, or the maximum limit of 50km is reached. I used the longitude and latitude as starting points for this. 

        Once the information was received in the json format, the hotel name was found to be located within "features" and "properties". The try and except code was added in order to enable the program to move forward with the code if no hotel name is found. If the try and except feature is not added, the code will not complete the tasks it needs to do in order to finish running the program. 

        After running the full program, a list was created with the nearest hotels. This list was then mapped using hvplot to visualize the data points.  

    -End of README.md
