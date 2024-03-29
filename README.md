# CrowdfundingInsights

Hello, there! Welcome to CrowdfundingInsights!


<img src="https://www.eatplaydrink.capetown/wp-content/uploads/2019/06/footer_image.png" />


Let me introduce it.


## Value Proposition:
**Crowdfunding Insights** is a web application that provides nonprofits such as [Kiva](https://www.kiva.org/about/) with a detailed analysis of their outreach efforts, lending partners, and recipients. 

This product provides thoughtful analysis of their critical data and tools to help simplify their outreach efforts to partners and borrowers, helping lenders understand their target communities thoughtfully, allowing them to maximize their efforts, make better informed decisions, and help set investment priorities.


## Key Features:
* Allow the user to analyze and filter loan distribution by theme category, region, country, theme, sector, activity, expected duration, and partners.

* Provide the user with poverty level based lending suggestions by analyzing the multidimensional poverty index(MPI) of regions and external poverty resources including:
	*  [**World Development Indicators**](https://datacatalog.worldbank.org/dataset/world-development-indicators/)
	*  [**Prevalence of Unemployment**](https://datatopics.worldbank.org/jobs/)

* Allow the user to analyze the geolocations of the loan distribution and needs per theme category, activity, borrowing intensity (amount, frequency).

* Provide recommendations on what lender Kiva should approach with a funding need based on a given region, amount, expected duration of the loan, and category.


## Perspectives:
The responsive web application is capable of communicating with backend SQL database. By searching from keywords, it pulls data from the relational data model. From there, it drives further comparative analysis by traverse the primary keys through the data models, and visualize data outcomes through tables, charts, or geographical maps. 


#### From Loans:
![](https://github.com/Jiapei1001/CrowdfundingInsights/blob/main/WebContent/resources/images/find%20loans.gif)
<br>
<br>
#### From Loan Partners:
![](https://github.com/Jiapei1001/CrowdfundingInsights/blob/main/WebContent/resources/images/find%20partners.gif)
<br>
<br>
#### From Loan Themes:
![](https://github.com/Jiapei1001/CrowdfundingInsights/blob/main/WebContent/resources/images/find%20themes.gif)



## Data Warehousing:

### External Data Source:

* Dataset 1: [**World Development Indicators**](https://datacatalog.worldbank.org/dataset/world-development-indicators/)

	This is a CSV file obtained from The World Bank, specifically from the world development indicators database. This dataset includes information on various metrics covering economy and growth, education, and environment. With the variety of indicators included in this dataset we plan to investigate whether access to financial institutions, education, etc. correlates to funding amount. Looking at these metrics will also help us to provide recommendations to Kiva with regards to where the need for more funding may be the greatest.



* Dataset 2: [**Prevalence of Unemployment**](https://datatopics.worldbank.org/jobs/)

	In this data set, we look at the prevalence of unemployment in a country. The numbers are given as a percentage as the total workforce. Our reason for investigating the unemployment rate is that small businesses are at a higher risk of going under, and that we expect to see a correlation between loans requested and unemployment. Although the dataset included many years worth of data, we chose to only look at 2018.

### ETL Workflow #1: 
### Percentage of Population with an Account at a Financial Institution By Country

The inspiration behind this graph was to determine if there was a negative correlation between the percentage of those with an account at a financial institution and the loan count. Surprisingly the correlation coefficient was only -0.14 indicating that there is no correlation between account ownership and loan count.

<p align="center">
<img src="https://raw.githubusercontent.com/Jiapei1001/CrowdfundingInsights/main/WebContent/resources/images/ETL1_Population%20with%20an%20Account%20By%20Country.png" width=66% align="center"/>
</p>

In the graph below,  the average percentage of the population with account ownership by country is represented by a bar chart and sorted in ascending order. The loan count per country was normalized to be within the range of 0 - 100 (the same range as the percentage data) and overlaid on top of the account ownership data.

<p align="center">
<img src="https://raw.githubusercontent.com/Jiapei1001/CrowdfundingInsights/main/WebContent/resources/images/ETL1_result.png" width=66% align="center"/>
</p>

Kiva’s goal is to provide access to loans to those who have limited access to obtaining a loan from a financial institution. A country with a low percentage of their population having an account at a financial institution could benefit greatly from a crowdfunding service such as Kiva.

We can use this data to help inform future funding efforts. For example, only 10% of the population in South Sudan had an account at a financial institution, but the normalized loan count is nearly zero. Kiva can increase their outreach efforts in this area and notify partner lenders of the need.

<p align="center">
<img src="https://raw.githubusercontent.com/Jiapei1001/CrowdfundingInsights/main/WebContent/resources/images/ETL1_result_map.png" width=66% align="center"/>
</p>

### ETL Workflow #2: School Enrollment

When extract the average school enrollment and loans from the dataset, the hypothesize is that there was a positive correlation between average school enrollment (primary) and loan count. 

<p align="center">
<img src="https://raw.githubusercontent.com/Jiapei1001/CrowdfundingInsights/main/WebContent/resources/images/ETL3_School%20Enrollment.png" width=66% />
</p>

We hope that countries with low school enrollment could obtain more loans so that children in these countries are able to receive a better education. Even though the correlation coefficient between them is low, we believe for a few countries, like the Philippines, the loans support children in getting a better education to some extent. Next, we could collect more information, like the policy of each country. For example, due to the nine-year compulsory education, the loan count for China is low but the average school enrollment is high. After analysis, we could find out which countries really need more help and notify lenders.

<p align="center">
<img src="https://raw.githubusercontent.com/Jiapei1001/CrowdfundingInsights/main/WebContent/resources/images/ETL3_result.png" width=66% />
</p>

### ETL Workflow #3: Loan Amount Distribution and GDP by Country

The intents of charts are to zoom into the correlations between the country average GDP and the total loan amount, and their geographical distributions. We wanted to study if the loans are evenly distributed, or have a positive or negative correlation with average GDP.

<p align="center">
<img src="https://raw.githubusercontent.com/Jiapei1001/CrowdfundingInsights/main/WebContent/resources/images/ETL4_Loan%20Amount.png" width=66% />
</p>

<br>
From the results, we can see the correlation is relatively low. In countries with higher GDP, loan amounts are randomly distributed; contrasts are high (see comparisons between Brazil, Turkey and Mexico). In countries with lower GDP, we can see huge contrasts, between countries with high loan amounts (Philippines, Kenya, Cambodia, El Salvador) and countries with low loan amounts (Burundi, Malawi, Togo, etc).

<p align="center">
<img src="https://raw.githubusercontent.com/Jiapei1001/CrowdfundingInsights/main/WebContent/resources/images/ETL4_GDP.png" width=66% />
</p>

If the intent of Kiva is to support need-based local recipients to conduct small businesses, outreach efforts in countries with low GDP and low amounts are suggested to be further explored. Increasing loan lending channels in those areas through collaborations with local authorities, educating local residents to increase awareness, etc. It is also suggested to utilize the successful model and lessons in the Philippines to project outreach efforts into countries (at the leftmost side x-axis).


## Data Source:

The web application is created with the [Kiva Crowdfunding data](https://www.kaggle.com/kiva/data-science-for-good-kiva-crowdfunding?select=kiva_loans.csv). The data set consists of four csv files. The csv files are inserted into MySQL and to aggregate the data together into different tables. There is over 672k rows of loan information in the first csv file.

### UML Diagram:

<p align="center">
<img src="https://raw.githubusercontent.com/Jiapei1001/CrowdfundingInsights/main/WebContent/resources/images/UML.jpeg" width=80% />
</p>
