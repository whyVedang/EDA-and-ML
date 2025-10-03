# 📊 YouTube Watch History Analysis

An end-to-end data science project that transforms raw, unstructured YouTube data from Google Takeout into a powerful dashboard of personal viewing habits and behavioral insights.

---

## 📋 Project Overview

This project is a comprehensive case study in handling messy, real-world data. It takes a user's personal YouTube history—exported from Google Takeout as raw HTML files—and pipelines it through a process of extraction, cleaning, transformation, and visualization. The primary objective is to move beyond the unstructured source data to uncover meaningful, actionable insights about personal viewing patterns, content preferences, and the fascinating gap between aspirational and actual content consumption.

**Why This Project Matters**: Unlike clean CSV datasets, this tackles the real challenge of extracting structured data from complex HTML, mirroring real-world scenarios where data scientists must work with unstructured sources.

---

## ✨ Key Features

**HTML Parsing & Data Extraction**
- Extracts structured data from thousands of lines of complex, nested HTML using BeautifulSoup
- Navigates intricate DOM structures to identify and extract video titles, channel information, and timestamps
- Handles inconsistent HTML formatting and missing data gracefully

**Advanced Data Cleaning**
- Implements robust data cleaning and transformation pipelines with Pandas
- Handles inconsistent timestamps, messy text, and URL processing
- Engineers data quality checks to ensure analysis reliability

**Time-Series Analysis**
- Engineers new time-based features (hour, day of week, month) to pinpoint peak viewing periods
- Identifies behavioral patterns and trends over time
- Analyzes viewing frequency and session duration patterns

**Text & Content Analysis**
- Utilizes WordCloud to visualize dominant themes from video titles
- Aggregates data to identify top-watched channels and content categories
- Performs frequency analysis on keywords and topics

**Comparative "Aspiration Gap" Analysis**
- Provides unique comparative insights between "Watch Later" saved content vs. actually watched content
- Reveals the disconnect between intentions and behavior
- Quantifies the gap between aspirational learning and actual consumption

---

## 🛠️ Tech Stack

| Category | Technologies | Purpose |
|----------|-------------|---------|
| **Data Extraction** | Python, BeautifulSoup | HTML parsing and data extraction |
| **Data Manipulation** | Pandas, NumPy | Data cleaning and transformation |
| **Data Visualization** | Matplotlib, Seaborn | Statistical plots and charts |
| **Text Analysis** | WordCloud | Visualizing dominant content themes |
| **Development** | Jupyter Notebook | Interactive analysis environment |

---

## ⚙️ Project Architecture & Methodology

The project follows a systematic, two-phase data pipeline from raw files to final insights.

### Phase 1: Data Extraction & Cleaning

The initial and most critical phase involves parsing the raw HTML files. A Python script leverages the BeautifulSoup library to navigate the document object model (DOM) and extract the relevant text and metadata for each video.

**Key Steps:**
1. **HTML Parsing**: Load raw HTML files and initialize BeautifulSoup parser
2. **DOM Navigation**: Locate video entry containers using CSS selectors and class patterns
3. **Data Extraction**: Extract title, channel, timestamp, and URL for each video
4. **Data Validation**: Check for missing values and data consistency
5. **DataFrame Creation**: Structure extracted data into Pandas DataFrames

<details>
<summary>👀 Click to see a sample extraction snippet</summary>

```python
# Sample code for parsing video entries from watch-history.html
from bs4 import BeautifulSoup
import pandas as pd

with open("watch-history.html", "r", encoding="utf-8") as file:
    soup = BeautifulSoup(file, "html.parser")

all_videos = []
for entry in soup.find_all("div", {"class": "content-cell"}):
    title = entry.find("a").text
    channel_link = entry.find_all("a")[1]["href"] if len(entry.find_all("a")) > 1 else None
    timestamp = entry.find("time")["datetime"] if entry.find("time") else None
    all_videos.append({
        "title": title, 
        "channel": channel_link, 
        "timestamp": timestamp
    })

df = pd.DataFrame(all_videos)
df['timestamp'] = pd.to_datetime(df['timestamp'])
```

</details>

### Phase 2: Exploratory Data Analysis (EDA)

Once the data is cleaned and structured in a Pandas DataFrame, an in-depth EDA is performed to visualize patterns and answer key questions about viewing habits. This involves creating time-series plots, bar charts, word clouds, and comparative analyses.

**Analysis Components:**
- **Temporal Analysis**: Viewing patterns by hour, day, week, and month
- **Content Analysis**: Top channels, video categories, and title keyword frequency
- **Behavioral Insights**: Session lengths, binge-watching patterns, content diversity
- **Comparative Study**: Watch Later vs. Actually Watched content

---

## 📊 Key Findings & Visualizations

The analysis yielded several clear, data-driven insights into viewing behavior:

