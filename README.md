
# Do Higher Hospitality Wages Lead to Better Hotel Ratings?

*An analysis of hotel reviews and hospitality wages across U.S. states*

Many people assume that better-paid hotel staff give better service, which should lead to happier guests. This project tests that idea with real data. We combined 55,000+ hotel reviews with U.S. Bureau of Labor Statistics wage data to see whether states that pay hospitality workers more have better-rated hotels, and what guests actually complain about.

## Key Findings

- **Wages are not linked to ratings.** Across 42 states, the correlation between average hospitality wage and average hotel rating is **r = −0.03**. Some of the highest-paying states (Massachusetts, New York, Nevada) have below-average ratings.
- **Room condition is strongly linked to ratings.** The share of reviews that mention room problems (cleanliness, pests, smell or smoke, broken or outdated rooms) has a correlation of **r = −0.89** with state ratings.
- **Cleanliness is the most common complaint.** It shows up in about 18% of low-rated reviews and only 1.5% of high-rated ones. Staff and service complaints appear in only about 6%. Pest mentions are rare, but those reviews average just **1.94 / 5**.
- **Ratings differ by state but stay steady over time.** State averages range from 3.17 (South Carolina) to 4.60 (New Hampshire). The national average stayed between 3.68 and 3.82 from 2011 to 2016.

**Recommendation:** Hotels that want better ratings should invest in room upkeep (housekeeping, maintenance, smoke control and pest control) rather than across-the-board wage increases. Wages still matter for staff retention and fairness, but this data shows no evidence that higher state wage levels alone raise guest ratings.

## Data

| Source | Description | License |
| --- | --- | --- |
| [Datafiniti Hotel Reviews (Kaggle)](https://www.kaggle.com/datasets/datafiniti/hotel-reviews) | 3 CSV files, 55,912 reviews | CC BY-NC-SA 4.0 |
| [BLS Occupational Employment and Wage Statistics, May 2013](https://www.bls.gov/oes/tables.htm) | 434,473 wage records | Public domain |

The raw data files are not included in this repository. Download them from the links above.

## Methods

1. **Data cleaning.** Combined three review files with different structures (25, 26 and 19 columns). Removed 214 exact duplicates, standardized column names, text and dates, and put all ratings on a single 1–5 scale. Missing values and possibly cut-off reviews were flagged, not filled in with guesses. Assertion checks confirm the row counts add up.
2. **Wage preparation.** Built a state-level average hospitality wage from six hotel-related occupations, including housekeepers, desk clerks, cooks and waiters. Converted wage-file state names to the codes used in the reviews.
3. **Complaint detection.** Sorted complaint keywords from the review text into 8 categories, such as cleanliness, pests, smell/smoke, broken or outdated rooms, and staff/service.
4. **Analysis.** Joined reviews and wages by state, keeping only the 42 states with at least 100 reviews (27,474 U.S. reviews). Compared ratings by state, year and occupation wage, and calculated correlations between rating, wages and room complaints.

## Tech Stack

Python · pandas · NumPy · Matplotlib · Seaborn · openpyxl · Google Colab

## How to Run

1. Download the data files: `Datafiniti_Hotel_Reviews.csv`, `Datafiniti_Hotel_Reviews_Jun19.csv`, `7282_1.csv` and `780_data_wages_01.xlsx`.
2. Open the notebook in Google Colab or Jupyter and upload or place the files in the working folder.
3. Run all cells from top to bottom. Cleaned outputs are saved to `hotel_cleaning_outputs/`.

## Limitations

- The results are correlations, not proof of cause and effect, and they are measured at the state level. Individual hotels may behave differently.
- The wage data is from 2013 and the reviews are from 2011 to 2016. Ratings were stable over that period, which makes the comparison reasonable.
- Complaints were found by keyword matching, which can miss some complaints or misread context.
- Review counts vary a lot by state, which is why only states with 100+ reviews were included.

## Team

Team B07: **Anna Zvanskaya**, Paula Vasques, Pushan Parihr, Summer Kao, Sharanya Srinivas
Final project for BA780 Introduction to Data Analytics

*AI disclosure: Claude was used to help brainstorm, debug code and plan visualizations. All work was reviewed and validated by the team.*
