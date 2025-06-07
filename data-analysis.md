---
layout: default
title: Data Analysis Projects
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
          <h3>Diamond Price Prediction Analysis</h3>
          <div class="dataset-title">ggplot2 Diamonds Dataset</div>
          <div class="tools-used">Tools: R (dplyr, ggplot2, visdat)</div>
        </div>
      </div>
      <p class="project-objective"><strong>Objective:</strong> To explore the complex relationships between diamond attributes (cut, color, clarity, carat) and price, aiming to identify key price drivers and build a predictive understanding.</p>
      <ul>
        <li>Conducted thorough EDA, data cleaning (handling duplicates, zero values), and feature engineering (e.g., volume).</li>
        <li>Utilized statistical analysis and visualizations in R to uncover non-linear relationships and counter-intuitive patterns.</li>
        <li><strong>Key Insight/Result:</strong> Demonstrated that while carat weight is dominant, normalizing by price-per-volume reveals more intuitive quality-price correlations. [Your specific quantifiable finding here! e.g., Developed a regression model achieving an R-squared of X.].</li>
      </ul>
      <span class="project-details-indicator">View Analysis →</span>
    </div>
  </a>

  <a href="{{ '/projects/data-analysis/population-project/population_project.html' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-box-link">
    <div class="project-box">
      <span class="project-number">Project II</span>
      <div class="project-header">
        <img src="{{ '/assets/images/people.png' | relative_url }}" alt="Population Icon"> <!-- Ensure this image exists -->
        <div class="project-header-text">
          <h3>Global Population Dynamics Analysis</h3>
          <div class="dataset-title">World Bank Population Dataset</div>
          <div class="tools-used">Tools: R (tidyverse, gganimate)</div>
        </div>
      </div>
      <p class="project-objective"><strong>Objective:</strong> To analyze global demographic trends, including population distribution, growth rates, and density, identifying significant patterns and regional disparities over time.</p>
      <ul>
        <li>Processed and analyzed time-series population data for [Number] countries, focusing on data integrity and consistency.</li>
        <li>Created dynamic visualizations (e.g., using gganimate) to illustrate population shifts and growth trajectories.</li>
        <li><strong>Key Insight/Result:</strong> Uncovered significant disparities in population growth, highlighting [mention a specific finding, e.g., "X regions facing rapid urbanization challenges" or "quantified impact of Y factor on growth rates"].</li>
      </ul>
      <span class="project-details-indicator">View Visualizations →</span>
    </div>
  </a>

  <a href="{{ '/projects/data-analysis/bac-stock/bac-project.html' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-box-link">
    <div class="project-box">
      <span class="project-number">Project III</span>
      <div class="project-header">
        <img src="{{ '/assets/images/stock-market.png' | relative_url }}" alt="Stock Market Icon"> <!-- Ensure this image exists -->
        <div class="project-header-text">
          <h3>Bank of America (BAC) Stock Analysis</h3>
          <div class="dataset-title">Kaggle BAC Stock Dataset</div>
          <div class="tools-used">Tools: R (quantmod, GARCH modeling)</div>
        </div>
      </div>
      <p class="project-objective"><strong>Objective:</strong> To conduct a thorough time-series analysis of Bank of America's stock (BAC), focusing on volatility modeling and understanding financial market characteristics.</p>
      <ul>
        <li>Performed rigorous data validation and cleaning on extensive historical stock data.</li>
        <li>Applied GARCH models to analyze and forecast stock volatility, identifying periods of high persistence (β1 = 0.86).</li>
        <li><strong>Key Insight/Result:</strong> Successfully modeled volatility clusters, providing insights into risk assessment for BAC stock. [If a predictive element was involved, mention its outcome, e.g., "Forecasted volatility with X% accuracy over Y period."].</li>
      </ul>
      <span class="project-details-indicator">View Modeling →</span>
    </div>
  </a>

  <!-- Project IV - Example of a box not wrapped in an <a> tag, if it's just descriptive -->
  <div class="project-box no-link"> 
    <span class="project-number">Project IV</span>
    <div class="project-header"> 
       <img src="{{ '/assets/images/citybike_icon.png' | relative_url }}" alt="City Bike Icon"> <!-- Add an icon if you have one -->
       <div class="project-header-text">
          <h3>City Bikes Demand Forecasting</h3>
          <!-- <div class="dataset-title">Internal City Dataset</div> -->
          <div class="tools-used">Technologies: Python (Pandas, Scikit-learn), Excel</div>
        </div>
    </div>
    <p class="project-objective"><strong>Objective:</strong> To develop a predictive model for daily bike rental demand to help a city bike-sharing program optimize inventory and operations.</p>
    <ul>
        <li>Engineered time-series features from historical rental data and integrated external factors like weather and public holidays using Pandas.</li>
        <li>Developed and evaluated a Multiple Linear Regression (MLM) model in Scikit-learn, addressing challenges such as [mention a challenge, e.g., multicollinearity or seasonality].</li>
        <li><strong>Key Result:</strong> The MLM model achieved an R-squared of [e.g., 0.75] / a Mean Absolute Error (MAE) of [e.g., X bikes], providing actionable daily demand forecasts. [Optionally, mention how any user-friendly interface helped stakeholders].</li>
    </ul>
    <!-- No "View Details" indicator if it's not a link and the content is self-contained here -->
  </div>
</div>