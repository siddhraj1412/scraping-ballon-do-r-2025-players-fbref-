# Ballon d'Or 2025 Nominees Stats Dataset

Dataset link :- https://www.kaggle.com/datasets/siddhrajthakor/ballon-dor-2025-nominees-players-standard-stats

This repository contains a scraped dataset of player statistics for the 30 men's nominees of the 2025 Ballon d'Or, focused on top 5 European leagues (Premier League, La Liga, Bundesliga, Serie A, Ligue 1). Data sourced from FBref.com for the 2024–25 season.

## Dataset Overview
- **Columns**: Player, Nation, Pos, Squad, Gls, Ast, Min, Gls/90, xG, League (added for source tracking), and more (full stats like playing time, per-90 metrics).
- **Files**:
  - `all_nominees_stats.csv`: Merged dataset with nominees only (~30 rows).
  - League-specific CSVs (e.g., `premier_nominees.csv`) in `/data/raw/`.
- **Filtering**: Only Ballon d'Or nominees included, using a predefined list of names.
- **Scraping Method**: Used Python with pandas, requests, and BeautifulSoup to scrape FBref tables from commented HTML sections.

Example preview (top rows):
| Player         | Nation | Pos  | Squad     | Gls | Ast | League        |
|----------------|--------|------|-----------|-----|-----|---------------|
| Mohamed Salah | eg EGY | FW  | Liverpool | 33  | 23  | Premier League|
| Lamine Yamal  | es ESP | FW  | Barcelona | ... | ... | La Liga      |

## How to Use
1. Download the CSVs.
2. Load in Python: `import pandas as pd; df = pd.read_csv('all_nominees_stats.csv')`.
3. Analyze: e.g., `df.nlargest(5, 'Gls')` for top scorers.

## Scraping Reproduction
The dataset was created using these steps:
1. Scrape league pages (e.g., https://fbref.com/en/comps/9/stats/Premier-League-Stats).
2. Extract commented tables via BeautifulSoup.
3. Flatten multi-index columns.
4. Filter for nominees: `df[df['Player'].isin(nominees_list)]`.
5. Merge with `pd.concat()` and add 'League' column.
6. Save CSVs.

Code snippets provided in chat history for full reproduction. No additional dependencies beyond standard (pandas, requests, bs4).

## Sources
- FBref.com for stats.
- Official 2025 nominees list from France Football announcements.

For questions, open an issue.
