# Best neighborhood for a New Coffee Shop in Toronto
#### Problem
Toronto is a large city with many neighborhoods, each with its own unique characteristics. For a new coffee shop, it is crucial to choose a district that offers the best business opportunities while minimizing competition. This project will analyze the existing coffee shop distribution, population density, and other venue categories to identify the best neighborhood for a new coffee shop in Toronto.
#### Data
The analysis will be based on the following data sources:</br>
   - Wikipedia: To obtain postal code data : https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M</br>
   - Population data : https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=9810001901</br>
   - Income data: Data: https://www12.statcan.gc.ca/census-recensement/2016/dp-pd/prof/details/download-telecharger/comp/page_dl-tc.cfm?Lang=E ["Forward sortation areas (FSAs)]</br>
   - Foursquare API to obtain venues data : https://api.foursquare.com/v2/venues/explore?&client_id={}&client_secret={}&v={}&ll={},{}&radius={}&limit={}</br>
#### Pseudocode
1. Scrape wikipedia Postal code Data:
   - clean the postal code data and create a data frame.
   - Confirm if we have all the postal codes.
2. Add latitude and longitude to the postal code data:
   - Clean the data of NUll and retain only the useable data.
3. Get population data:
   - Download the csv from stats canada.
   - Read and filter the csv for Toronto postal codes.
   - Save the population per postal code as a data frame.
4. Get Income data:
   - Download the csv from stats canada.
   - Clean the csv for Toronto relevant lines.
   - Read through the Toronto relevant lines.
   - Save the average income per postal code as a data frame.
5. Clean and merge the data frames:
   - Check for duplicates, null values and merge the data frames.
   - Final data frame to have - Postal Code,Borough,Neighborhood,Latitude,Longitude,Population,Average Income.
6. Plot the Postal codes on a map.
7. Plot charts:
   - Plot the top income postal codes/Neighborhoods.
   - Plot the top populated postal codes/Neighborhoods.
8. Setup the API credentials.
9. Call the API to count the number of cafes with in 500 meters of each postal code lat/lon.
   - Plot the Top 10 and the bottom 10 counts of coffee shops on the map using different colors for High and low counts.
9. Get top 100 places within Radius of 500 Meters of each postal code from Google API.
   - Create a function to get - 'venue.name', 'venue.categories', 'venue.location.lat', 'venue.location.lng'.
   - Create a data frame each for all the post codes using the get function.
   - Combine all post code data frames to make one that stores - Neighborhoods/postal code,Latitude, Longitude, Venue name,Venue Latitude, Venue Longitude, Venue Category.
   - Plot the top count of coffee shops per postal codes/Neighborhoods.
10. Explore the Neighborhoods/postal code:
   - Create a data frame with Top 5 Most Common (frequency of) Venues for each postal code.
   - Plot this as a chart.
   - Create a data frame that store the top 10 venue categories for each postal code.
   - Plot this as a chart.
11. Cluster the results:
   - Use K-mean to cluster and create data frames for each postcode/Neighborhood.
   - Neighborhood data frame to have - Postal code, Population, Income,  a column each for the the top 10 Common Venue category.
   - Draw an phrase that describes each Neighborhood as per the clustered data frame.
12. Discuss and conclude - listing out the options to open a new coffee shop.