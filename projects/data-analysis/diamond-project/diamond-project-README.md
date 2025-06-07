---
title: "Diamond Dataset Analysis"
author: "CA. Anup Acharya"
date: 2024-03-15
output:
  html_document:
    toc: true
    toc_float: true
    code_folding: show
    theme: united
    highlight: tango
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE, warning = FALSE, message = FALSE, fig.width = 10, fig.height = 6)
```

## Introduction

This project analyzes the diamonds dataset to understand the relationships between various diamond attributes and their prices. We will explore how factors such as cut, color, clarity, and carat weight influence diamond prices and identify patterns in the data.

## Loading Required Libraries

First, we load all the necessary libraries for our analysis:

```{r libraries}
# Loading required libraries
library(tidyverse)
library(readr)
library(dplyr)
library(visdat)
library(ggradar)
library(treemap)
```

## Data Loading and Initial Exploration

We'll start by loading the built-in diamonds dataset from the ggplot2 package:

```{r load_data}
# Loading datasets diamonds for initial preview
data("diamonds")

# Viewing & Analyzing Dataset
glimpse(diamonds) # Summary of dataset
str(diamonds) # Data structure
sapply(diamonds, class) # Data types of each column
```

## Data Cleaning and Preparation

### Column Renaming

Based on the initial exploration, we need to make a few adjustments to the column names for clarity:

```{r rename_columns}
# Making a copy of the original dataset
diamond_original <- diamonds

# Correcting column names for better understanding
diamond_original <- diamond_original %>%
  rename(
    depth_percent = depth,
    length = x,
    width = y, 
    depth = z
  )
```

**Rationale:** The original column names (x, y, z, depth) were ambiguous. Renaming them to length, width, depth, and depth_percent makes their meaning clearer and facilitates better understanding of the data.

### Missing Value Analysis

Let's check for missing values in the dataset:

```{r missing_values}
# Finding missing information using visdat package
vis_miss(diamond_original)
```

**Finding:** There are no missing values in the dataset, which is excellent for our analysis as we don't need to handle missing values.

### Duplicate Row Detection and Removal

```{r duplicates}
# Finding duplicate rows
duplicate_rows <- diamond_original[duplicated(diamond_original), ]
print(paste("Number of duplicate rows:", nrow(duplicate_rows)))

# Removing duplicate rows
diamond_complete <- diamond_original %>% 
  distinct()

# Checking if duplicates are removed
print(paste("Original rows:", nrow(diamond_original)))
print(paste("After removing duplicates:", nrow(diamond_complete)))
```

**Finding:** The dataset contains some duplicate entries that we need to remove to ensure our analysis isn't biased by counting the same diamond multiple times.

### Handling Zero Values

Let's identify if any columns have zero values, which could indicate data entry errors:

```{r zero_values}
# Identifying if any column has field value 0 or very small values
lowvalue_length <- subset(diamond_complete, subset = !(length > 0.001))
lowvalue_width <- subset(diamond_complete, subset = !(width > 0.001))
lowvalue_depth <- subset(diamond_complete, subset = !(depth > 0.001))

# Displaying count of problematic rows
print(paste("Rows with negligible length:", nrow(lowvalue_length)))
print(paste("Rows with negligible width:", nrow(lowvalue_width)))
print(paste("Rows with negligible depth:", nrow(lowvalue_depth)))

# Removing rows with any dimensional value = 0 or very small
diamond_cleaned <- diamond_complete %>%
  filter(length > 0.001, width > 0.001, depth > 0.001)

# Checking if zero values are removed
print(paste("Before cleaning:", nrow(diamond_complete)))
print(paste("After cleaning:", nrow(diamond_cleaned)))
```

**Rationale:** Zero or negligible values for dimensions (length, width, depth) are not realistic for diamonds and would skew our volume calculations. We removed these rows as they likely represent data entry errors.

## Summary Statistics

Let's look at the summary statistics of our cleaned dataset:

```{r summary}
# Summary of the cleaned dataset
summary(diamond_cleaned)
```

## Price Analysis by Diamond Attributes

### Diamond Cut Analysis

```{r cut_analysis}
# Mean values grouped by cut
mean_cut_wide <- diamond_cleaned %>% 
  group_by(cut) %>% 
  summarise(
    mean_price = round(mean(price), 2),
    mean_table = round(mean(table), 2),
    mean_length = round(mean(length), 2),
    mean_width = round(mean(width), 2),
    mean_depth = round(mean(depth), 2),
    mean_depth_percent = round(mean(depth_percent), 2),
    mean_volume = round(mean(length * width * depth), 2),
    mean_price_per_volume = round(mean(price/(length * width * depth)), 2)
  )

