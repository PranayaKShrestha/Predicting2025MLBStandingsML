# Predicting MLB Standings (2025) ⚾

Every season, baseball fans and analysts attempt to forecast how the standings will look at the end of the year. With advanced data sources and machine learning techniques, we can now approach this question more systematically. This project aims to leverage historical mid-season standings and various team performance metrics to predict the final win totals for each MLB team for the 2025 season. Personally, this project was done to help improve my skills in python, especially with libraries such as pandas, and numpy while also introducing myself to ML. 

The approach combines data scraping from multiple sources and a machine learning model trained on 20 years of historical data to generate end-of-season projections.


# Setup / Methodology ⚾

**Data Collection**
The first step was to gather both historical and current mid-season standings:

- Historical Data (2005–2024): Includes standings at the All-Star break and final season standings.

- 2025 Mid-Season Data: Scraped from ESPN/MLB sources for team wins/losses, runs scored, runs allowed, home/away splits, remaining games, and projected strength of schedule.

Tools Used for Scraping:

scrapping_mlb_standings_data.ipynb

- Uses requests, BeautifulSoup, and pandas to pull and process standings tables.

- Cleans raw text into structured numerical fields (e.g., converting Home and Away records into separate wins/losses).

- Merges scraped team names with external datasets like Fangraphs projections.

**Feature Engineering**

From historical mid-season standings, the following features were engineered:

- Basic performance: Wins (W_mid), runs scored (RS_mid), runs allowed (RA_mid), and run differential (DIFF_mid).

- Context metrics: Home/away win percentages, remaining home/away games, and strength of schedule (SOS_final historically, projected_SOS_end_season for 2025).

- Advanced metrics: Mid-season Pythagorean wins and Win_Diff_mid (difference between actual and expected wins).

- The target variable is Final_Wins

**Model Development**

Notebook: Predicting_mlb_standings_2025.ipynb

The machine learning model:

- Model Choice: Random Forest Regressor and XGBoost were tested, with XGBoost chosen for its superior performance on structured tabular data.

- Training Data: 20 seasons (2005–2024), each season’s All-Star break metrics mapped to final win totals.

- Validation: Train/test split with grid search to tune hyperparameters, ensuring no data leakage.

**2025 Projections**

After training, the model was applied to the 2025 mid-season standings. Additional data, such as Fangraphs projected strength of schedule and projected Pythagorean wins, were incorporated to refine predictions.

The final output is:

Predicted Wins for each MLB team for the 2025 season

Comparison vs. Fangraphs Projections (to evaluate differences)

# Analysis ⚾

<img width="1430" height="1430" alt="image" src="https://github.com/user-attachments/assets/7b172e67-da22-406c-937f-48799ca69baa" />
<img width="1430" height="220" alt="image" src="https://github.com/user-attachments/assets/d72e8d11-246c-4d90-9ead-181011ddc14e" />


# Limitations ⚾
- Injury / trade impacts are not explicitly modeled, although Fangraphs projections partially account for roster changes.

- Sample size limited by availability of consistent mid-season historical data (20 seasons).

- No player-level forecasting—this model is purely team-level.


