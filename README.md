# Mobile Phone Activity Data Analysis - Assignment 1

## Title: Analysis of Milan's Mobile Phone Activity Patterns Using CDR Data

### Assignment Goal
The primary objective of this assignment is to analyze and extract meaningful insights from Call Detail Records (CDR) data collected in Milan, Italy over a one-week period. Through comprehensive data processing, cleaning, and statistical analysis, we aim to understand communication patterns, spatial distributions, and temporal variations in mobile phone usage including SMS, calls, and internet activity.

### Dataset Overview

**Source:** Kaggle - Mobile Phone Activity Dataset (https://www.kaggle.com/datasets/marcodena/mobile-phone-activity)

**Time Period:** One week (November 1-7, 2013)

**Data Collection Method:** Radio Base Station (RBS) recordings of telecommunication interactions

**Spatial Aggregation:** 10,000 grid cells (235×235 meters each) covering the city of Milan and the Province of Trentino (Italy)

**Temporal Aggregation:** 60-minute intervals

**Key Activities Tracked:**
- Received SMS
- Sent SMS
- Incoming calls
- Outgoing calls
- Internet activity (generated for connections lasting >15 min or transferring >5 MB)

**Files Used for This Assignment:**
1. `sms-call-internet-mi-2013-11-02.csv`
2. `sms-call-internet-mi-2013-11-04.csv`
3. `sms-call-internet-mi-2013-11-06.csv`

### Analytical Approach

#### 1. **Data Loading and Merging Strategy**
- Loaded three specified CSV files representing different days of activity
- Implemented systematic merging to create a unified dataset
- Preserved data integrity by maintaining original structure while combining sources

#### 2. **Data Preprocessing and Cleaning**
- **Date/Time Processing:** Extracted date and time components from the datetime column to enable temporal analysis
- **Missing Value Handling:** Implemented mean imputation for NaN values in activity columns (smsin, smsout, callin, callout, internet)
- **Aggregate Features:** Created calculated columns:
  - `total_sms`: Sum of smsin and smsout
  - `total_calls`: Sum of callin and callout
  - `total_internet`: Direct mapping from internet column
- **Country Code Classification:** Implemented logic to distinguish domestic (Italy = countrycode 39) vs. international communications

#### 3. **Statistical Analysis Framework**
- **Descriptive Statistics:** Calculated mean, median, standard deviation, min, and max values for key metrics
- **Temporal Analysis:** Analyzed activity patterns by hour, identifying peak and low usage periods
- **Comparative Analysis:** Used numpy for statistical comparisons between different conditions (domestic vs. international, SMS vs. calls)
- **Correlation Analysis:** Examined relationships between different activity types at the grid level

#### 4. **Key Analysis Components**

**Missing Value Management:**
- Identified columns with highest frequency of missing values
- Applied column-wise mean imputation to maintain data integrity
- Tracked the number of modified records for transparency

**Temporal Pattern Analysis:**
- Calculated activity distribution across 24-hour cycles
- Identified peak and off-peak hours
- Compared daytime (6am-8pm) vs. nighttime (8pm-6am) activity patterns

**Geospatial Analysis:**
- Analyzed distribution across 10,000 unique grid cells
- Examined activity concentration in different geographical areas

**International vs. Domestic Communications:**
- Calculated percentage distributions for calls and SMS
- Analyzed temporal patterns for international communications
- Compared incoming vs. outgoing ratios for international calls

### Key Findings and Insights

#### **Data Volume and Structure:**
- The combined dataset contains 6564031 million records across the three days
- 10,000 unique grid cells represent the spatial coverage of Milan
- Multiple country codes indicate diverse international communication patterns

#### **Temporal Patterns:**
- Identified distinct peak hours for different activity types
- Nighttime activity shows different characteristics than daytime usage
- Internet activity displays unique temporal patterns compared to voice/SMS

#### **Communication Behaviors:**
- International communications dominate the dataset
- Domestic calls show distinct temporal distributions
- There os 1.67 ratio of incoming vs. outgoing communications for  international calls

#### **Correlation Insights:**
- SMS and call volumes show [specific correlation pattern] at grid level

### Technical Implementation Details

**Libraries Used:**
- `pandas` for data manipulation and analysis
- `numpy` for statistical computations
- `matplotlib` for data visualization
- Built-in Python libraries for file operations



### Challenges and Solutions

**Challenge 1:** Large file sizes requiring efficient memory management
**Solution:** Implemented chunked processing where necessary and optimized data types

**Challenge 2:** Inconsistent missing value patterns across different days
**Solution:** Applied systematic mean imputation with careful tracking of modifications

**Challenge 3:** Temporal analysis across multiple time dimensions
**Solution:** Created comprehensive datetime features enabling multi-faceted time analysis



### Conclusion

This analysis provides a comprehensive view of mobile communication patterns in he city of Milan and the Province of Trentino (Italy), revealing insights into temporal behaviors, spatial distributions, and communication preferences. The approach demonstrates robust data handling techniques and meaningful statistical analysis that can be extended to similar datasets in other urban contexts.



