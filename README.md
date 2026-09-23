# Airline Passenger Satisfaction Analysis

Analysis of a public Kaggle airline survey dataset (~130k passengers) to find
what drives passenger satisfaction. The dataset's original source is not
documented, so treat the findings as illustrative.

## Questions
- What drives satisfaction: service quality, delays, or passenger type?
- How do business, economy and personal travellers differ?
- Which services would an airline gain most by improving?

## Approach
- Cleaned data (dropped ID columns, filled missing arrival delay with the median)
- Explored satisfaction by class, travel type, loyalty, age, distance and delay
- Compared logistic regression and random forest; used feature importance
## Data
- Source: public Kaggle "Airline Passenger Satisfaction" survey dataset
  (original source not documented)
- Train set: 103,904 passengers, 25 columns; test set: 25,976 passengers
- Target: `satisfaction` (satisfied vs neutral or dissatisfied)
- Class balance (train): 43.3% satisfied, 56.7% neutral or dissatisfied,
  so no resampling was needed
- Missing values: only `Arrival Delay in Minutes` (310 rows, about 0.3%),
  filled with the train median
- Duplicates: none
- Majority-class baseline: about 56.7% accuracy, so model accuracy should
  be read against that
  
## Key findings
1. ___ (class / travel type gap: __% vs __%)
2. ___ (delay effect)
3. ___ (top services linked with satisfaction)

## Model results
- Logistic regression accuracy: __
- Random forest accuracy: __

## Recommendations
1. ___
2. ___
3. ___

## Tools
Python, pandas, matplotlib, seaborn, scikit-learn (Google Colab)
