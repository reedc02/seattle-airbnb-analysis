# Seattle Airbnb Price Analysis

## Project Overview

This project analyzes Seattle Airbnb listing data (from Kaggle) to identify the factors that contribute to higher nightly prices. Using Python for data cleaning, visualization, and linear regression modeling, the analysis examines how listing characteristics such as size, room type, and neighborhood location influence pricing.

The goal is to demonstrate a complete data analysis workflow, complemented by SQL for aggregation and Tableau for geographic and visual exploration.

---

## Research Question

**What factors contribute to higher Airbnb prices in Seattle?**

---

## Data Source

* Dataset: Seattle Airbnb Open Data
* Source: Kaggle
* File used: `listings.csv`
* Observations after cleaning: 3,795 listings

---

## Tools & Technologies

* Python (pandas, numpy, matplotlib, seaborn, statsmodels): data cleaning, EDA, regression modeling

* Jupyter Notebook: analysis documentation

* SQL (SQLite): aggregation and neighborhood-level summaries

* Tableau Public: interactive geographic and analytical visualizations



---

## Data Cleaning & Preparation

Relevant variables for analysis were selected:

* Price
* Neighborhood
* Room and property type
* Capacity (accommodates, bedrooms, bathrooms)
* Review metrics

Key cleaning decisions:

* Dropped listings with missing `bedrooms`, `bathrooms`, or `property_type` (<0.5% of data)
* Retained listings with missing review metrics, as these likely represent newer listings and dropping them could bias the analysis
* Converted price to numeric and capped values at the 99th percentile to limit the influence of extreme outliers

---

## Exploratory Data Analysis

Exploratory analysis revealed:

* Airbnb prices are right-skewed, with a few very high-priced listings
* Entire homes are consistently priced higher than private or shared rooms
* Larger listings (more bedrooms, bathrooms, and guest capacity) command higher prices
* Median prices vary substantially by neighborhood

---

## Modeling Approach

An Ordinary Least Squares (OLS) regression model was used to quantify the relationship between listing characteristics and nightly price.

**Target variable:**

* `price_capped` (price capped at the 99th percentile)

**Key predictors:**

* Accommodates
* Bedrooms
* Bathrooms
* Room type (one-hot encoded)
* Neighborhood (one-hot encoded)

---

## SQL Analysis

Following the Python analysis, SQL was used to aggregate and summarize the cleaned Airbnb data. Queries focused on:

- Average nightly price by neighborhood
- Listing counts per neighborhood
- Price differences by room type

These SQL-derived summary tables were used to validate modeling results and support visual exploration in Tableau.


## Mini-Conclusion

Initial results indicate that listing size and room type are key drivers of price, and neighborhood location also plays a role. To provide neighborhood-level evidence, regression coefficients were examined and visualized in scatter plots showing average price, listing counts, and impact on price.

---

## Key Findings 

* **Listing size is the strongest predictor of price:**

  * Each additional bedroom increases nightly price by approximately **$33**
  * Each additional bathroom increases price by about **$24**, holding other factors constant
* **Room type matters:** Private and shared rooms are priced significantly lower than entire homes
* **Location significantly affects pricing:**

  * Neighborhoods such as **Pioneer Square**, **Pike-Market**, **Central Business District**, **South Lake Union**, **West Queen Anne**, and **Westlake** consistently command higher prices
* The model explains approximately **64% of the variation** in capped Airbnb prices
* Visualization combining neighborhood-level averages, listing counts, and regression coefficients confirms the location effect, providing clear evidence of how both listing attributes and neighborhood influence Airbnb pricing

---

## Tableau Visualization

An interactive Tableau dashboard was created to visually explore pricing patterns across Seattle neighborhoods.

The dashboard includes:
- A geographic map showing average capped Airbnb prices by location
- A bar chart highlighting neighborhoods with the strongest positive price impact based on regression coefficients

These visualizations reinforce the regression findings and demonstrate how location contributes to higher Airbnb prices.

Tableau Dashboard: [https://public.tableau.com/views/SeattleAirbnb-PriceDistributionMap/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link]


## Limitations

* Cross-sectional data; does not capture seasonal or dynamic pricing effects
* Price capping reduces the influence of extreme values but may underrepresent luxury listings
* Linear model may not fully capture non-linear relationships or interactions between features
* Host-level, availability, and demand factors were not included

---

## Author

Courtney Reed
# seattle-airbnb-analysis
