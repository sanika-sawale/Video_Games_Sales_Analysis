# Video_Games_Sales_Analysis

# 🎮 Video Game Sales – Data Cleaning & Visualization

An exploratory data analysis (EDA) project on **16,598 video games** released between 1980 and 2020. The notebook cleans the raw sales data, checks it for quality issues, and uses Python visualizations to answer questions such as: *Which genres sell best? Which platforms and publishers dominate? Which regions buy the most games? How have sales changed over time?*

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Tools & Libraries](#-tools--libraries)
- [Project Workflow](#-project-workflow)
- [Key Insights](#-key-insights)
- [Visualizations](#-visualizations)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [Limitations & Future Work](#-limitations--future-work)
- [Author](#-author)

---

## 🎯 Project Overview

The project has two parts:

1. **Data cleaning:** inspect the raw dataset, handle missing values, validate the data, and save a cleaned version.
2. **Data visualization:** explore the cleaned data with charts that reveal trends across genres, platforms, publishers, regions, and release years.

---

## 📂 Dataset

| Property | Details |
|---|---|
| **File** | `vgsales.csv` |
| **Rows** | 16,598 |
| **Columns** | 11 |
| **Time span** | 1980 – 2020 |
| **Sales unit** | Millions of copies sold |

| Column | Description |
|---|---|
| `Rank` | Ranking by overall sales |
| `Name` | Name of the game |
| `Platform` | Platform the game was released on (e.g. PS2, Wii, X360) |
| `Year` | Year of release |
| `Genre` | Genre of the game (12 genres) |
| `Publisher` | Company that published the game |
| `NA_Sales` | Sales in North America (millions) |
| `EU_Sales` | Sales in Europe (millions) |
| `JP_Sales` | Sales in Japan (millions) |
| `Other_Sales` | Sales in the rest of the world (millions) |
| `Global_Sales` | Total worldwide sales (millions) |

> 📎 **Dataset source:** *add the link to where you downloaded the dataset here (e.g. Kaggle).*

---

## 🛠 Tools & Libraries

- **Python**
- **Pandas** – data loading and cleaning
- **NumPy** – numerical operations
- **Matplotlib** – plotting
- **Seaborn** – statistical visualizations
- **Jupyter Notebook** – development environment

---

## 🔄 Project Workflow

### 1. Data Exploration
- Previewed the data and checked its shape, data types, column names, and statistical summary (`head()`, `info()`, `describe()`)

### 2. Data Cleaning & Validation

| Check | Finding | Action |
|---|---|---|
| Missing `Year` | 271 values (≈ 1.6%) | Left as missing rather than guessing a release year |
| Missing `Publisher` | 58 values (≈ 0.3%) | Filled with `"Unknown"` |
| Duplicate rows | 0 found | No action needed |
| Extra whitespace in text columns | Checked | Stripped from all text columns |
| Negative sales values | 0 found | No action needed |
| Release year range | 1980 – 2020 | Confirmed valid |
| Regional vs. global sales | Difference between `Global_Sales` and the sum of the four regions is at most ±0.02 | Attributed to rounding; no action needed |
| Unique values | 31 platforms, 12 genres | Checked for inconsistent labels |

The cleaned dataset was saved as `vgsales_cleaned.csv`.

### 3. Data Visualization
Nine visualizations were built from the cleaned data (see below).

---

## 💡 Key Insights

*(Values are approximate, read from the charts in the notebook.)*

- **Genres:** **Action** is the best-selling genre (~1,750M copies), followed by **Sports** (~1,330M) and **Shooter** (~1,040M). **Strategy** is the lowest (~175M).
- **Platforms:** **PS2** leads by a clear margin (~1,255M), followed by **X360**, **PS3**, **Wii**, and **DS**.
- **Publishers:** **Nintendo** is the top publisher (~1,785M), well ahead of **Electronic Arts** (~1,110M) and **Activision** (~725M).
- **Best-selling game:** **Wii Sports** sold about **82.7M** copies, roughly double the second-place game, **Super Mario Bros.** (~40.2M). The top 10 is dominated by Nintendo franchises (Mario, Pokémon, Wii Sports) and classic titles like Tetris and Duck Hunt.
- **Regions:** **North America** accounts for the largest share of sales (~4,400M), followed by **Europe** (~2,440M), **Japan** (~1,290M), and the rest of the world (~800M).
- **Trend over time:** sales grew steadily from the late 1990s, **peaking around 2008** (~680M copies for games released that year), then declined.
- **Sales distribution:** most games sell very few copies, while a small number of blockbusters sell tens of millions. The histogram and genre boxplot show a strongly right-skewed distribution with many high outliers.
- **Correlations:** global sales are most strongly correlated with **North America** (0.94) and **Europe** (0.90) sales, and less so with **Japan** (0.61), which suggests the Japanese market behaves differently from the other regions. Release year has almost no correlation with global sales (−0.07).

---

## 📊 Visualizations

| # | Chart | Type | What it shows |
|---|---|---|---|
| 1 | Total Global Sales by Genre | Bar chart | Which genres sell the most |
| 2 | Top 10 Platforms by Global Sales | Horizontal bar chart | Leading gaming platforms |
| 3 | Global Sales by Release Year | Line chart | Sales trend from 1980 to 2020 |
| 4 | Top 10 Best-Selling Video Games | Horizontal bar chart | Biggest hits of all time |
| 5 | Total Sales by Region | Bar chart | NA vs. EU vs. JP vs. Other |
| 6 | Distribution of Global Sales | Histogram | How sales are spread across games |
| 7 | Global Sales Distribution by Genre | Box plot | Spread and outliers within each genre |
| 8 | Top 10 Publishers by Global Sales | Horizontal bar chart | Leading publishers |
| 9 | Correlation Heatmap | Heatmap | Relationships between numeric columns |

**Sample outputs**

| | |
|---|---|
| ![Sales by Genre](images/genre_sales.png) | ![Top Platforms](images/top_platforms.png) |
| ![Sales Over Time](images/sales_by_year.png) | ![Correlation Heatmap](images/correlation_heatmap.png) |

---

## 📁 Project Structure

```
Video-Game-Sales-Analysis/
│
├── video_games.ipynb          # Main notebook (cleaning + visualization)
├── vgsales.csv                # Raw dataset
├── vgsales_cleaned.csv        # Cleaned dataset
├── images/                    # Saved chart images used in this README
│   ├── genre_sales.png
│   ├── top_platforms.png
│   ├── sales_by_year.png
│   └── correlation_heatmap.png
├── requirements.txt
└── README.md
```

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/Video-Game-Sales-Analysis.git
   cd Video-Game-Sales-Analysis
   ```

2. **Install the dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook
   ```

4. Open `video_games.ipynb` and run all cells (**Kernel → Restart & Run All**). Make sure `vgsales.csv` is in the same folder as the notebook.

**`requirements.txt`**
```
pandas
numpy
matplotlib
seaborn
jupyter
```

---

