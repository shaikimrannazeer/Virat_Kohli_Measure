# Virat Kohli Dashboard 🏏

This project is a **Power BI Dashboard** that shows detailed insights about the cricket career of **Virat Kohli**.  
It helps to analyze his batting performance, records, and overall career statistics in an interactive way.

---

## 📂 File
- `Virat Kohli Dashboard.pbix` → Power BI report file

---

## 📊 Features
- Matches played, runs scored, centuries, half-centuries
- Year-wise and format-wise performance (ODI, Test, T20I, IPL)
- Strike rate, average, and consistency tracking
- Interactive filters and visuals for easy analysis

---

📷 Preview

(<img width="1303" height="728" alt="Image" src="https://github.com/user-attachments/assets/f31eac7c-4706-4357-aa25-3a3255a1470e" />)

## 📊 Dashboard Highlights

- *Total Runs* Scored
- *Centuries (100s), Fifties (50s), and 30+ Scores*
- *Highest Score*
- *Total Matches Played*
- *Date-wise Analysis* with Year, Month, and Day breakdown
- *Dynamic Filtering* using slicers and visuals

---

## 🧠 DAX Formulas

### 🎯 Batting Milestones

#### ➤ 100s
```dax
100s = 
VAR res = SWITCH(TRUE(),
    'Virat_Kohli'[runs] >= 100 && 'Virat_Kohli'[runs] < 200, 1,
    'Virat_Kohli'[runs] >= 200 && 'Virat_Kohli'[runs] < 300, 2,
    'Virat_Kohli'[runs] >= 300 && 'Virat_Kohli'[runs] < 400, 3,
    0)
RETURN res
```
➤ 50s
```50s = 
VAR res = SWITCH(TRUE(),
    'Virat_Kohli'[runs] >= 50 && 'Virat_Kohli'[runs] < 99, 1,
    'Virat_Kohli'[runs] >= 150 && 'Virat_Kohli'[runs] < 199, 1,
    'Virat_Kohli'[runs] >= 250 && 'Virat_Kohli'[runs] < 299, 1,
    0)
RETURN res
```

➤ 30+

```
30+ = IF('Virat_Kohli'[runs] >= 30, 1, 0)
```

📅 Calendar Table & Date Columns
➤ Create Date Table
```
Calendar = CALENDAR(
    DATE(YEAR(MIN(Virat_Kohli[date])), 1, 1),
    DATE(YEAR(MAX(Virat_Kohli[date])), 12, 31)
)
```
➤ Derived Columns
```
day = FORMAT(Calendar[Date], "ddd")
day_no = DAY(Calendar[Date])
month = FORMAT(Calendar[Date], "mmm")
month_no = MONTH(Calendar[Date])
year = YEAR(Calendar[Date])
```
📈 Aggregate Measures
➤ Total Runs
```
Runs = SUM(Virat_Kohli[runs])
```
➤ Total 100s
```
100s = SUM(Virat_Kohli[100s])
```
➤ Total 50s
```
50s = SUM(Virat_Kohli[50s])
```
➤ Total 30+
```
30+ = SUM(Virat_Kohli[30+])
```
➤ Highest Score
```
HighestScore = MAX(Virat_Kohli[runs])
```
➤ Total Matches
```
Total_Matches = COUNT(Virat_Kohli[opponent])
```

🛠 Skills Applied

-->Data Cleaning & Modeling
-->DAX Calculations
-->Date Table Creation
-->Power BI Visualizations
-->Interactive Reporting

🚀 How to Use
1. Open the .pbix file using Power BI Desktop.
2. Explore interactive visuals using slicers (by year, opponent, format).
3. Analyze Kohli’s run consistency, peak performances, and milestones.

📌 Author

Shaik Imran Nazeer

GitHub: shaikimrannazeer

⭐ Project Motivation
This project combines my passion for cricket with my skills in Power BI. The goal is to present Virat Kohli’s legendary career with impactful data storytelling using dashboards and DAX.
