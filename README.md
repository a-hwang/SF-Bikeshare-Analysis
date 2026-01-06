# San Francisco Bikeshare Analysis

**Author:** Albert Hwang (albertjh)
**Course:** CS145 Project 2

## Overview

This project analyzes San Francisco's bikeshare system to answer the question: **"How can San Francisco's transit systems best suit the needs of its residents?"**

The analysis uses Google BigQuery's public `san_francisco_bikeshare` dataset (~366MB) to explore usage patterns, identify popular routes, and build predictive models.

## Dataset

The dataset consists of four tables:

| Table | Description |
|-------|-------------|
| `bikeshare_regions` | Geographic regions of bikeshare service |
| `bikeshare_station_info` | Station details (location, capacity, installation date) |
| `bikeshare_station_status` | Real-time bike/dock availability |
| `bikeshare_trips` | Individual trip records (duration, start/end times, stations) |

**Note:** Data from 2017 onwards is used due to station ID inconsistencies in earlier records.

## Key Findings

### Temporal Usage Patterns

- **Weekdays vs Weekends:** Significantly higher usage on weekdays, suggesting bikeshare is primarily used for commuting
- **Peak Hours:** Early morning (5-10am) and early evening (5-8pm) see the highest activity
- **Seasonal Trends:** Usage varies by month with identifiable patterns

### Popular Routes & Stations

- **Top Stations:** San Francisco Caltrain and Ferry Building are the most frequented, reinforcing the commute hypothesis
- **Common Routes:** Analyzed station pairs to identify the most popular trips
- **Commute Corridors:** Morning and evening routes show distinct patterns, useful for transit planning

### Last Mile Analysis

Identified long-distance popular routes (>250 trips) that could benefit from dedicated transit lines, such as Berry St at 4th St to The Embarcadero at Sansome St.

## Predictive Models

### KNN Baseline (SQL)

Predicts likely end stations based on:
- Historical trip frequency
- Day type (weekday/weekend)
- Time interval (morning/evening)
- Geographic distance

**Results:**
- Naive baseline: 22.2% accuracy
- With day type: 27.4% accuracy (weekends)
- With time intervals: 42.2% accuracy (weekend early morning)


## Technologies Used

- Google BigQuery (SQL)
- BigQuery ML (Linear Regression)
- Python (pandas, numpy)
- Visualization: Plotly, Matplotlib, Seaborn

## Conclusions

1. Bikeshare serves primarily as a commuting solution, with peak usage during rush hours
2. Popular routes connect major transit hubs (Caltrain, Ferry Building)
3. Long-distance popular routes represent opportunities for new transit lines
4. Predictive models can help optimize bike redistribution and identify demand patterns

## Future Work

- Incorporate population data to identify underserved areas
- Expand analysis to address the last-mile problem more comprehensively
- Integrate with other transit data for multi-modal planning
