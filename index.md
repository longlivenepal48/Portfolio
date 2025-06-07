---
layout: default
title: Home
---

# Welcome to My Professional Portfolio

<p class="page-intro-paragraph"> {/* Using a class for specific styling if needed, otherwise just <p> is fine for global justify */}
  I'm a strategic financial professional with expertise in financial analysis, audit management, and data analytics. My background combines traditional accounting with modern data analysis techniques to uncover insights and drive business value.
</p>

<!-- "Portfolio Sections Overview" has been REMOVED -->

## Featured Sections
<p class="section-intro">Click below to explore different facets of my work:</p>
<div class="featured-sections-container">
    <a href="{{ '/introduction.html' | relative_url }}" class="featured-section">
        <h3><i class="fas fa-user-tie"></i> About Me</h3>
        Okay, `_layouts/default.html` and the new, full `assets/css/style.css` are set.

---

**File 3 of 7: `index.md` (Removing "Portfolio Sections Overview")**

As requested, we will remove the "Portfolio Sections Overview" block from the homepage. The page will consist of the main welcome, the "Featured Sections" cards, and "Professional Highlights." All paragraphs and list items will be justified by the global CSS.

*   **Location:** `portfolio/index.md`
*   **Action:** Replace the entire content of your `index.md` file with the following code.

```markdown
---
layout: default
title: Home
description: "Welcome to Anup Acharya's Data Science Portfolio. Explore projects in data analysis, big data, and Kaggle competition entries, demonstrating expertise in finance and analytics."
---

# Welcome to My Professional Portfolio

<p class="section-intro">
  I'm a strategic financial professional with expertise in financial analysis, audit management, and data analytics. My background combines traditional accounting with modern data analysis techniques to uncover insights and drive business value.
</<p>Discover my professional background, extensive experience, and qualifications as a Chartered Accountant & CPA, with a strong focus on data-driven financial analysis.</p>
    </a>

    <a href="{{ '/data-analysis.html' | relative_url }}" class="featured-section">
        <h3><i class="fas fa-chart-line"></i> Data Analysis</h3>
        <p>Explore projects showcasing my analytical skills using Excel, SQL, R, and Python to derive actionable financial and operational insights.</p>
    </a>

    <a href="{{ '/big-data.html' | relative_url }}" class="featured-section">
        <h3><i class="fas fa-server"></i> Big Data</h3>
        <p>Review large-scale data implementations for financial consolidation, expense optimization, and advanced business intelligence solutions.</p>
    </a>

    <a href="{{ '/kaggle.html' | relative_url }}" class="featured-section">
        <h3><i class="fab fa-kaggle"></i> Kaggle Projects</h3>
        <p>See my data science competition entries, methodologies, and results, particularly focusing on financial prediction and complex analysis.</p>
    </a>
</div>

## Professional Highlights
<ul>
    <li><strong>Strategic Financial Management:</strong> Expertise in GAAP and NFRS compliant financial statement preparation, in-depth analysis, and forecasting.</li>
    <li><strong>Audit & Compliance Excellence:</strong> Strong background in comprehensive audit management, rigorous risk assessment, and ensuring regulatory compliance.</li>
    <li><strong>Advanced Data Analytics:</strong> Google Certified Data Analyst with proficient skills in SQL, R, Python, and impactful data visualization techniques.</li>
    <li><strong>Actionable Business Intelligence:</strong> Proven experience in creating dynamic dashboards and insightful reports that drive strategic decision-making.</li>
p>

<!-- "Portfolio Sections Overview" has been REMOVED -->

## Featured Sections
<p class="section-intro">Click below to explore different facets of my work:</p>
<div class="featured-sections-container">
    <a href="{{ '/introduction.html' | relative_url }}" class="featured-section">
        <h3><i class="fas fa-user-tie"></i> About Me</h3>
        <p>Discover my professional background, extensive experience, and qualifications as a Chartered Accountant & CPA, with a strong focus on data-driven financial analysis.</p>
    </a>

    <a href="{{ '/data-analysis.html' | relative_url }}" class="featured-section">
        <h3><i class="fas fa-chart-line"></i> Data Analysis</h3>
        <p>Explore projects showcasing my analytical skills using Excel, SQL, R, and Python to derive actionable financial and operational insights.</p>
    </a>

    <a href="{{ '/big-data.html' | relative_url }}" class="featured-section">
        <h3><i class="fas fa-server"></i> Big Data</h3>
        <p>Review large-scale data implementations for financial consolidation, expense optimization, and advanced business intelligence solutions.</p>
    </a>

    <a href="{{ '/kaggle.html' | relative_url }}" class="featured-section">
        <h3><i class="fab fa-kaggle"></i> Kaggle Projects</h3>
        <p>See my data science competition entries, methodologies, and results, particularly focusing on financial prediction and complex analysis.</p>
    </a>
</div>

## Professional Highlights
<ul>
    <li><strong>Strategic Financial Management:</strong> Expertise in GAAP and NFRS compliant financial statement preparation, in-depth analysis, and forecasting.</li>
    <li><strong>Audit & Compliance Excellence:</strong> Strong background in</ul>