---
layout: default
title: Data Analysis Projects
# description: "A collection of Anup Acharya's data analysis projects demonstrating skills in R, Python, SQL, and data visualization for deriving insights."
---

# Data Analysis Projects

<p class="section-intro">
  This section showcases my ability to extract insights from diverse datasets using tools like R and Python. Each project demonstrates a systematic approach to data cleaning, analysis, visualization, and interpretation to answer key questions or solve specific problems.
</p>

<div class="project-container">
    
  <a href="{{ '/projects/data-analysis/diamond-project/diamond-project.html' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-box-link">
    <div class="project-box">
      <span class="project-number">Project I</span>
      <div class="project-header">
        <img src="{{ '/assets/images/diamond.png' | relative_url }}" alt="Diamond Icon">
        <div class="project-header-text">
          <h3>Diamond Price Analysis</h3>
          <div class="dataset-title">ggplot2 Diamonds Dataset</div>
          <div class="tools-used">Tools: R (dplyr, ggplot2)</div>
        </div>
      </div>
      <p class="project-objective"><strong>Objective:</strong> To explore relationships between diamond attributes and price, identifying key drivers and patterns for predictive understanding.</p>
      <p class="project-key-result"><strong>Key Finding:</strong> Carat weight is dominant, but price-per-volume normalizes quality-price trends. [Add brief model metric if applicable, e.g., R-squared: 0.XX].</p>
      <span class="project-details-indicator">View Full Analysis →</span>
    </div>
  </a>

  <a href="{{ '/projects/data-analysis/population-project/population_project.html' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-box-link">
    <div class="project-box">
      <span class="project-number">Project II</span>
      <div class="project-header">
        <img src="{{ '/assets/images/people.png' | relative_url }}" alt="Population Icon">
        <div class="project-header-text">
          <h3>Global Population Dynamics</h3>
          <div class="dataset-title">World Bank Population Data</div>
          <div class="tools-used">Tools: R (tidyverse, gganimate)</div>
        </div>
      </div>
      <p class="project-objective"><strong>Objective:</strong> To analyze global demographic trends (distribution, growth, density) and identify significant regional patterns over time.</p>
      <p class="project-key-result"><strong>Key Insight:</strong> Uncovered significant disparities in growth sustainability, highlighting [mention a brief, specific finding, e.g., rapid urbanization in X regions].</p>
      <span class="project-details-indicator">View Visualizations →</span>
    </div>
  </a>

  <a href="{{ '/projects/data-analysis/bac-stock/bac-project.html' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-box-link">
    <div class="project-box">
      <span class="project-number">Project III</span>
      <div class="project-header">
        <img src="{{ '/assets/images/stock-market.png' | relative_url }}" alt="Stock Market Icon">
        <div class="project-header-text">
          <h3>BAC Stock Volatility Analysis</h3>
          <div class="dataset-title">Kaggle BAC Stock Dataset</div>
          <div class="tools-used">Tools: R (quantmod, GARCH)</div>
        </div>
      </div>
      <p class="project-objective"><strong>Objective:</strong> To conduct time-series analysis of Bank of America's stock, focusing on volatility modeling and financial market characteristics.</p>
      <p class="project-key-result"><strong>Key Outcome:</strong> Successfully modeled volatility clusters (GARCH β1=0.86), providing insights for risk assessment. Emphasized data validation importance.</p>
      <span class="project-details-indicator">View Modeling Details →</span>
    </div>
  </a>

  <!-- Project IV - Card not wrapped in a link -->
  <div class="project-box no-link"> 
    <span class="project-number">Project IV</span>
    <div class="project-header"> 
       <img src="{{ '/assets/images/citybike_icon.png' | relative_url }}" alt="City Bike Icon"> <!-- ADD YOUR ICON IMAGE and ensure it exists -->
       <div class="project-header-text">
          <h3>City Bikes Demand Forecasting</h3>
          <div class="tools-used">Tech: Python (Pandas, Scikit-learn), Excel</div>
        </div>
    </div>
    <p class="project-objective"><strong>Objective:</strong> To develop a predictive model for daily bike rental demand to help optimize inventory and operations for a city bike-sharing program.</p>
    <p class="project-key-result"><strong>Key Result:</strong> MLM model achieved R-squared of [e.g., 0.75], providing actionable daily demand forecasts. [Add specific MAE if available].</p>
  </div>

</div>