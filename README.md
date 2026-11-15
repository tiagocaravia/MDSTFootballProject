# MDST Football Project

A data-driven football analytics project focused on fantasy football value estimation, player performance analysis, and predictive modeling. This repository consolidates NFL player stat data, team defense data, and analytical notebooks to evaluate how usage patterns, efficiency metrics, and team context influence fantasy production.

## Project Overview

This project was designed to explore how football statistics can be transformed into actionable insights for fantasy analysis. The work combines data preparation, exploratory analysis, and predictive modeling to study player performance across multiple seasons.

The analysis emphasizes the four fantasy-relevant positions:

- Quarterback (QB)
- Running Back (RB)
- Wide Receiver (WR)
- Tight End (TE)

The underlying objective is to quantify which factors most strongly correlate with fantasy output and to assess whether these signals can be used for predictive modeling and player segmentation.

## Core Objectives

- Clean and combine raw football datasets into a usable analytical foundation
- Evaluate fantasy-relevant player performance across seasons
- Identify the strongest drivers of fantasy production
- Build and compare predictive modeling approaches
- Explore player clustering and positional usage patterns
- Produce visual and analytical outputs suitable for portfolio presentation

## What This Project Includes

- Data aggregation and preparation from multiple CSV sources
- Exploratory analysis of player and team performance
- Feature engineering based on targets, carries, passing attempts, and efficiency metrics
- Linear regression for fantasy output prediction
- K-means clustering analysis for player grouping and pattern detection
- Visual analytics for performance trends and relationship exploration

## Technical Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- Jupyter Notebook

## Data Sources

The repository includes structured datasets stored in the DataSets directory, including:

- Fantasy player performance data
- Team defense statistics
- Multi-season fantasy scoring data

These files are used to combine historical player statistics with contextual defensive metrics to study the relationship between usage, efficiency, and fantasy value.

## Repository Structure

- DataSets/  
  Contains the cleaned and raw football datasets used in the analysis.

- Modeling/  
  Contains the analytical notebooks covering regression, clustering, and visualization.

- README.md  
  Project overview and usage guide.

## Modeling Approach

The project applies a combination of statistical and machine learning methods:

- Linear regression to estimate fantasy production using usage-based features
- Feature engineering around metrics such as targets per game, rushing attempts per game, passing attempts per game, and touchdown opportunities
- Player filtering based on minimum usage thresholds to reduce noise from low-volume performers
- K-means analysis to group players by similar performance profiles
- Visual diagnostics to interpret model behavior and feature relationships

## Key Analytical Focus Areas

- Fantasy output prediction for QB, RB, WR, and TE players
- Efficiency versus volume tradeoffs
- Correlation between team defense context and fantasy results
- Identification of high-value usage patterns
- Positional evaluation and segmentation of player archetypes

## Environment Setup

To run the notebooks locally, use a Python environment with the required dependencies installed.

1. Create and activate a virtual environment
2. Install dependencies
3. Launch Jupyter Notebook or JupyterLab

Example:

```bash
python -m venv .venv
source .venv/bin/activate
pip install pandas numpy matplotlib seaborn scikit-learn jupyterlab
jupyter lab
```

## Usage

Open the notebooks in the Modeling folder to reproduce the analysis:

- linear_regression.ipynb
- k_means.ipynb
- def_modeling.ipynb
- Plots_Visuals.ipynb

Each notebook is structured to progressively move from data preparation to exploratory analysis and modeling.

## Project Significance

This project demonstrates practical skills in:

- Data cleaning and feature engineering
- Exploratory data analysis
- Statistical modeling
- Machine learning application in sports analytics
- Data storytelling through visualization
- Translating raw sports data into interpretable business and analytical insights

These are valuable capabilities for roles in data analysis, analytics engineering, quantitative research, and data science.

## Future Enhancements

Potential next steps for expanding the project include:

- Incorporating additional seasons and more complete historical datasets
- Comparing multiple model families, including tree-based methods and ensemble approaches
- Building a reusable forecasting workflow for future player valuation
- Creating a dashboard for interactive fantasy analysis
- Expanding the dataset to include advanced efficiency and opportunity metrics

## Conclusion

The MDST Football Project brings together sports data, statistical modeling, and data visualization to provide a professional analytics workflow grounded in real-world NFL performance data. It is designed to highlight both analytical depth and practical decision-making ability in a way that is relevant to modern data-focused roles.

This repository reflects a strong foundation in Python-based analytics, statistical reasoning, and applied machine learning, making it suitable for technical discussion in interviews, portfolio reviews, and professional presentations.