# Display the results
mean_cut_wide

# Plot mean price by cut
ggplot(mean_cut_wide, aes(x = cut, y = mean_price, fill = cut)) +
  geom_col() +
  geom_text(aes(label = mean_price), vjust = -0.5) +
  labs(
    title = "Mean Price vs Diamond Cut",
    x = "Diamond Cut",
    y = "Mean Price (USD)"
  ) +
  theme_minimal()
```

**Finding:** Interestingly, "Premium" cut diamonds have a higher average price than "Ideal" cut diamonds. This suggests that factors other than cut quality (like carat weight) significantly influence price.

### Diamond Color Analysis

```{r color_analysis}
# Mean values grouped by color
mean_color_wide <- diamond_cleaned %>% 
  group_by(color) %>% 
  summarise(
    mean_price = round(mean(price), 2),
    mean_table = round(mean(table), 2),
    mean_length = round(mean(length), 2),
    mean_width = round(mean(width), 2),
    mean_depth = round(mean(depth), 2),
    mean_depth_percent = round(mean(depth_percent), 2),
    mean_volume = round(mean(length * width * depth), 2),
    mean_price_per_volume = round(mean(price/(length * width * depth)), 2)
  )

# Display the results
mean_color_wide

# Plot mean price by color
ggplot(mean_color_wide, aes(x = color, y = mean_price, fill = color)) +
  geom_col() +
  geom_text(aes(label = mean_price), vjust = -0.5) +
  labs(
    title = "Mean Price vs Diamond Color",
    x = "Diamond Color",
    y = "Mean Price (USD)"
  ) +
  theme_minimal()

# Plot mean price per volume by color
ggplot(mean_color_wide, aes(x = color, y = mean_price_per_volume, fill = color)) +
  geom_col() +
  geom_text(aes(label = mean_price_per_volume), vjust = -0.5) +
  labs(
    title = "Mean Price per Volume vs Diamond Color",
    x = "Diamond Color",
    y = "Mean Price per Volume (USD/mm³)"
  ) +
  theme_minimal()
```

**Finding:** The analysis shows that color J (which is more yellowish) actually has a higher average price than color D (which is colorless and should be more valuable). This contradicts diamond grading standards where D color should be most valuable. This unexpected result suggests that other factors like carat weight are having a stronger influence on the price than color alone.

### Diamond Clarity Analysis

```{r clarity_analysis}
# Mean values grouped by clarity
mean_clarity_wide <- diamond_cleaned %>% 
  group_by(clarity) %>% 
  summarise(
    mean_price = round(mean(price), 2),
    mean_table = round(mean(table), 2),
    mean_length = round(mean(length), 2),
    mean_width = round(mean(width), 2),
    mean_depth = round(mean(depth), 2),
    mean_depth_percent = round(mean(depth_percent), 2),
    mean_volume = round(mean(length * width * depth), 2),
    mean_price_per_volume = round(mean(price/(length * width * depth)), 2)
  )

# Display the results
mean_clarity_wide

# Sorting clarity levels in proper order (worst to best)
mean_clarity_wide$clarity <- factor(mean_clarity_wide$clarity, 
                                    levels = c("I1", "SI2", "SI1", "VS2", "VS1", "VVS2", "VVS1", "IF"))
mean_clarity_wide_sorted <- mean_clarity_wide %>%
  arrange(clarity)

# Plot mean price by clarity
ggplot(mean_clarity_wide, aes(x = clarity, y = mean_price, fill = clarity)) +
  geom_col() +
  geom_text(aes(label = mean_price), vjust = -0.5) +
  labs(
    title = "Mean Price vs Diamond Clarity (Size of Diamond Ignored)",
    x = "Diamond Clarity",
    y = "Mean Price (USD)"
  ) +
  theme_minimal()

# Plot mean price per volume by clarity in sorted order
ggplot(mean_clarity_wide_sorted, aes(x = clarity, y = mean_price_per_volume, fill = clarity)) +
  geom_col() +
  geom_text(aes(label = mean_price_per_volume), vjust = -0.5) +
  labs(
    title = "Mean Price per Volume vs Diamond Clarity",
    x = "Diamond Clarity",
    y = "Mean Price per Volume (USD/mm³)"
  ) +
  theme_minimal()

