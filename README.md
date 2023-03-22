# Property-Rent-Estimator-with-Python-and-Jupyter-Notebook

This is a python machine learning project designed to estimate rent prices for properties. It contains a scraper to download the information for current property listings, a preprocessing file, and a machine learning Random Forest algorithm with GUI window to facilitate entering information for new predictions. The independent variables used to predict the monthly rent are area of the property, zip code, number of bedrooms and bathrooms, parking and laundry type, and other features such as presence of EV charging and air conditioning, wheelchair accessibility, pets allowed and others.

The pros of the project are that it scrapes current market listings, can be used for any geographical location with enough listings, and every step is easy and intuitive to use with different data sets. Some steps may take a few hours to complete, such as scaping the data and assigning zip code based on GPS coordinates, so I have included a sample data set from the San Francisco Bay Area to preview the project.

The file to start with is "scrap_data_craigslist.ipynb" to scrape the data, then "preprocessing.ipynb" where multiple csv files scraped in different time can be combined into a single dataframe, and finally "ml_model.ipynb".

Please note that the scraping file requires a Chrome browser and WebDriver Mnager for Chrome installed.

Please let me know if you have any questions or suggestions for improvement.
