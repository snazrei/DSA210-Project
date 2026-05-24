# DSA210 Final Project Report

**What Makes a Movie Successful?**
 
## 1. Motivation

Movies are one of the most widely consumed forms of entertainment in the world, yet what separates a blockbuster hit from a box-office flop remains a fascinating and commercially important question. The film industry involves massive investments — studios routinely spend hundreds of millions of dollars on production and marketing — and understanding which factors predict success can have real consequences for decision-makers.

This project was motivated by a genuine curiosity about the data science behind the entertainment industry. Specifically, the central question is:

 **Can we identify measurable factors — such as budget, genre, or release era — that consistently predict a movie's commercial and critical success?**

Beyond pure curiosity, this analysis has practical relevance for filmmakers, streaming platforms like Netflix, and investors who need to allocate resources intelligently. By analyzing real-world data from two large movie databases, this project applies core data science techniques — exploratory data analysis, visualization, and hypothesis testing — to uncover meaningful patterns in the film industry.


## 2. Data Sources

Two publicly available datasets were used in this project, each offering a complementary perspective on the movie landscape.

### 2.1 TMDb Movies Dataset

The **TMDb** dataset aggregates metadata on tens of thousands of films. Key features include:

- **Title** — Movie name
- **Budget** — Production budget (in USD)
- **Revenue** — Box office revenue (in USD)
- **Genres** — One or more genre labels per film
- **Vote Average / Vote Count** — Community rating and engagement
- **Release Date** — Used to derive release year and decade
- **Popularity** — A TMDb-specific popularity score

### 2.2 Netflix Titles Dataset

The **Netflix Titles** dataset provides information on streaming content, including:

- **Type** — Movie or TV Show
- **Title** — Content name
- **Director / Cast** — Creative team information
- **Country** — Country of production
- **Release Year** — Year of original release
- **Rating** — Content rating (e.g., PG, R)
- **Duration** — Runtime or number of seasons

### 2.3 Data Collection

Both datasets were sourced from **Kaggle**. They are publicly available for academic use. 

## 3. Data Analysis

The analysis was conducted in a Jupyter Notebook (`analysis.ipynb`) using Python, through three main stages: data cleaning, EDA, and hypothesis testing.

### 3.1 Data Cleaning & Feature Engineering

- **Handling missing values:** Rows with missing or zero values for budget and revenue were removed.
- **Type conversion:** Release dates were parsed into datetime objects; financial columns were cast to numeric types.
- **Feature engineering:**
  - A **profit** column was derived as `revenue - budget`.
  - A **profit margin** column was computed as `profit / budget * 100`.
  - A **decade** column was extracted from the release year.
  - Genre columns were exploded where a film listed multiple genres.
- **Merging datasets:** TMDb and Netflix datasets were cross-referenced by title where applicable.

**Libraries used:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`

### 3.2 Exploratory Data Analysis (EDA)

**Profit Distribution:** A histogram revealed a heavily right-skewed distribution — most movies make modest profits while a small number of blockbusters generate extremely high returns.

**Revenue by Genre:** A bar chart showed that Action, Adventure, and Animation films consistently generate the highest average revenue, while Documentary and Foreign films tend to have the lowest.

**Budget vs. Revenue:** A scatter plot revealed a positive association — higher-budget films tend to generate higher revenue — though with considerable variance.

**Ratings by Decade:** A line plot showed that older films (pre-1980s) tend to have higher average ratings, likely due to survivorship bias.

## 3.3 Hypothesis Testing

**Test 1 — Pearson Correlation: Budget vs. Revenue**
- H₀: There is no linear correlation between budget and revenue.
- Result: Statistically significant positive correlation found (p < 0.05).

**Test 2 — ANOVA: Revenue Differences Across Genres**
- H₀: Mean revenue is equal across all genres.
- Result: Statistically significant differences found between genre groups (p < 0.05).

**Test 3 — t-Test: Ratings Over Time**
- H₀: No significant difference in ratings between pre- and post-2000 films.
- Result: Pre-2000 films scored significantly higher on average, consistent with survivorship bias.

## 4. Findings

**Budget is a significant but imperfect predictor of revenue.** The Pearson correlation confirmed a meaningful positive relationship between production budget and box-office revenue. However, high budgets do not guarantee financial success — some low-budget films outperform expensive productions.

**Genre is a strong driver of commercial performance.** Action, Adventure, and Animation dominate in terms of revenue, while Horror can achieve high profit margins despite lower budgets due to cheap production costs.

**Profit distributions are highly unequal.** The vast majority of films cluster around modest profit levels, with a small number of mega-hits accounting for a disproportionate share of total industry revenue.

**Audience ratings favor older films — likely due to survivorship bias.** Pre-2000 films score higher on average not because they are objectively better, but because only the most celebrated ones remain in the dataset.

**Streaming-era content skews toward certain genres.** The Netflix dataset reflects a strategic mix of drama, international content, and documentaries alongside broader genre diversity compared to the theatrical landscape in TMDb.


## 5. Limitations and Future Work

**Data completeness:** A significant portion of TMDb had missing budget/revenue values, creating selection bias toward larger studio productions.

**Survivorship bias:** Rating comparisons across decades are affected by the fact that only celebrated older films remain well-known.

**Profit as a metric:** Box-office revenue does not account for marketing spend, streaming rights, merchandise, or home video sales.

**No causal inference:** All findings are correlational. Budget does not *cause* higher revenue — there are many confounding variables.

**Future Work:**
- Sentiment analysis on critic and audience reviews
- Machine learning models to predict revenue from multiple features
- Deeper analysis of director and cast effects
- Streaming vs. theatrical performance comparison
- Time series analysis of genre trends over decades

## 6. AI Assistance Disclosure

This project used Claude (Anthropic) as an AI assistant for:

- Writing and debugging the data cleaning code
- Structuring the EDA visualizations using `matplotlib` and `seaborn`
- Writing the hypothesis testing code

Prompts used included:
- "Write data cleaning code for my TMDb and Netflix CSV files"
- "Write EDA code with matplotlib for movie data"
- "Write hypothesis tests for budget vs revenue correlation, genre revenue differences, and rating trends over time"