# Line chart for clarity trend
ggplot(mean_clarity_wide_sorted, aes(x = clarity, y = mean_price_per_volume, group = 1, label = round(mean_price_per_volume))) +
  geom_line() +
  geom_point(size = 5) +
  geom_text(vjust = -1.5) +
  labs(
    title = "Mean Price per Volume vs Diamond Clarity",
    x = "Diamond Clarity",
    y = "Mean Price per Volume (USD/mm³)"
  ) +
  theme_minimal()
```

**Finding:** When analyzing price per volume (which helps normalize by size), we see a more expected trend: price per volume generally increases with better clarity. However, there is an unexpected dip for VVS1 clarity, which might be due to the interplay of other factors like cut and color. When we simply look at average price without considering volume, clarity doesn't show the expected pattern - this demonstrates the importance of normalizing by size.

## Carat Analysis

```{r carat_analysis}
# Create carat and clarity combined analysis
mean_carat_wide <- diamond_cleaned %>%
  mutate(carat_clarity = paste(carat, clarity, sep = "_")) %>%
  group_by(carat, clarity, carat_clarity) %>% 
  summarise(
    mean_price = round(mean(price), 2),
    mean_table = round(mean(table), 2),
    mean_length = round(mean(length), 2),
    mean_width = round(mean(width), 2),
    mean_depth = round(mean(depth), 2),
    mean_depth_percent = round(mean(depth_percent), 2),
    mean_volume = round(mean(length * width * depth), 2),
    mean_price_per_volume = round(mean(price/(length * width * depth)), 2),
    .groups = 'drop'
  )

# Relation of Carat with Volume
ggplot(mean_carat_wide, aes(x = carat, y = mean_volume, group = 1)) +
  geom_line() +
  geom_point(size = 0.5) +
  labs(
    title = "Diamond Carat vs Mean Volume",
    x = "Diamond Carat",
    y = "Mean Volume (mm³)"
  ) +
  theme_minimal()

# Relation of Carat with Price by clarity
ggplot(mean_carat_wide, aes(x = carat, y = mean_price, color = clarity)) +
  geom_point() +
  labs(
    title = "Mean Price vs Carat (Colored by Clarity)",
    x = "Diamond Carat",
    y = "Mean Price (USD)"
  ) +
  theme_minimal()

# With regression lines
ggplot(mean_carat_wide, aes(x = carat, y = mean_price, color = clarity)) +
  geom_point() +
  geom_smooth(method = "lm") +
  labs(
    title = "Mean Price vs Carat with Regression Line by Clarity",
    x = "Diamond Carat",
    y = "Mean Price (USD)"
  ) +
  theme_minimal()

# Using log scale
ggplot(mean_carat_wide, aes(x = carat, y = mean_price, color = clarity)) +
  geom_point() +
  scale_y_log10() +
  labs(
    title = "Mean Price (Log Scale) vs Carat",
    x = "Diamond Carat",
    y = "Mean Price (USD) - Log Scale"
  ) +
  theme_minimal()

# Distribution of carat sizes
ggplot(diamond_cleaned, aes(x = carat)) +
  geom_histogram(bins = 40, color = "black", fill = "steelblue") +
  labs(
    title = "Distribution of Diamond Carat Sizes",
    x = "Carat Size",
    y = "Number of Diamonds"
  ) +
  theme_minimal()
```

**Finding:** The relationship between carat and price is strongly positive but non-linear. Price increases more rapidly as carat increases. When plotted on a log scale, the relationship appears more linear, suggesting an exponential relationship between carat and price. The regression lines for different clarity ratings show that higher clarity diamonds command higher prices across all carat weights.

The histogram shows that diamonds around 0.3-0.4 carats and 0.7-0.8 carats are most common in the dataset, likely due to market preferences for these "magic sizes" (e.g., 1/3 carat, 3/4 carat).

## Box Plot Analysis

```{r boxplot_analysis}
# Sort clarity levels
diamond_cleaned$clarity <- factor(diamond_cleaned$clarity, 
                                  levels = c("I1", "SI2", "SI1", "VS2", "VS1", "VVS2", "VVS1", "IF"))

# Box plot for clarity
ggplot(diamond_cleaned, aes(x = clarity, y = price, fill = clarity)) +
  geom_boxplot() +
  labs(
    title = "Price Distribution by Clarity Rating",
    x = "Clarity Rating",
    y = "Price (USD)"
  ) +
  theme_minimal()

# Sort cut levels
diamond_cleaned$cut <- factor(diamond_cleaned$cut, 
                              levels = c("Fair", "Good", "Very Good", "Premium", "Ideal"))

