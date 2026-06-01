# Property Rent Estimator with Python

A machine learning project that estimates monthly rent prices for residential properties. It scrapes live listings from Craigslist using Selenium and BeautifulSoup4, processes the data, and runs it through several regression models to find the best predictor. A simple GUI lets you enter property details and get a rent estimate without touching any code.

The best results came from the Gradient Boosting Regressor, which achieved a mean absolute error of 7.59% of the average listing price on SF Bay Area data.

---

## How it works

The project is split into three stages, each in its own notebook:

**1. Scraping** — `scrap_data_craigslist.ipynb`  
Scrapes current rental listings from Craigslist for a given search URL. Handles pagination automatically, extracts listing attributes (price, area, bedrooms, bathrooms, location, lat/long) and features (parking type, laundry, EV charging, AC, pets, wheelchair access, etc.). Failed requests due to connection issues are tracked and retried. Can be pointed at any geographic area with enough listings.

**2. Preprocessing** — `preprocessing.ipynb`  
Merges multiple CSV files from different scraping sessions into a single cleaned dataframe. Useful if you run the scraper across several days to build a larger dataset.

**3. Modeling** — separate notebook per model  
Four models are implemented and can be run independently:
- `gradient_boosting_regressor.ipynb` — best performer (7.59% MAE)
- `random_forest_regressor.ipynb`
- `elastic_net.ipynb`
- `linear_regression.ipynb`

Each notebook includes training, evaluation, and a Tkinter GUI window for entering new property details and generating predictions interactively.

---

## Getting started

You'll need Chrome and the following packages:

```bash
pip install selenium beautifulsoup4 pandas numpy scikit-learn webdriver-manager
```

Start with `scrap_data_craigslist.ipynb` if you want fresh data, or use the included sample CSVs from the SF Bay Area (Feb–Mar 2023) to jump straight to preprocessing and modeling. Note that the scraping step can take a few hours depending on the number of listings and the zip code lookup via GPS coordinates.

---

## Features used for prediction

The model uses the following as independent variables: property area in sq ft, zip code, number of bedrooms and bathrooms, parking type, laundry type, and a set of binary features — EV charging, air conditioning, furnished, smoking allowed, wheelchair accessible, cats allowed, dogs allowed. For shared room listings it also captures whether the room and bathroom are private or shared.

---

## Sample data

Three scraping sessions from the San Francisco Bay Area are included as sample CSVs if you want to preview the full pipeline without running the scraper yourself.

---

## Notes

The scraper is built to be reusable — just swap in a different Craigslist search URL to collect data for another city or region. The more scraping sessions you merge in preprocessing, the more robust the model tends to be.

Feel free to open an issue or reach out with questions or suggestions.

**Valeri Toshev**  
[github.com/ValTosh](https://github.com/ValTosh) · [linkedin.com/in/valeritoshev](https://linkedin.com/in/valeritoshev)
