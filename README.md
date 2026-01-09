# 🏎️ Formula 1 Budget Limitation Analysis

## Motivation
For my DSA210 project, I want to compare data before and after the F1 2021 Budget Cap and its effects on personal performance, salaries, and winners.  
Before 2021, high-spending teams such as Mercedes and Ferrari consistently dominated; the new cost-cap rules aim to level the field.

The project tests whether **team success is now less dependent on total spending** and **more related to driver skill and salaries**.

---

## Objectives
- Analyze how **team budgets** correlate with **constructor rankings** before and after 2021.  
- Examine whether **driver salaries** have become equal after the budget cap.  
- Test if **driver performance (skill/value)** became a decider of a team’s success.  
- Compare findings through visualizations and statistical analysis.

---

## Data Sources

### Performance & Results
- [Kaggle: *Formula 1 World Championship (1950–2020)*](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020)  
  Contains constructors, drivers, races, points, standings, and results.

### Driver Salaries (2012–2025)
Data compiled from publicly available articles:
- Crash.net salary reports (2012–2015)  
- GrandPrix247 (2016–2017)  
- GP Fans (2018–2019)  
- RacingNews365, Total Motorsport, NBC Miami, and others (2020–2025)

## Project Files

- `data/F1_Team_Spending_and_Salaries_2019_2025.xlsx`  
  Manually compiled team spending and driver salary estimates for 2019 and 2023.

- `data/winners_f1_1950_2025_v2.csv`  
  Race winners and teams for all Grands Prix between 1950 and 2025.

- `notebooks/eda_budget_cap.ipynb`  
  Jupyter notebook containing data cleaning, exploratory analysis, and hypothesis tests for the project.

- `requirements.txt`  
  Python dependencies required to reproduce the analysis.

---

## Methodology

### Data Collection & Cleaning
- Merge Kaggle race results (team-year performance) with salary estimates.  
- Standardize team names and convert currencies to USD (2021 base year).  
- Label each observation as **pre-cap (≤ 2020)** or **post-cap (≥ 2021)**.  
- Combine salaries with team spending.

### Exploratory Data Analysis
- Visualize team budgets, total points, and salary distributions.  
- Compute correlations between budget, salary, and points for both eras.  

### Statistical Testing & Modeling
- **Correlation tests** (Pearson/Spearman) → Budget vs Performance.  
- **t-tests / ANOVA** → Salary changes pre vs post cap.  
- **Regression model** →  
  `Team Points ~ Budget + Avg Salary + PostCap Interaction`.  

### Visualization & Reporting
- Scatter plots (budget vs points).  
- Heatmaps (correlations).  
- Boxplots (salary variance).  
- Gini or Herfindahl index to measure competitive balance.  

---

## Hypotheses

| # | Hypothesis | Null Hypothesis (H₀) | Alternative (H₁) |
|:-:|-------------|----------------------|------------------|
| 1 | **Budget–Performance Correlation** | Team budget and points correlation did **not change** after 2021 | Correlation **changed** after budget cap |
Finance years: [2019, 2023]
Merged (finance + wins) years: [2019, 2023]
   Year      Team  Total Spending Currency  Wins      Era
0  2019  Mercedes       425000000      USD  15.0  Pre-Cap
1  2019   Ferrari       435000000      USD   3.0  Pre-Cap
2  2019  Red Bull       335000000      USD   3.0  Pre-Cap
3  2019   McLaren       250000000      USD   0.0  Pre-Cap
4  2019   Renault       210000000      USD   0.0  Pre-Cap
<img width="2092" height="1331" alt="Screenshot 2026-01-09 222144" src="https://github.com/user-attachments/assets/3bb2b467-b120-4618-8609-515f593626e8" />
<img width="1184" height="584" alt="image" src="https://github.com/user-attachments/assets/1dc3ab5e-242a-4c9a-9ad0-7ddd4aba755a" />
Finance+Wins correlations (2019 vs 2023):
<img width="978" height="284" alt="image" src="https://github.com/user-attachments/assets/4bb26dd0-8e5a-4a89-9755-91f1ca572114" />

| 2 | **Salary Effect on Performance** | Driver salary is not significantly related to team success | Driver salary is **positively related** to team success after the cap |
--- Correlation test: Budget vs Wins (2019 vs 2023) ---
Pre-Cap -> r = 0.737, p = 0.0150
Post-Cap correlation cannot be computed (spending is constant).

--- t-test: Wins (2019 vs 2023) ---
T-test Wins: t = -0.039, p = 0.9694

<img width="1384" height="584" alt="image" src="https://github.com/user-attachments/assets/e769faff-a8bf-4d51-afb0-2ab0d5f3245a" />
<img width="984" height="484" alt="image" src="https://github.com/user-attachments/assets/884f2446-42ec-491b-af80-37ffdb7796c8" />

| 3 | **Salary Distribution** | Driver salaries show no difference in variance pre/post budget cap | Salary variance **decreased** after budget cap |

Correlation (Salary vs Points) 2019: 0.8168221865710157
Correlation (Salary vs Points) 2023: 0.9367562310520083
<img width="1389" height="590" alt="image" src="https://github.com/user-attachments/assets/53ed51c9-59aa-49d9-a9dd-ac1ffe0bea2e" />
<img width="2095" height="894" alt="Screenshot 2026-01-09 222226" src="https://github.com/user-attachments/assets/6d8a620f-57c9-4a83-b6e8-3bc4705966d1" />

| 4 | **Competitive Balance** | Points distribution uniformity remained the same | Competition **became more balanced** after the cap |

---

## Expected Findings
- The **budget–performance link** will decline post-cap.  
- The **driver salary–performance correlation** will rise (skill > spending).  
- **Competitive balance** among teams will improve.  

---

## Tools & Environment
- **Language:** Python 3.9  
- **Libraries:**  
  pandas, numpy, matplotlib, seaborn, scipy, statsmodels, scikit-learn  
- **Version Control:** Git + GitHub  
- **IDE:** Jupyter Notebook / VS Code  

---

## Ethical & AI Statement
All data sources are publicly available and properly cited.  
No private or scraped personal data is used.  
I used LLM tools for searching data and checked the README file for relevance with the course guidelines.

---

## Future Work
- Add **reliability metrics** (DNFs or accidents) from the Ergast API to see whether reduced budgets impacted robustness.  
- Include **driver market dynamics**, such as contract durations or sponsorship effects.  
- Apply **machine learning regression models** to predict team performance using multi-year financial and driver variables.