# Box plot for cut
ggplot(diamond_cleaned, aes(x = cut, y = price, fill = cut)) +
  geom_boxplot() +
  labs(
    title = "Price Distribution by Cut Type",
    x = "Cut Type",
    y = "Price (USD)"
  ) +
  theme_minimal()

# Sort color levels
diamond_cleaned$color <- factor(diamond_cleaned$color, 
                                levels = c("D", "E", "F", "G", "H", "I", "J"))

# Box plot for color
ggplot(diamond_cleaned, aes(x = color, y = price, fill = color)) +
  geom_boxplot() +
  labs(
    title = "Price Distribution by Color",
    x = "Diamond Color",
    y = "Price (USD)"
  ) +
  theme_minimal()
```

**Finding:** 
1. **Clarity Box Plot**: Shows considerable overlap in price distributions across clarity grades, with higher median prices for IF and VVS1 diamonds. However, the highest-priced diamonds are not necessarily the highest clarity, suggesting other factors (likely carat) strongly influence maximum prices.

2. **Cut Box Plot**: Reveals that Premium and Very Good cuts have higher median prices than Ideal cuts, which contradicts expectations. This suggests that consumers may not be paying primarily for cut quality, or that larger diamonds (which cost more) are not always ideal cut.

3. **Color Box Plot**: Shows surprisingly higher median prices for lower color grades (H, I, J) compared to better colors (D, E). This counter-intuitive result suggests that in this dataset, lower color grade diamonds tend to be larger (higher carat), again demonstrating that carat weight has a stronger influence on price than color.

## Distribution Analysis

```{r distribution_analysis}
# Create aggregate dataset for treemap and heatmap
diamond_aggregate <- diamond_cleaned %>% 
  group_by(cut, color, clarity) %>% 
  summarise(count = n(),
            .groups = 'drop')

# Treemap visualization
treemap(diamond_aggregate,
        index = c("cut", "color", "clarity"),
        vSize = "count",
        title = "Number of Diamonds by Cut, Color and Clarity"
)

# Heatmap for clarity and color
ggplot(diamond_aggregate, aes(x = clarity, y = color, fill = count)) +
  geom_tile(color = "grey") +
  scale_fill_gradient(low = "white", high = "red") +
  labs(
    title = "Heat Map - Number of Diamonds by Clarity and Color",
    x = "Clarity",
    y = "Color"
  ) +
  theme_minimal()
```

**Finding:** 
1. **Treemap Analysis**: Shows that Ideal cut diamonds are the most common in the dataset, followed by Premium and Very Good cuts. Within these categories, certain color-clarity combinations are more frequent than others.

2. **Heatmap Analysis**: Reveals that SI1 and VS2 clarity diamonds in colors G and H are the most common in the dataset. The highest concentration (red areas) shows the most frequently occurring combinations, giving insight into market preferences or supply patterns.

## Correlation Analysis

```{r correlation_analysis}
# Scatter plot of carat with price by cut
ggplot(diamond_cleaned, aes(x = carat, y = price, color = cut)) +
  geom_point(alpha = 0.5) +
  labs(
    title = "Relationship Between Carat and Price by Cut",
    x = "Carat Size",
    y = "Price (USD)"
  ) +
  theme_minimal()

# Scatter plot of carat with price by color
ggplot(diamond_cleaned, aes(x = carat, y = price, color = color)) +
  geom_point(alpha = 0.5) +
  labs(
    title = "Relationship Between Carat and Price by Color",
    x = "Carat Size",
    y = "Price (USD)"
  ) +
  theme_minimal()
```

**Finding:** The scatter plots confirm that carat weight is the strongest determinant of diamond price. The relationship is non-linear, with price increasing more rapidly as carat increases. While better cuts and colors generally command higher prices within the same carat range, the effect is less pronounced compared to the impact of carat weight.

## Conclusion

Our analysis of the diamond dataset reveals several key insights:

1. **Carat Weight Dominance**: Carat weight is by far the strongest determinant of diamond price, often overshadowing the effects of other quality factors like cut, color, and clarity.

2. **Price Per Volume**: When normalizing for size by calculating price per volume, the expected relationships between quality factors and price become more apparent. Better clarity generally commands higher prices per unit volume.

3. **Counter-intuitive Findings**: Without controlling for size, we observed some counter-intuitive results, such as lower quality diamonds (in terms of color or cut) sometimes having higher average prices because they tend to be larger.

4. **Market Preferences**: The distribution analysis shows certain combinations of cut, color, and clarity are much more common in the market, potentially reflecting consumer preferences or supply patterns.

5. **Non-linear Pricing**: The relationship between carat and price is non-linear, with an exponential price increase as carat weight increases.
