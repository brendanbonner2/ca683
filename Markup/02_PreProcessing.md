## Data cleaning and preprocessing.

The data selected by the previous step ensured that we had access to data sources to be able to develop a hypothesis around the data and to have enough data to allow the information to be analysed, but there are also a number of elements in the dataset that need to be cleaned and preprocessed before we can reduce the data set for 

The aim is to ensure the data is Qualitive (Binominal, Nominal or Ordinal) or Quantitived (discrete or continuous) to allow us to apply the right analytic technique to understand the data.

Date	Quantative, Continuous

Input Data
Population
Flu Cases	Quantitive, Continuous
Mobile Usage	Quantitive, Nominal
Latitude
Longitude

Output
Modern	Quantative, Discrete
Flu/1m	Quantitive, Discrete

### Data Understanding

The initial data exploration has provided insights into the data being used. There are 240 dates representing the monthly entries from 1995 to 2014. These are displayed with 144 countries listed in the Influenza data sets, broken down into one data page for each Influenza strain. For the purpose of this assessment, we will only be looking at unclassified Type B, which is known as seasonal flu. The first  observation is that of the 34,500 data points, almost 70% (23,800) did not contain data points. The lack of data at these points indicates either no reporting or no reported cases, and we will work with the 10,760 data points that are valid.

Of the datapoints that are valid, we can view in the dataset that the number of instances has a periodic peak, roughly each year, with the last 5 years seeing a consistent background complemented by higher peak that are related to the increased reporting of seaonal across regions.

The worldbank dataset that is used can be pulled down and aggregated into a single, multi-index data frame to enable direct manipulation of the data, and a single clean utility for the feature data sets. The informaiton is via 254 country entries, including some aggregation regions (Arab World, Western Europe). There is also an available list of countries that can be used to cross reference, and expand the feature set. This will come in useful when examining features such as geographical position and validation of the country name from both reference sources. During this exercise the information source covered 15,840 entries covering 264 Countries and Regions.

Developing an understanding of the application domain, the relevant prior knowledge, the goals of the end-user
Creating a target data set: selecting a data set, or focusing on a subset of variables, or data samples, on which discovery is to be performed.

Steps Taken:

Missing Data In both data sets, there is missing data in the form of a lack of reporting or unknown information reported. In the case of the fluNet data, it can logically be assessed that the information in earlier years was due to the lack of reporting and as such, it's reliability is lower while in earlier years, while the commonality of seasonal flu results in a large number of cases not been required to be reported until the case requires intervention. In the case of the flue data, we will not make assumptions that the data is fully reliable, and as such we can disregard unreported cases per country to reduce the data set by 70% to identify verified reported cases.

Aggregation: The data provided for the FluNet database includes a series of non-country definitions that are aggregations of infections per WHO region. For the purpose of this exercise, we will be looking at country level statistics only, and these have been removed.

Missing Data by Inference: In the case of population growth, mobile phone usage and rural/urban dwelling figures, there are two cases for missing data; non reporting and lack of granularity. In our target data set, we are looking to identify the current metric at a resolution per month. Without further information regarding crisis or major upheaval, each of these indicators can have their growth infered to achieve granularity. To achieve this, we filled the blank data for each of these indicators by spline interpolation with a k of 5, which provides a smooth growth (either positive or negative) to be able to determine the current national status at the time of the reported cases.

Date Alignment: All data has been provided in either annual or monthly. In all cases, we indexed based on the complete date on the first day of each month.

Rural/Urban Divide: It was partially hoped that additional data could be extrapolated by examining members of population who do not define as either Urban or Rural, but in all cases the population was one or the other.

Country Names: In the case of country names, the prefered method is to use standardised IDs for identifying countries, such as iso2codes, but this is not always possible. In this case, we have the World Bank countries list, which includes information regarding the country, including wealth limits (which is useful later) and location, plus other extraneous information. We used a thrid party package *country_converter* to convert the countries into a standard format, which resulted in two errors - 'Serbia and Montenegro (2003-2006)' & 'Channel Islands'. In this case, the latter had no infections, and the number of entries related to the former allowed us to integrate the numbers with Serbia.  


Removal of noise or outliers.
Collecting necessary information to model or account for noise.
Strategies for handling missing data fields.
Accounting for time sequence information and known changes.
