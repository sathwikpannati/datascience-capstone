# SpaceX Falcon 9 First-Stage Landing Prediction

End-to-end data science project that predicts whether the first stage of a SpaceX Falcon 9 rocket will land successfully. Because a reusable first stage is a major driver of launch cost, a landing prediction is also an estimate of what a launch is likely to cost.

The project covers the full workflow: data collection from a REST API and web scraping, data wrangling, exploratory analysis with SQL and visualisation, an interactive map and dashboard, and classification models tuned with cross-validation.

> Completed as the capstone project of the **IBM Data Science Professional Certificate** (Coursera).

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=white)
![Plotly Dash](https://img.shields.io/badge/Plotly%20Dash-3F4F75?logo=plotly&logoColor=white)
![Folium](https://img.shields.io/badge/Folium-77B829)

---

## Workflow

| Step | Notebook / file | What it does |
|---|---|---|
| 1 | [`01_data_collection_api.ipynb`](notebooks/01_data_collection_api.ipynb) | Collects launch data from the SpaceX REST API and keeps Falcon 9 launches |
| 2 | [`02_data_collection_web_scraping.ipynb`](notebooks/02_data_collection_web_scraping.ipynb) | Scrapes Falcon 9 launch records from Wikipedia with BeautifulSoup |
| 3 | [`03_data_wrangling.ipynb`](notebooks/03_data_wrangling.ipynb) | Cleans the data and creates the binary landing-outcome label (`class`) |
| 4 | [`04_eda_sql.ipynb`](notebooks/04_eda_sql.ipynb) | Explores launch sites, payloads and outcomes with SQL queries |
| 5 | [`05_eda_visualization.ipynb`](notebooks/05_eda_visualization.ipynb) | Visual EDA of flight number, payload, orbit and launch site vs. success; feature engineering |
| 6 | [`06_launch_site_map_folium.ipynb`](notebooks/06_launch_site_map_folium.ipynb) | Interactive Folium maps of launch sites, outcomes and proximity to coast, railways and cities |
| 7 | [`spacex_dash_app.py`](dashboard/spacex_dash_app.py) | Plotly Dash dashboard: success rate by launch site and payload vs. outcome |
| 8 | [`07_machine_learning_prediction.ipynb`](notebooks/07_machine_learning_prediction.ipynb) | Standardises features and tunes four classifiers with `GridSearchCV` |

## Results

Models were tuned with 10-fold cross-validation (`GridSearchCV`) and evaluated on a held-out test set (20% of the data, 18 launches).

| Model | Best CV accuracy | Test accuracy |
|---|---|---|
| Logistic Regression | 84.6% | 83.3% |
| Support Vector Machine | 84.8% | 83.3% |
| Decision Tree | **88.9%** | 83.3% |
| K-Nearest Neighbours | 84.8% | 83.3% |

**Key takeaways**

- All four models reach the same test accuracy (83.3%). The test set is very small, so it cannot separate the models; the Decision Tree has the best cross-validation score.
- The confusion matrices show that the main error type is false positives: some failed landings are predicted as successful.
- The yearly landing success rate kept rising from 2013 to 2020, and success rates differ clearly between launch sites and orbit types.

## Project structure

```
datascience-capstone/
├── notebooks/
│   ├── 01_data_collection_api.ipynb
│   ├── 02_data_collection_web_scraping.ipynb
│   ├── 03_data_wrangling.ipynb
│   ├── 04_eda_sql.ipynb
│   ├── 05_eda_visualization.ipynb
│   ├── 06_launch_site_map_folium.ipynb
│   └── 07_machine_learning_prediction.ipynb
├── dashboard/
│   └── spacex_dash_app.py
├── requirements.txt
└── README.md
```

## How to run

```bash
git clone https://github.com/sathwikpannati/datascience-capstone.git
cd datascience-capstone
pip install -r requirements.txt

# Notebooks
jupyter notebook notebooks/

# Dashboard (opens on http://127.0.0.1:8050)
python dashboard/spacex_dash_app.py
```

The notebooks and the dashboard load their datasets from public URLs, so no local data files are needed.

## Skills demonstrated

Data collection (REST API, web scraping) · Data wrangling with pandas · SQL queries for EDA · Data visualisation (Matplotlib, Seaborn, Plotly, Folium) · Interactive dashboards (Plotly Dash) · Feature engineering · Classification (Logistic Regression, SVM, Decision Tree, KNN) · Hyperparameter tuning with cross-validation

## Author

**Sathwik Pannati** · M.Eng. Applied AI for Digital Production Management, Technische Hochschule Deggendorf
[LinkedIn](https://www.linkedin.com/in/sathwik-pannati-803a03254/) · [GitHub](https://github.com/sathwikpannati)
