# IMDb Data Analysis:

A comprehensive data science project demonstrating end-to-end data analysis—from wrangling 5+ fragmented IMDb datasets into a unified pipeline to extracting actionable insights through advanced exploratory data analysis.

---

## 📋 Project Summary

This project is a real-world chronicle of transforming a massive, fragmented, and messy IMDb dataset into a powerful analytical tool. I single-handedly navigated multiple complex files, executed a multi-stage data wrangling process to forge a single unified dataset, and then performed a deep-dive exploratory analysis to uncover hidden trends in the film industry.

This repository doesn't just show the final product—it showcases my end-to-end capabilities in data preparation, strategic cleaning, and curiosity-driven analysis.

---

## 🎯 The Challenge: Tackling a Messy, Real-World Dataset

This wasn't a simple `pd.read_csv()` and plot project. The initial dataset was spread across several large files, each with its own quirks and challenges that I had to overcome:

- **Disparate Data Sources**: Information fragmented across multiple files (`title.basics`, `title.ratings`, `name.basics`, `title.crew`, etc.), requiring strategic merging approaches
- **Data Integrity Issues**: Raw data plagued with missing values, incorrect data types (e.g., runtime stored as object instead of numeric), and vast amounts of irrelevant entries (TV shorts, non-commercial videos)
- **Statistical Noise**: Thousands of movies with very few votes, making their ratings statistically insignificant—required devising a filtering strategy for meaningful analysis
- **Complex Relationships**: Linking movies (`tconst`) to people (`nconst`) across different files and roles (director, actor, writer) demanded careful and precise merging logic

---

## 🔧 My Process: From Chaos to Clarity

I structured my workflow across several notebooks, creating a logical and reproducible pipeline from raw data to final insights.

### Phase 1: Forging the Master Dataset (The Wrangling)

My first priority was to build a clean, reliable dataset.

**Data_Wrangling.ipynb**: Started by merging core movie titles and ratings. Immediately performed critical cleaning tasks like fixing data types and handling missing information. Crucially, made the strategic decision to **filter out 70%+ of movies** with low vote counts—essential for removing noise and ensuring analysis integrity.

**Data_Wrangling2.ipynb**: With a solid base, enriched the dataset by integrating the creative minds behind the movies—directors and writers. This involved careful merging that linked people to productions.

**Data_Wrangling3.ipynb**: In the final and most complex wrangling step, integrated the principal cast (actors, actresses, etc.). Required meticulous handling of different roles and joining them to the main dataset, resulting in a single, comprehensive, analysis-ready master file.

### Phase 2: Uncovering the Story (The EDA)

With a clean dataset, I could finally start asking interesting questions.

**EDA1.ipynb**: Started broad, analyzing the entire genre landscape to see which film types are most common versus most critically acclaimed. Then narrowed focus to top director careers, using data to identify success patterns.

**EDA2.ipynb**: Expanded analysis to cast, investigating star power and exploring correlations between a film's runtime, release year, and eventual rating—uncovering the "sweet spot" for movie length.

---

## 🌟 Key Findings & Deeper Insights

My analysis yielded several fascinating insights into the film industry:

### The "Funnel of Quality"
Discovered a strong relationship between the number of votes a movie receives and its rating. While popular movies aren't always highly rated, it's extremely rare to find a movie with a massive number of votes and a very low rating. This suggests that a certain quality threshold is necessary to achieve widespread viewership.

### Genre Disparity
While Drama and Comedy are the most frequently produced genres, they don't hold the top spots for ratings. Niche genres like Documentary, Biography, and History consistently achieve higher average ratings, indicating a dedicated and appreciative audience.

### Director Versatility is Key
When analyzing the filmographies of top directors like Christopher Nolan and Martin Scorsese, I found that while they have signature genres, they are also highly versatile. The ability to successfully direct films across multiple genres is a hallmark of the industry's most respected creators.

### The Runtime "Sweet Spot"
Analysis revealed that movies with a runtime between **90 and 120 minutes** tend to receive the highest ratings from audiences. Films that are too short may be perceived as underdeveloped, while those that are excessively long risk pacing issues—pointing to an optimal length for audience satisfaction.

---

## 🛠️ Technical Stack

| Category | Technologies | Purpose |
|----------|-------------|---------|
| **Language** | Python 3.x | Core programming language |
| **Data Processing** | Pandas, NumPy | Data manipulation and numerical operations |
| **Visualization** | Matplotlib, Seaborn | Creating insightful plots and charts |
| **Environment** | Jupyter Notebook | Interactive development and analysis |

---

## 📊 Analysis Pipeline

