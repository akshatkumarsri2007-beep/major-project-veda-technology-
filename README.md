# major-project-veda-technology-
# OTT Streaming Content Trend Analysis (Netflix)

Exploratory data analysis of Netflix's content catalog to find patterns in genre popularity, ratings, release trends and regional content mix, finished with a content strategy memo for a content acquisition team.

**Author:** Akshat Srivastava
**Project:** Veda Technology Internship, Project 1

---

## Business question

What does Netflix's catalog tell us about what to greenlight next?

## Dataset

[Netflix Movies and Tv Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows) (Kaggle, shivamb)

- 8,807 titles (6,131 movies and 2,676 TV shows), 12 columns
- Release years 1925 to 2021; titles added to Netflix between 2008 and September 2021
- Catalog data only: there is no viewership or engagement data

## Key findings

| # | Finding | Evidence |
|---|---------|----------|
| 1 | **Movies are getting shorter** | Movies under 90 min rose from 16.8% (released 2000-09) to 34.7% (2016-21); average runtime fell from 112 to 95 min |
| 2 | **Growth is coming from international markets** | Titles released in 2017-21 vs 2012-16: Spain +172%, Mexico +159%, Japan +115%, South Korea +88%. The US share stayed roughly flat (38.9% to 39.6%) |
| 3 | **Most TV shows are one-and-done** | 67.0% of TV shows have one season, only 17.1% have three or more. The pattern holds for older shows too (68.5% of shows released in 2018 or earlier) |

Other numbers: 45.5% of titles are adult-rated, the median movie is 98 minutes long, the United States appears on 41.9% of titles and India on 11.9%.

### Recommendations

1. Prioritise tightly paced films in the 85-100 minute range.
2. Increase investment in Spanish-language, Mexican, Korean and Japanese originals, where growth is strongest.
3. Treat limited series with a planned ending as the default TV format, and commit to multi-season runs only for proven shows.

## What's in this repo

| File | Description |
|------|-------------|
| `netflix_eda.ipynb` | Full analysis: cleaning, 8 visualizations, SQL queries and memo charts |
| `queries.sql` | 10 SQL queries (aggregations, joins, window functions) |
| `report/Netflix_Content_Trend_Analysis_Report.pdf` | 7-page written report with findings and recommendations |
| `memo/` | Content strategy memo (3 actionable insights) |
| `charts/` | Charts used in the memo |

## Approach

1. **Load and inspect** the raw catalog.
2. **Clean the data**
   - Fixed 3 rows where the runtime was stored in the `rating` column
   - Filled missing director, cast and country with "Unknown"; missing rating as "Not Rated"
   - Parsed `date_added` and split `duration` into minutes (movies) and seasons (TV shows)
   - Split multi-value genre and country columns and grouped ratings into age groups
3. **Explore visually** with 8 charts: catalog split, titles added per year, top genres, genre mix over time, countries, ratings and audience, movie duration trend, seasons per show.
4. **Validate in SQL** (SQLite): 10 queries reproducing the key figures, including multi-table joins and window functions.
5. **Write the memo** with three insights, each with evidence and a recommendation.

## SQL queries

| Query | Question | Technique |
|-------|----------|-----------|
| Q1 | Movies vs TV shows split | `GROUP BY`, subquery |
| Q2 | Titles added per year, with TV share | Conditional aggregation |
| Q3 | Top 10 genres | Helper table, `GROUP BY` |
| Q4 | Top 10 countries | Helper table, `GROUP BY` |
| Q5 | Top genres among Indian titles | Three-table `JOIN` |
| Q6 | Movie duration by period | `CASE`, `AVG` |
| Q7 | Age-group share within each type | Window function |
| Q8 | Seasons distribution | `CASE`, subquery |
| Q9 | Top genre per country | `JOIN`, `ROW_NUMBER()` |
| Q10 | Fastest-growing countries | `JOIN`, `HAVING`, `NULLIF` |

## Tools

Python (Pandas, NumPy, Matplotlib, Seaborn, Plotly), SQL (SQLite), Google Colab

## Author

**Akshat Srivastava**
