# Best neighborhood for a New Cafe in Toronto
#### Problem
Toronto has many neighborhoods, each with its own unique characteristics. The task was to  choose a neighborhood that offers the best business opportunities, a healthy customer base, while minimizing competition.
#### The Objective
- To analyze the spread of other types of businesses, existing competition, population density and median household income with in each neighborhood.
- To perform a comprehensive data analysis and come up with a MVP as the first iteration.
- To obtain relevant data from credible data sources, create a code that can be reused independent of the data sources, code that is scale-able, and flexible enough for future
- To Suggest three of Toronto’s postal codes, where a new cafe business shall be profitable.
#### Data
The analysis will be based on the following data sources:</br>
   - Wikipedia: To obtain postal code data : [List of postal codes of Canada: M](https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M)</br>
   - Population data : [Population and dwelling counts: Canada and forward sortation areas](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=9810001901)</br>
   - Income data: Data: [Census Profile, 2021 Census of Population(Forward sortation areas (FSAs))](https://www12.statcan.gc.ca/census-recensement/2021/dp-pd/prof/details/download-telecharger.cfm?Lang=E)</br>
   - Google Places API : [Nearby places](https://developers.google.com/maps/documentation/places/web-service/supported_types?_gl=1*gb02v5*_up*MQ..*_ga*MTY4MjAzNTA0MS4xNzMzNjg2NTMz*_ga_NRWSTWS78N*MTczMzY4NjUzMi4xLjEuMTczMzY4Nzk5Ni4wLjAuMA..)</br>
#### Approach
1. **Scrape Postal Code Data**
   - Scrape postal code data of Toronto from Wikipedia.
   - Clean and save the postal code data into a data frame.
   - Verify if all postal codes are obtained.

2. **Add Geographical Data**
   - Add latitude and longitude using pgeocode.
   - Inspect, discuss, and clean the geo data for data sanity.

3. **Population Data**
   - Download the population CSV from Statistics Canada.
   - Extract Toronto-specific data from the CSV and save it in a new, lighter CSV.
   - Read the new CSV and save the population data into a data frame.

4. **Income Data**
   - Download the income CSV from Statistics Canada.
   - Extract Toronto-specific data from the CSV and save it in a new, lighter CSV.
   - Read the new CSV and save the income data into a data frame.

5. **Merge Data**
   - Merge the postal-geo data, population data, and income data into a master data frame.

6. **Inspect and Clean Master Data**
   - Inspect and clean the master data frame (toronto_data).

7. **Visual Representation**
   - Plot the richest and most populous postal codes for visual representation.

8. **API Selection**
   - Find which API is better for our analysis, Google Places or Foursquare Places.
   - Set up an API call, inspect the response, and read the documentation.

9. **Function Creation**
   - Create a function to get all Place Type Cafe from the responses.
   - Use `get_places_cafe` function, append cafe names/count to `toronto_data`.

10. **Data Storage**
    - Store the response as a CSV.
    - Read the CSV and create `toronto_data_df` having postal codes, geo information, income, population, counts of cafes, and names of cafes.

11. **Visualization**
    - Plot `toronto_data_df` on a map to enable visualization of cafe competition.

12. **Function Iteration**
    - Iterate the function into `get_places_all` to get all place types for postal codes.
    - Use the `get_places_all` function on a single postal code to inspect the responses.

13. **Data Filtering**
    - Iterate `get_places_all` to filter out places with 'point_of_interest' as the first in type list and get the second type if available (this place type is not of business use).
    - Use the iterated `get_places_all` function to get all the place types for all postal codes.

14. **Final Data Storage**
    - Store the response as a CSV so that no more API calls are needed while working.
    - Read the CSV and create a data frame `toronto_data_places`.

15. **One-Hot Encoding**
    - Perform one-hot encoding on the 'Place Type' column to prepare categorical data for the machine learning model while maintaining important contextual information.

16. **Grouping and Analysis**
    - Group the `toronto_onehot` Data Frame by 'Postal Code' and calculate the mean of each one-hot encoded column for each postal code to analyze the distribution of different place types across various postal codes in Toronto.
    - Identify the most common place types for each postal code in Toronto as frequencies.

17. **Function Creation for Common Places**
    - Create a function to identify the most common places for rows in the Data Frame.
    - Create a new Data Frame that lists the top 10 most common places for each postal code in Toronto.

18. **Clustering**
    - Use Silhouette Score to establish the number of clusters.
    - Set up and run the K-means clustering algorithm on the one-hot encoded data (excluding the 'Postal Code' column) with 4 clusters.
    - Create a Data Frame that contains the cluster labels, original data, and the top 10 most common places for each postal code.

19. **Final Data Frame**
    - Create the final Data Frame using `toronto_onehot_merged`, dropping columns not necessary for conclusion and discussion.
    - Display all 4 clusters.

20. **Stacked Bar Chart**
    - Plot a stacked bar chart to analyze the characteristics of the clusters.

21. **Cluster Selection**
    - Select the most suitable cluster for the cafe business environment.
    - Plot cafe counts distribution for the selected clusters to analyze direct competition and select low competition clusters to move forward with.

22. **Visual Inspection and Discussion**
    - Visually inspect and discuss the clusters' data frames to choose postal codes where income and population are high.

23. **Prime Location Suggestions**
    - Identify three prime locations for opening a new cafe that offer a favorable business environment, low competition, and a high concentration of residents with disposable income.