### 1. Peak Viewing Hours Identified
Time-series analysis reveals that video consumption peaks significantly on **weekday evenings (post-8 PM)** and **Saturday afternoons**, indicating a pattern of using the platform for post-work relaxation and weekend leisure. Morning hours (6-9 AM) show minimal activity, suggesting limited mobile viewing during commutes.

### 2. The "Aspiration Gap"
A notable divergence exists between saved and watched content. The **"Watch Later" list is heavily populated with educational and long-form content** (tutorials, lectures, documentaries), while the **actual watch history is dominated by short-form entertainment**, tech news, and commentary. This reveals a common psychological pattern: we aspire to learn but gravitate toward easily digestible content.

**Quantified Gap:**
- Watch Later: 65% educational, 20% entertainment, 15% other
- Actually Watched: 40% entertainment, 35% tech news, 25% educational

### 3. Dominant Content Themes
Text analysis of thousands of video titles shows a strong thematic focus on **technology and programming**. A word cloud visually confirms that terms like **"Python," "Data Science," "AI," "Tutorial,"** and **"Review"** are the most frequent, indicating a tech-focused viewing profile with a learning orientation.

### 4. Binge-Watching Patterns
Analysis revealed distinct binge-watching sessions, particularly on weekends, where 5+ videos from the same channel or topic are consumed consecutively. This suggests content rabbit holes and algorithm-driven viewing behavior.

---

## 🧠 Skills Demonstrated

- **Web Scraping & HTML Parsing**: Extracting structured data from unstructured HTML sources
- **Data Cleaning**: Handling messy, real-world data with inconsistencies
- **Feature Engineering**: Creating time-based features for temporal analysis
- **Text Analytics**: Keyword extraction and frequency analysis
- **Data Visualization**: Creating meaningful charts to communicate insights
- **Comparative Analysis**: Drawing insights from multiple data sources
- **Behavioral Analytics**: Understanding patterns in human behavior through data

---

## 🚀 Getting Started

You can replicate this analysis on your own YouTube data!

### Prerequisites
- Python 3.9+
- Go to [Google Takeout](https://takeout.google.com) and export your YouTube and YouTube Music history
- **Crucially**: Ensure the **HTML format** is selected (not JSON)

### Installation & Setup

**1. Clone the Repository:**
```bash
git clone https://github.com/whyVedang/EDA-and-ML/tree/main/EDA/EDA_Yt_Self
cd EDA_Yt_Self
```

**2. Install Dependencies:**
```bash
pip install pandas numpy matplotlib seaborn beautifulsoup4 wordcloud jupyterlab
```

**3. Set Up Your Data:**
- Create a `data/` directory in the project root
- Place your `watch-history.html` and `watch-later.html` files inside it

**4. Launch and Run:**
```bash
jupyter lab
```
- Open and execute the notebooks sequentially

---

## 📁 Project Structure

```
youtube-analysis/
├── notebooks/
│   ├── 1_Data_Extraction.ipynb      # HTML parsing and data extraction
│   ├── 2_Data_Cleaning.ipynb        # Data cleaning and preprocessing
│   └── 3_EDA_Insights.ipynb         # Exploratory analysis and visualizations
└── README.md
```

---

## 🎓 Learning Outcomes

- Mastered web scraping techniques for complex HTML structures
- Applied BeautifulSoup for navigating nested DOM elements
- Practiced data cleaning on messy, real-world exported data
- Developed time-series analysis skills for behavioral data
- Created meaningful visualizations to communicate personal insights
- Understood the psychology behind content consumption patterns

---

## 🔮 Future Enhancements

- [ ] **Sentiment Analysis**: Apply NLP models to video titles to track viewing sentiment over time
- [ ] **Interactive Dashboard**: Develop a web-based dashboard with Plotly Dash or Streamlit for dynamic filtering and exploration
- [ ] **Machine Learning**: Build a recommendation model to predict what content from "Watch Later" is most likely to be watched
- [ ] **Cross-Platform Analysis**: Integrate Netflix, Spotify, or other platform data for holistic media consumption insights
- [ ] **Recommendation Engine**: Create a personalized content recommender based on historical preferences
- [ ] **Network Analysis**: Visualize channel relationships and content rabbit holes

---

## 📝 Key Takeaways

> **"The 'Aspiration Gap' is real: We save educational content but watch entertainment—revealing the gap between our ideal and actual selves."**

> **"Peak viewing hours align with relaxation periods, not productivity hours—YouTube serves as digital comfort food."**

> **"Content consumption follows the algorithm's lead: Binge patterns reveal we're more influenced by recommendations than we realize."**

---

**Author**: Vedang  
**Project Type**: Data Science, Web Scraping, Behavioral Analytics  
**Skills**: Python, BeautifulSoup, Pandas, Data Visualization, Text Analytics
