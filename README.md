# Best neighborhood for a New Coffee Shop in Toronto
#### Problem
Toronto has many neighborhoods, each with its own unique characteristics. The task was to  choose a neighborhood that offers the best business opportunities, a healthy customer base, while minimizing competition.</br>
The objective was to analyze the spread of other types of businesses, existing competition, population density and median household income with in each neighborhood. To perform a comprehensive data analysis and come up with a MVP as the first iteration.To obtain relevant data from credible data sources, create a code that can be reused independent of the data sources, code that is scaleable, and flexible enough for future.Suggest three of Toronto’s postal codes, where a new cafe business shall be profitable.
#### Data
The analysis will be based on the following data sources:</br>
   - Wikipedia: To obtain postal code data : [List of postal codes of Canada: M](https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M)</br>
   - Population data : [Population and dwelling counts: Canada and forward sortation areas](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=9810001901)</br>
   - Income data: Data: [Census Profile, 2021 Census of Population(Forward sortation areas (FSAs))](https://www12.statcan.gc.ca/census-recensement/2021/dp-pd/prof/details/download-telecharger.cfm?Lang=E)</br>
   - Google Places API : [Nearby places](https://developers.google.com/maps/documentation/places/web-service/supported_types?_gl=1*gb02v5*_up*MQ..*_ga*MTY4MjAzNTA0MS4xNzMzNjg2NTMz*_ga_NRWSTWS78N*MTczMzY4NjUzMi4xLjEuMTczMzY4Nzk5Ni4wLjAuMA..)</br>
#### Approach
- Scrape Postal code Data of Toronto from Wikipedia.
- Clean and save the postal code data into a data frame.
- Verify if we got all the postal codes.
- Add the Latitude and Longitude using pgeocode.
- Inspect, discuss and clean the Geo data for data sanity.
- Download the population csv from Statistics Canada.
- Extract Toronto specific data from csv and save in a lighter new csv.
- Read the new csv, save the population data into a data frame.
- Download the income csv from Statistics Canada.
- Extract Toronto specific data from csv and save in a lighter new csv.
- Read the new csv, save the income data into a data frame.
- Merge the postal-geo data, population data and income data into master data frame.
- Inspect and clean the master data frame (toronto_data).
- Plot the Richest and most Populous Postal codes for visual representation.
- Find which API is better for our analysis, Google places or Foursquare places.
- Set up an API call, inspect the response and read the documentation.
- Create a function to get all Place Type Cafe from the responses.
- Use get_places_cafe function, append cafe names/count of toronto_data.
- Store the response as a csv read the csv and create toronto_data_df having Postal codes, Geo information, Income, Population, counts of cafe, names of cafe.
- Plot toronto_data_df on a map to enable visualization of cafe competition.
- Iterate the function into get_places_all to get all Place types for postal codes.
- Use the get_places_all function on a single postal code to inspect the responses.
- Iterate get_places_all to filter out places with 'point_of_interest' as the first in type list and get the second type if available (this place type is not of business use).
- Use the iterated get_places_all function to get all the place types for all postal codes.
- Store the response as a csv so that no more API calls are needed while working.
- Read the csv and create a data frame toronto_data_places.
- Perform one-hot encoding on the 'Place Type' column, to prepare categorical data for machine learning model while maintaining important contextual information.
- Group the toronto_onehot Data Frame by 'Postal Code' and calculate the mean of each one-hot encoded column for each postal code, for analyzing the distribution of different place types across various postal codes in Toronto.
- Identify most common place types for each postal code in Toronto as frequencies.
- Create a function to identify the most common places for rows in the Data Frame.
- Create a new Data Frame that lists the top 10 most common places for each postal code in Toronto.
- Use Silhouette Score to establish the number of clusters.
- Set up and run the K-means clustering algorithm on the one-hot encoded data (excluding the string 'Postal Code' column) with 4 clusters.
- Create a Data Frame that contains the cluster labels, original data, and the top 10 most common places for each postal code.
- Create the final Data frame using the toronto_onehot_merged, drop the columns not necessary for conclusion and discussion.
- Display all the 4 Clusters.
- Plot a Stacked bar chart that helps Analyze their characteristic.
- Select the most suitable cluster for business environment for the cafe business.
- Plot Cafe counts distribution for the selected clusters to analyze the direct competition and select the low competition clusters to move forward with them.
- Visually inspect and discuss the clusters data frames of these final cluster/s to choose the postal codes where the income and population is high.
- Identify three suggestions of prime locations for opening a new cafe that offer a favorable business environment, low competition, and a high concentration of residents with disposable income.