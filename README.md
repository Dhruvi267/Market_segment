# Best neighborhood for a New Coffee Shop in Toronto
#### Problem
Toronto is a large city with many neighborhoods, each with its own unique characteristics. For a new coffee shop, it is crucial to choose a district that offers the best business opportunities while minimizing competition. This project will analyze the existing coffee shop distribution, population density, and other venue categories to identify the best neighborhood for a new coffee shop.

#### Data
The analysis will be based on the following data sources:</br>
   - Wikipedia: To obtain postal code data, including names of neighborhoods, boroughs, and geographical coordinates.</br>
   - OpenCage Geocoder API: To look up the latitudes and longitudes of all neighborhoods.</br>
   - Foursquare API: To obtain the number of coffee shops, their types, and locations in all neighborhoods.</br>
   - Population Data: To get the population density of each neighborhood.</br>

#### Pseudocode

1. Import necessary libraries and download the csv for population

2. Download Postal code Data from Wikipedia
   - Read wikipage to create dataframe with Toronto geospacial data.
   - Identify and extract the relevant table containing  data
   - Create a dataframe with columns: Postcode, Borough, Neighborhood, latitude, longitude.

3. Add population data to the data frame
   - read the csv 
   - Append to the dataframe

4. Explore Dataset
   - Use geopy library to get the latitude and longitude values of Toronto
   - Create a map of Toronto with postal codes superimposed
   - Define Foursquare API credentials and version

5. Explore First District in the Dataframe
   - Get the neighborhoods's name, latitude, and longitude values
   - Create a GET request URL for Foursquare API to get top 100 venues within a radius of 500 meters
   - Send the GET request and examine the results
   - Clean the JSON response and structure it into a pandas dataframe

6. Explore All postal codes in Toronto
   - Create a function to repeat the process for all postal codes
   - Run the function to get venues for each neighborhoods and create a new dataframe 
   - Check the properties of the resulting dataframe (size, number of venues, unique categories)

7. Examine Each neighborhood
   - Group rows by district and calculate the mean frequency of occurrence of each category
   - Print each neighborhood along with the top 5 most common venues
   - Create a new dataframe with venues in descending order

8. Cluster postal codes
   - Run k-means clustering to cluster the postal codes into 6 clusters
   - Create a new dataframe for the cluster and the top 10 venues for each district
   - Visualize the resulting clusters using folium

9. Examine Clusters
   - Examine each cluster and determine the discriminating venue categories
   - Assign a name to each cluster based on the defining categories
