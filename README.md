# Best neighborhood for a New Coffee Shop in Toronto
#### Problem
Toronto is a large city with many neighborhoods, each with its own unique characteristics. For a new coffee shop, it is crucial to choose a neighborhood that offers the best business opportunities while minimizing competition. 
This project will analyze the existing coffee shop distribution with in each neighborhood, population density with in each neighborhood, Median Household Income with in each neighborhood , and the spread of other types of Places with in each neighborhood to identify the best neighborhood for a new coffee shop in Toronto.
#### Data
The analysis will be based on the following data sources:</br>
   - Wikipedia: To obtain postal code data : [List of postal codes of Canada: M](https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M)</br>
   - Population data : [Population and dwelling counts: Canada and forward sortation areas](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=9810001901)</br>
   - Income data: Data: [Census Profile, 2021 Census of Population(Forward sortation areas (FSAs))](https://www12.statcan.gc.ca/census-recensement/2021/dp-pd/prof/details/download-telecharger.cfm?Lang=E)</br>
   - Google Places API : [Nearby places](https://developers.google.com/maps/documentation/places/web-service/supported_types?_gl=1*gb02v5*_up*MQ..*_ga*MTY4MjAzNTA0MS4xNzMzNjg2NTMz*_ga_NRWSTWS78N*MTczMzY4NjUzMi4xLjEuMTczMzY4Nzk5Ni4wLjAuMA..)</br>
#### Approach
1. Scrape Postal code Data of Toronto from Wikipedia.
2. Clean and save the postal code data into a data frame.
3. Verify if we got all the postal codes.
4. Add the Latitude and Longitude for each postal code using pgeocode.
5. Inspect, discuss and clean the Geo data for data sanity.
6. Download the csv having population data from Statistics Canada.
7. Clean and extract Toronto specific population data from the downloaded csv and save the save the lighter and relevant data in a new csv.
8. Read the csv and save the population data into a data frame.
9. Download the csv having income data from Statistics Canada.
10. Clean and extract Toronto specific income data from the downloaded csv and save the save the lighter and relevant data in a new csv.
11. Read the csv and save the income data into a data frame.
12. Merge the geo data, population data and the income data into a data frame (toronto_data).
13. Inspect and clean the toronto_data.
14. Plot the Richest and most Populous Postal codes for visual representation.
15. Find which API is better for our analysis, Google places or Foursquare places.
16. Set up an API call for Google Places Nearby.
16. Inspect the response and read the documentation.
17. Create a function to get all Place Type = Cafe from the responses.
20. Use the get_places_cafe function and append the response cafe names and count of cafe to toronto_data data frame.
21. Store the response as a csv so that no more API calls are needed while working.
22. Read the csv and create toronto_data_df having Postal codes, Geo information, Income, Population, counts of cafe, names of cafe.
23. Plot the toronto_data_df on a map so that the decision makers can visualize the area where we have lesser competition.
24. Iterate the function get_places_cafe into get_places_all where it can get all Place types for postal codes.
25. Use the get_places_all function on a single postal code to inspect the responses.
26. Filter out places with 'point_of_interest' as the first type and get the second type if available, as this place type is not of business use.
27. Use the altered get_places_all function to get all the place types for all the postal codes.
28. Store the response as a csv so that no more API calls are needed while working.
29. Read the csv and create a data frame toronto_data_places.
30. Performs one-hot encoding on the 'Place Type' column, to prepare categorical data for machine learning model while maintaining important contextual information.
31. Group the toronto_onehot DataFrame by 'Postal Code' and calculate the mean of each one-hot encoded column for each postal code, for analyzing the distribution of different place types across various postal codes in Toronto.
32. Identify the most common place types for each postal code in Toronto. as frequencies.
33. Create a function for identifying the most common venues for a given row in the DataFrame.
34. Create a new DataFrame that lists the top 10 most common venues for each postal code in Toronto.
35. set up and run the K-means clustering algorithm on the one-hot encoded data (excluding the 'Postal Code' column) with 6 clusters.
36. Create a DataFrame that contains the cluster labels, original data, and the top 10 most common venues for each postal code.
37. Create the final Data frame using the toronto_onehot_merged, drop the columns not necessary for conclusion and discussion.
38. Print all the 6 Clusters and And Analyze their characteristic.
39. Plot Print all the 6 Clusters and And Analyze their characteristic.
40. Draw a final conclusion and advise on the neighborhood contenders for new coffee shop.