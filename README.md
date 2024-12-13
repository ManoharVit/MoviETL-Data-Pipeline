# MoviETL: Data Pipeline for Film Industry Analytics

## Introduction

MoviETL represents a state-of-the-art data pipeline designed specifically for analytical stakeholders in the film industry. This pipeline facilitates robust insights into movie ratings, audience preferences, and financial metrics, aiding in sophisticated, data-driven decision-making processes.

## Objectives

- **Top-Rated Movies Analysis**: Leverage historical data to identify and analyze top-rated films.
- **Audience Preference Quantification by Genre**: Systematically categorize and evaluate viewer preferences across various genres.
- **Seasonal Impact on Box Office Revenues**: Investigate how seasonal variations influence box office performance.
- **Inflation-Adjusted Financial Insights**: Provide detailed financial analyses adjusted for inflation to assess genre-based profitability.

## Project Structure
```bash
.
├── Dockerfile
├── LICENSE
├── README.md
├── config
│   └── airflow.cfg
├── dags
│   ├── bash_scripts
│   │   └── load_staging_table.sh
│   ├── movies_dwh_dag.py
│   ├── python_scripts
│   │   ├── load_staging_cpi.py
│   │   ├── load_staging_date.py
│   │   ├── load_staging_genre.py
│   │   ├── load_staging_movies.py
│   │   └── load_staging_ratings.py
│   └── sql_scripts
│       ├── create_tables.sql
│       ├── upsert_cpi.sql
│       ├── upsert_date.sql
│       ├── upsert_genre.sql
│       ├── upsert_movies.sql
│       └── upsert_ratings.sql
├── docker-compose-LocalExecutor.yml
├── movietl.txtx
├── plugins
│   ├── __init__.py
│   └── operators
│       ├── __init__.py
│       └── data_quality.py
└── script
    └── entrypoint.sh

```

## Data Sources

- **Primary Dataset**: The [Movielens dataset](https://www.kaggle.com/rounakbanik/the-movies-dataset) sourced from Kaggle, encompassing over 26 million user ratings and details on 45,000 films.
- **Supplementary Data**: Consumer Price Index data from [Fred St. Louis](https://fred.stlouisfed.org/series/CUSR0000SS62031), employed to adjust financial figures for inflation.

## Technical Architecture

- **Extraction**: Data is sourced via the Kaggle API and through direct API requests to Fred St. Louis for CPI data.
- **Transformation**: Utilizes Apache Spark for its distributed data processing capabilities, ensuring efficient and scalable handling of extensive datasets.
- **Loading**: Employs AWS Redshift for its high-capacity data warehousing solutions.
- **Orchestration**: Managed through Apache Airflow, which orchestrates the workflow, ensuring robust and timely data processing.

## Rationale for Technology Selection

- **Apache Spark**: Selected for its superior scalability and performance in processing large datasets.
- **Apache Airflow**: Provides sophisticated ETL management and workflow scheduling capabilities.
- **AWS Redshift**: Chosen for its scalability and integration features suitable for extensive data storage requirements.
- **Docker**: Ensures a consistent environment across development and operational phases, mitigating potential discrepancies.

## Data Modeling Strategy

Emphasizes data normalization to enhance storage efficiency, maintain integrity, and support effective and efficient CRUD operations.

## Anticipated Scenarios and Proposed Solutions

- **Increased Data Volume**: Augment the Spark cluster with additional nodes and optimize data segmentation via Airflow to handle increased loads effectively.
- **Daily Pipeline Execution**: Adapt Airflow configuration to accommodate daily scheduling requirements, ensuring that the pipeline executes prior to daily deadlines.
- **High User Concurrency**: Strategically scale Redshift resources and optimize query processing by utilizing pre-aggregated data and query optimization techniques based on user activity patterns.

## Future Directions

- **Enhanced Scalability**: Continually adapt infrastructure to meet evolving data demands using scalable technologies like Spark and Redshift.
- **Increased Automation**: Modify Airflow schedules to increase data update frequency, thus providing more timely insights.
- **Improved Concurrency Management**: Utilize Redshift’s robust architecture to maintain efficient query performance under high user load.

## Deployment Guidelines

Provides comprehensive deployment instructions, covering Docker containerization, Airflow configuration, and overall setup to facilitate a seamless implementation process.

## Conclusion

MoviETL is engineered to offer a dynamic and adaptive solution for in-depth analysis of the film industry, combining advanced data handling technologies with strategic insights to empower stakeholders to make well-informed decisions.