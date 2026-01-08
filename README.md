# Movie & Streaming Analytics Lakehouse

This project analyses factors that influence the performance of the audiovisual sector, combining cinema, streaming, piracy, ratings and awards data from multiple Kaggle datasets. 

## Business context and goals

We work in the context of the film and streaming industry, where piracy, release strategy and audience/critic reception strongly affect revenue and reputation. 

Main goals:

- Analyse piracy patterns over time and around the release window.
- Evaluate the impact of release timing and initial leaks on piracy exposure.
- Study the evolution of global box office revenue and number of films released.
- Compare ratings across platforms (IMDB, TMDB, Rotten Tomatoes) and between critics and audience.
- Analyse awards and recognition patterns (Oscars) over time.

## Lakehouse architecture

We adopt a **Data Lakehouse** architecture with three layers:

- **Bronze:** raw Kaggle datasets (CSV/JSON) about box office, streaming titles, piracy, audience and critic reviews, and Oscars.  
- **Silver:** cleaned and standardised tables (e.g. `movies_info`, `dataset_piracy`, `rotten_tomatoes_movies`, `the_oscar_award`, unified `titles`).  
- **Gold:** dimensional model centred on `dim_title`, with dimensions such as time, genre, platform, rating status and awards, and fact tables for piracy views/downloads, box office, ratings and views.

Notebooks:

- `bronze.ipynb` – ingestion, basic quality checks, handling missing values, duplicates, invalid formats and high cardinality issues.  
- `silver.ipynb` – transformations and normalisation, building clean conformed tables.  
- `create_gold-18.ipynb` – creation of the dimensional model and analytical Gold tables. 

## Analytical questions and dashboards

From the Gold model we answer questions such as: 

- How do piracy levels differ between titles with and without an initial leak, and how does this evolve over time?  
- Is piracy concentrated in a specific window after release (days since release vs piracy views)?  
- How has global box office revenue evolved by decade, and how does that relate to the number of films released each year?  
- Are ratings consistent across platforms (IMDB, TMDB, Rotten Tomatoes)?  
- How do critic and audience ratings differ, and how often do we see large discrepancies?  
- What are the patterns of Oscar nominations and wins by category, person and over time?

Dashboards include:

- **Piracy Exposure & Release Timing** – days since release, initial leak flag and piracy intensity.  
- **Global Box Office Evolution** – revenue and count of titles over time.  
- **Cinema vs Streaming ROI** – difference in investment, risk and average ROI between theatrical and streaming releases.  
- **Cross-Platform Rating Consistency** – correlation between rating platforms.  
- **Critic vs Audience Distribution** – distribution of differences and identification of outliers.  
- **Awards Distribution & Recognition Patterns** – Oscars by category, person and year. 

## Technology

- Python + Jupyter for all transformations (Bronze, Silver, Gold).  
- Data Lakehouse approach compatible with Spark/Hive environments and BI tools (e.g. Tableau / Power BI) for dashboards. 
