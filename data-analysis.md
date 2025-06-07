---
layout: default
title: Data Analysis Projects
---

# Data Analysis Projects

<p style="font-size: 1.05em; margin-bottom: 1.5rem;">
  This section showcases my ability to extract insights from diverse datasets using tools like R and Python. Each project demonstrates a systematic approach to data cleaning, analysis, visualization, and interpretation to answer key questions or solve specific problems. 
  <!-- Optional: For my most impactful projects, click to see a detailed breakdown of the process and outcomes. -->
</p>

<div class="project-container">
    
  <a href="{{ '/projects/data-analysis/diamond-project/diamond-project.html' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-box-link">
    <div class="project-box">
      <span class="project-number">Project I</span>
      <div class="project-header">
        <img src="{{ '/assets/images/diamond.png' | relative_url }}" alt="Diamond Icon" width="60" height="60">
        <div class="project-header-text">
          <h3 style="margin: 0 0 4px 0;">Diamond Price Prediction Analysis</h3>
          <div class="dataset-title">ggplot2 Diamonds Dataset</div>
          <div class="tools-used">Tools: R (dplyr, ggplot2, visdat)</div>
        </div>
      </div>
      <p><strong>Objective:</strong> To explore the complex relationships between diamond attributes (cut, color, clarity, carat) and price, aiming to identify key price drivers and build a predictive understanding.</p>
      <ul>
        <li>Conducted thorough EDA, data cleaning (handling duplicates, zero values), and feature engineering (e.g., volume).</li>
        <li>Utilized statistical analysis and visualizations in R to uncover non-linear relationships and counter-intuitive patterns (e.g., lower quality cuts sometimes fetching higher average prices due to carat weight).</li>
        <li><strong>Key Insight/Result:</strong> Demonstrated that while carat weight is dominant, normalizing by price-per-volume reveals more intuitive quality-price correlations. [Add a specific quantifiable finding or model performance metric if a predictive model was built, e.g., "Developed a regression model achieving an R-squared of X."].</li>
        <!-- Suggestion: <li class="project-link"><a href="/projects/detailed/diamond-analysis-deep-dive.html">View Detailed Analysis & Findings →</a></li> -->
      </ul>
    </div>
  </a>

  <a href="{{ '/projects/data-analysis/population-project/population_project.html' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-box-link">
    <div class="project-box">
      <span class="project-number">Project II</span>
      <div class="project-header">
        <img src="{{ '/assets/images/people.png' | relative_url }}" alt="Population Icon" width="60" height="60">
        <div class="project-header-text">
          <h3 style="margin: 0 0 4px 0;">Global Population Dynamics Analysis</h3>
          <div class="dataset-title">World Bank Population Dataset</div>
          <div class="tools-used">Tools: R (tidyverse, gganimate)</div>
        </div>
      </div>
      <p><strong>Objective:</strong> To analyze global demographic trends, including population distribution, growth rates, and density, identifying significant patterns and regional disparities over time.</p>
      <ul>
        <li>Processed and analyzed time-series population data for [Number] countries, focusing on data integrity and consistency.</li>
        <li>Created dynamic visualizations (e.g., using gganimate) to illustrate population shifts and growth trajectories across continents and individual nations.</li>
        <li><strong>Key Insight/Result:</strong> Uncovered significant disparities in population growth sustainability, highlighting [mention a specific finding, e.g., "X regions facing rapid urbanization challenges" or "quantified the impact of Y factor on growth rates"].</li>
        <!-- Suggestion: <li class="project-link"><a href="/projects/detailed/population-dynamics-deep-dive.html">View Detailed Analysis & Visualizations →</a></li> -->
      </ul>
    </div>
  </a>

  <a href="{{ '/projects/data-analysis/bac-stock/bac-project.html' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-box-link">
    <div class="project-box">
      <span class="project-number">Project III</span>
      <div class="project-header">
        <img src="{{ '/assets/images/stock-market.png' | relative_url }}" alt="Stock Market Icon" width="60" height="60">
        <div class="project-header-text">
          <h3 style="margin: 0 0 4px 0;">Bank of America (BAC) Stock Analysis</h3>
          <div class="dataset-title">Kaggle BAC Stock Dataset</div>
          <div class="tools-used">Tools: R (quantmod, GARCH modeling)</div>
        </div>
      </div>
      <p><strong>Objective:</strong> To conduct a thorough time-series analysis of Bank of America's stock (BAC) from 1978-2025, focusing on volatility modeling and understanding financial market characteristics.</p>
      <ul>
        <li>Performed rigorous data validation and cleaning on extensive historical stock data.</li>
        <li>Applied GARCH models to analyze and forecast stock volatility, identifying periods of high persistence (β1 = 0.86).</li>
        <li><strong>Key Insight/Result:</strong> Successfully modeled volatility clusters, providing insights into risk assessment for BAC stock. [If a predictive element was involved, mention its outcome, e.g., "Forecasted volatility with X% accuracy over Y period."]. Highlighted the importance of robust data validation in financial time series.</li>
        <!-- Suggestion: <li class="project-link"><a href="/projects/detailed/bac-stock-analysis-deep-dive.html">View Detailed Modeling & Results →</a></li> -->
      </ul>
    </div>
  </a>

  <div class="project-box"> <!-- Project IV - Assuming no direct link page for this one -->
    <span class="project-number">Project IV</span>
    <h3>City Bikes Demand Forecasting</h3>
    <p><strong>Technologies:</strong> Python (Pandas, Scikit-learn), Excel</p>
    <p><strong>Objective:</strong> To develop a predictive model for daily bike rental demand to help a city bike-sharing program optimize inventory and operations.</p>
    <ul>
        <li>Engineered time-series features from historical rental data and integrated external factors like weather and public holidays using Pandas.</li>
        <li>Developed and evaluated a Multiple Linear Regression (MLM) model in Scikit-learn, addressing challenges such as [mention a challenge, e.g., multicollinearity or seasonality].</li>
        <li><strong>Key Result:</strong> The MLM model achieved an R-squared of [e.g., 0.75] / a Mean Absolute Error (MAE) of [e.g., X bikes], providing actionable daily demand forecasts. [Optionally, mention how the user-friendly interface helped stakeholders].</li>
        <!-- Suggestion: If this project is strong, consider creating a detailed page and linking it:
        <li class="project-link"><a href="/projects/detailed/citybikes-forecasting-deep-dive.html">View Model Details & Impact →</a></li> -->
    </ul>
  </div>

</div>