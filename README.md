# Property-Rent-Estimator-with-Python-and-Jupyter-Notebook

This is a python machine learning project designed to estimate rent prices for properties. It contains a scraper to download the information for current property listings, a preprocessing file, and a machine learning Random Forest algorithm with GUI window to facilitate entering information for new predictions. The independent variables used to predict the monthly rent are area of the property, zip code, number of bedrooms and bathrooms, parking and laundry type, and other features such as presence of EV charging and air conditioning, wheelchair accessibility, pets allowed and others.

The pros of the project are that it scrapes current market listings, can be used for any geographical location with enough listings, and every step is easy and intuitive to use with different data sets. Some steps may take a few hours to complete, such as scraping the data and assigning zip code based on GPS coordinates, so I have included a sample data set from the San Francisco Bay Area to preview the project.

The file to start with is "scrap_data_craigslist.ipynb" to scrape the data, then "preprocessing.ipynb" where multiple csv files scraped in different time can be combined into a single dataframe, and finally select the machine learning models, which are on separate files.

The data I have used is from three periods between two weeks each. The most accurate results are yield by Gradient Boosting Regressor model, and the percentage of the mean absolute error of the average price is 7.59%

Please note that the scraping file requires a Chrome browser and WebDriver Manager for Chrome installed.


Full description:

The first step is to scrape the data, organize the data into a data frame, and save the data frame to a csv file, which is done by running file scrap_data_craigslist.ipynb. This file contains the following functions:
-	number_of_pages(url) – this function takes as a parameter a URL of a single search result page, and uses Selenium WebDriver to open this page, then it clicks on the last page link and returns the number of search result pages.

-	get_links(url, pages_number) – takes as parameters a URL of a single search result page, and the number of pages returned from the previous function. It uses Selenium WebDriver to open the first page and to click on the next page link as many times as the number of search result pages is, while using Beautiful Soup 4 to extract the URLs of each listing on each page. It returns a list with all listing URLs.

-	scrap_listings(links) – takes as a parameter the list with the URLs of the listings, and using Beautiful Soup 4 extracts information for each listing, such as title of the listing, content (description) of the listing, attributes (price, the area of the property in sq. ft., listed location, latitude, longitude, number of bedrooms and bathrooms), and features (property type, parking type, laundry type, rent period, if EV charging is available, if there is air conditioning, if furnished or not, if smoking is allowed, if the property is wheelchair accessible, if cats or dogs are allowed, and finally room and bathroom type (private or shared) which is relevant only if the scraping is for a room in shared property). 
This function returns a list with the above information and a list with the URLs that didn’t get extracted due to bad Internet connection or response code different than 200 in order to run them once again, which is an option of the app() function.

-	get_attributes(scrap_list) – takes the list with the listing information from function scrap_listings and extracts the listing price, the area of the property in sq. ft., listed location, latitude, longitude, number of bedrooms and bathrooms. This function returns a list with nested lists with the attributes for all listings.

-	get_features(scrap_list, show_unique_features=False) – takes the list with the listing information from function scrap_listings and extracts listing property type, parking type, laundry type, rent period, if EV charging is available, if there is air conditioning, if furnished or not, if smoking is allowed, if the property is wheelchair accessible, if cats or dogs are allowed, and finally room and bathroom type (private or shared) which is relevant only if the scraping is for a room in shared property. This function returns a list with nested lists with the features for all listings.
It also has a parameter to print the unique features in all listings.

-	df_to_file(file_name, attributes, features) – takes attributes list, the features list, and a file name to save them on as a scv file.

-	app(url, file_name, rerun_bad_connection=True) – runs all the above functions. If the rerun_bad_connection is set to True, the function will rerun all listing URLs that didn’t get extracted by the scrap_listings function.


Please let me know if you have any questions or suggestions for improvement.
