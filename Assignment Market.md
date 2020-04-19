## Project Definition and Data Choice

This data mining project will be based on an assessment if we can predict infection and death rates of the Influenza virus (type B) alongside patterns in human behaviour, principally in relation to human mobility.

As humanity has advanced technologically, Are there features in the data showing a correlation between changes in common population mobility (introduction of mass and personal transport), that have changed the average weekly distance covered by individuals over the course of the last 20 years, to the basic reproduction rate (R0) of Human Influenza Type B

### Influenza Data Sources
The data choice for influeza patterns is primarily from the WHO FluNet/FluId datasets which are compiled by individual countries and aggregated by geographical region into FluMart. A preferred target for the data is to see if the R0 (R-Naught) of a particular strain of Influenza, where the current rate is mean R0 1.3: range 0.9 to 2.1 (Coburn et al., 2009)

The fluNet database itself is primarily accessible for epidemiological studies to assess the patterns of mutation and migration of the virus. For our purposes, a scientific report from Nature (Alonso et al., 2015) provided an open pre-processed data containing the underlying epidemiology data split between 125 countries over from 2009 to 2014.

### Human Mobility Sources
In terms of human mobility, a number of options were assessed with a criteria that it must be over at least a decade to identify patterns, and there are features that can be used. The initial source of this data was based on a radio discussion in March 2020 that referred to the average person travelling 2km per day in the 1900s, compared to 10km today, but the caller in this case was anonymous, and no data was found to support this claim locally or globally.

To counter this, we will examined a number of methods of determining how far the average human travels each day per country or region. Direct commute times are limited in their range, such as the the addition of commute times in the Censure of Ireland (CSO, 2016), which show no significant individual change in overall commute times (~26 minutes) while focused on one urban area. Another source of data is the Mobile Phone data, which has a number of pools from both vendors and data aggregation sources, have been shown to be inconsistent to identify mobility patterns that are comparable globally, and exhibit missing pattern data (Li et al., 2019)

### Data Sources

The data sources for this project are two public data sources for both domains that provide data per country over time. The first is the FluNet database described above, and while the repository allows access to datasets via exporting information from the web based explorer (“FluNet database of the WHO Global Influenza Surveillance Network,” 2020), there is a scope for error in downloading the complete data set. To circumvent this, we pulled the pre-parsed aggregated dataset for the EpiPOI toolset (Alfonso et al., 2015), which contains the agregated data from 1995 to 2014.

Population Human mobility statistcs were extracted from the World Bank data repositiory. This data is available in both CSV file format and directly in JSON. We used the python wbdata library, which allows named datasets to be imported as dataframes directly. The libraries Chosen for this analysis were the following:

    - Population Data Metrics:
        - SP.POP.0014.TO.ZS  : Population % between 0 and 14
        - SP.POP.1564.TO.ZS  : Population % between 14 and 64
        - SP.POP.65UP.TO.ZS  : Population % between 65 and up
    - Rural / Urban Populations
        - SP.RUR.TOTL.ZS : Total population % living in Rural locations
        - SP.URB.TOTL.IN.ZS : Total population % living in Urban locations
    - Mobile Phone Penetration Rates
        - IT.CEL.SETS.P2 : Cellphone Penetration Rates

It is worth noting that there is a large discrepancy between methods of recording each of the above metrics in terms of the definition of what is rural and urban, and the methods of identifying cellhone ownership.

## Selection & Data Understanding
The initial data exploration has provided insights into the data being used. There are 240 dates representing the monthly entries from 1995 to 2014. These are displayed with 144 countries listed in the Influenza data sets, broken down into one data page for each Influenza strain. For the purpose of this assessment, we will only be looking at unclassified Type B, which is known as seasonal flu. The first  observation is that of the 34,500 data points, almost 70% (23,800) did not contain data points. The lack of data at these points indicates either no reporting or no reported cases, and we will work with the 10,760 data points that are valid.

Of the datapoints that are valid, we can view in the dataset that the number of instances has a periodic peak, roughly each year, with the last 5 years seeing a consistent background complemented by higher peak that are related to the increased reporting of seaonal across regions.

The worldbank dataset that is used can be pulled down and aggregated into a single, multi-index data frame to enable direct manipulation of the data, and a single clean utility for the feature data sets. The informaiton is via 254 country entries, including some aggregation regions (Arab World, Western Europe). There is also an available list of countries that can be used to cross reference, and expand the feature set. This will come in useful when examining features such as geographical position and validation of the country name from both reference sources. During this exercise the information source covered 15,840 entries covering 264 Countries and Regions.

Developing an understanding of the application domain, the relevant prior knowledge, the goals of the end-user
Creating a target data set: selecting a data set, or focusing on a subset of variables, or data samples, on which discovery is to be performed.

Both sets use a 

* Understanding Your Data
    * Descriptive Element
    * Vizualisation







## Pre-processing
Removal of noise or outliers.
Collecting necessary information to model or account for noise.
Strategies for handling missing data fields.
Accounting for time sequence information and known changes.

* Transform
* Rescale
* Standardize
* Normalize
* Binarize

## Transformation
Finding useful features to represent the data depending on the goal of the task.
Using dimensionality reduction or transformation methods to reduce the effective number of variables under consideration or to find invariant representations for the data

* Feature Selection

## Data Mining
Searching for patterns of interest in a particular representational form or a set of such representations as classification rules or trees, regression, clustering, and so forth.
Choosing the data mining task.
Deciding whether the goal of the KDD process is classification, regression, clustering, etc.
Choosing the data mining algorithm(s).
Selecting method(s) to be used for searching for patterns in the data.
Deciding which models and parameters may be appropriate.
Matching a particular data mining method with the overall criteria of the KDD process.

* Evaluate Machine Learning algorithms


## Interpretation
Interpreting mined patterns.

Performance metrics in terms of errors and deviation