```
1. Data Wrangling       → Raw .tsv files cleaned and merged
2. Crew Integration     → Director/writer data joined
3. Cast Integration     → Principal cast data merged
4. Genre Analysis       → Production vs. quality patterns
5. Correlation Study    → Runtime, votes, rating relationships
```

---

## 🔍 Methodology

### Data Wrangling (Notebooks 1-3)
1. **Initial Cleaning**: Loaded 5+ raw IMDb `.tsv` files, handled inconsistent schemas
2. **Strategic Filtering**: Applied minimum vote thresholds to eliminate statistical noise
3. **Multi-stage Merging**: Progressively joined datasets on common keys (`tconst`, `nconst`)
4. **Type Optimization**: Converted data types for memory efficiency and proper analysis

### Exploratory Data Analysis (Notebooks 4-5)
1. **Genre Distribution**: Analyzed production frequency vs. average ratings
2. **Director Patterns**: Examined filmography diversity of top-rated directors
3. **Feature Correlations**: Investigated relationships between votes, runtime, and ratings
4. **Cast Analysis**: Explored impact of principal cast on movie success

---

## 📈 Key Visualizations

- **Genre Production vs. Quality Matrix**: Scatter plots revealing the inverse relationship between volume and quality
- **Rating Distribution Histograms**: Understanding the "Funnel of Quality" effect
- **Runtime vs. Rating Curves**: Identifying the optimal movie length (90-120 min sweet spot)
- **Director Genre Diversity Charts**: Mapping versatility across top creators

---

## 🧠 Skills Demonstrated

- **Data Wrangling**: Complex multi-file merging, missing data strategies, outlier detection
- **Statistical Analysis**: Correlation analysis, distribution analysis, hypothesis testing
- **Data Visualization**: Creating publication-quality plots for insight communication
- **Domain Knowledge**: Understanding film industry metrics and audience behavior patterns
- **Code Organization**: Modular, reproducible notebook structure
- **Critical Thinking**: Strategic decision-making on data filtering and quality thresholds

---

## 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/whyVedang/EDA-and-ML/tree/main/EDA/EDA_IMDB_Self
cd EDA_IMDB_Self

# Install dependencies
pip install pandas numpy matplotlib seaborn jupyterlab

# Download IMDb datasets to data/ folder
# Launch Jupyter
jupyter lab
```

### Required Datasets (place in `data/` folder):
- `title.basics.tsv` - Basic title information
- `title.ratings.tsv` - Ratings and vote counts
- `title.crew.tsv` - Directors and writers
- `name.basics.tsv` - Names and professions
- `title.principals.tsv` - Principal cast and crew

Download from: [IMDb Datasets](https://datasets.imdbws.com/)

---

## 📁 Project Structure

```
imdb-data-analysis/
├── notebooks/
│   ├── 1_Data_Wrangling.ipynb           # Data loading and cleaning
│   ├── 2_Data_Wrangling_Crew.ipynb      # Crew data integration
│   ├── 3_Data_Wrangling_Cast.ipynb      # Cast data integration
│   ├── 4_EDA_Genres_Directors.ipynb     # Genre and director analysis
│   └── 5_EDA_Cast_Correlations.ipynb    # Correlation analysis
├── data/                                 # Raw IMDb .tsv files (not included)
└── README.md
```

---

## 🎓 Learning Outcomes

- Mastered handling large-scale, real-world messy datasets with millions of records
- Applied advanced Pandas techniques for multi-file data integration
- Developed intuition for data quality assessment and strategic noise reduction
- Created compelling visualizations to communicate complex findings
- Practiced reproducible data science workflow design
- Gained domain expertise in film industry metrics and patterns

---

## 🔮 Future Enhancements

- [ ] Time-series analysis of rating trends over decades
- [ ] Predictive modeling for movie success using machine learning
- [ ] Natural language processing on plot summaries and reviews
- [ ] Interactive dashboard with Plotly/Dash for dynamic exploration
- [ ] Budget vs. revenue analysis (with additional data sources)
- [ ] Sentiment analysis on user reviews

---

## 📝 Key Takeaways

> **"More production doesn't equal better quality—Drama may dominate quantity, but Documentary dominates quality ratings."**

> **"The 'Funnel of Quality': Movies that attract more votes consistently achieve higher ratings, suggesting word-of-mouth amplifies quality films."**

> **"Director versatility across genres is a stronger predictor of long-term success than genre specialization."**

---

**Author**: Vedang  
**Project Type**: Data Science, Exploratory Data Analysis  
**Skills**: Python, Pandas, Data Wrangling, Statistical Analysis, Data Visualization

---
