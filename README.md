# Airline Passenger Satisfaction Analysis

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/midhun-babu/Airline-Passenger-Satisfaction/blob/main/Airline_Analysis.ipynb)

Live page: https://midhun-babu.github.io/Airline-Passenger-Satisfaction/

## Analysis of a public airline passenger survey to find out what is linked to passenger satisfaction, and how well a model can predict it.

## Questions
- What is most strongly linked to satisfaction: service quality, delays, or passenger type?
- How do business, economy and personal travellers differ?
- Which services matter most to passengers?

## Data
- Source: public Kaggle dataset, [Airline Passenger Satisfaction](https://www.kaggle.com/teejmahal20/airline-passenger-satisfaction). The original source of the survey is not documented, so the findings are illustrative.
- Train set: 103,904 passengers. Test set: 25,976 passengers. 24 columns after cleaning.
- Target: `satisfaction` (satisfied, or neutral or dissatisfied).
- Class balance (train): 43.3% satisfied, 56.7% neutral or dissatisfied. No resampling was needed.
- Missing values: only `Arrival Delay in Minutes` (310 rows, about 0.3%), filled with the train median.
- Duplicates: none.

## Approach
1. Cleaned the data: dropped the index and ID columns, standardised column names, filled missing arrival delay values.
2. Explored satisfaction by class, travel type, customer type, delay, age and flight distance.
3. Trained logistic regression (baseline) and random forest, evaluated on the provided test set.
4. Used random forest feature importance to rank the main drivers.

## Key findings
- **Class and travel type show the biggest gaps.** 69.4% of Business class passengers were satisfied, against 24.6% in Economy Plus and 18.6% in Economy. By purpose of travel, 58.3% of business travellers were satisfied against 10.2% of personal travellers.
- **Loyal customers are more satisfied.** 47.7% of loyal customers were satisfied, against 23.7% of disloyal customers.
- **Delays are linked to lower satisfaction, but the effect is smaller than class or travel type.** The satisfied share was 45.8% with no departure delay and about 36% for delays over an hour. It stays around that level beyond 60 minutes rather than continuing to fall.

| Departure delay | Satisfied | Passengers |
|---|---|---|
| No delay | 45.8% | 58,668 |
| 1-15 min | 43.7% | 22,184 |
| 16-60 min | 37.4% | 15,813 |
| 61-120 min | 35.6% | 4,699 |
| 120+ min | 36.1% | 2,540 |

- **Service ratings most linked to satisfaction:** online boarding (correlation about 0.50), inflight entertainment (about 0.40) and seat comfort (about 0.35). Gate location and departure/arrival time convenience show almost no link (near zero, the latter slightly negative).
- **Top features in the random forest:** online boarding, inflight wifi service, personal travel, economy class, inflight entertainment. Inflight wifi ranks high here but only about 0.28 in the correlation chart, so its effect is probably not a simple linear one.

## Model results
Evaluated on the test set (25,976 passengers). Always predicting "not satisfied" would score about 56.1%.

| Model | Accuracy | Precision (satisfied) | Recall (satisfied) |
|---|---|---|---|
| Logistic regression | 87.2% | 0.87 | 0.83 |
| Random forest | 96.3% | 0.97 | 0.94 |

## Recommendations
- Look at online boarding, inflight entertainment and seat comfort first. They show the strongest link with satisfaction in the correlation analysis, and online boarding and inflight entertainment also rank near the top in the random forest. Inflight wifi is a top feature in the model too.
- Gate location and departure/arrival time convenience show little link to satisfaction, so they look like lower priorities.
- Personal travellers and economy passengers report the lowest satisfaction, so they are the segment with the most room to improve.
- Delays are worth managing, but the data suggests service quality and passenger type explain more of the variation.

## Limitations
- The results show association, not cause. Feature importance shows which variables the model relies on, not the direction of their effect.
- The data is anonymous and its origin is not documented, so it may not represent any specific airline.
- The class and travel type rates are simple averages and do not control for other factors.

## How to run
1. Click the Colab badge above, or open `Airline_Analysis.ipynb` in Jupyter.
2. Run all cells. The notebook downloads the data with `kagglehub`, so no manual download is needed.
3. To run locally: `pip install -r requirements.txt`

## Project structure
```
Airline-Passenger-Satisfaction/
├── Airline_Analysis.ipynb
├── requirements.txt
├── README.md
└── images/
```

## Tools
Python, pandas, matplotlib, seaborn, scikit-learn, Google Colab

<!-- Add charts once the images are uploaded to the images/ folder, then delete these comment markers:

## Charts
![Satisfaction by class and travel type](images/class_travel.png)
![Correlation of service ratings with satisfaction](images/service_correlation.png)
![Top features](images/feature_importance.png)
![Satisfaction by departure delay](images/delay.png)
-->
