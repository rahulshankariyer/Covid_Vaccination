# Covid Vaccination - Effect on Cases & Deaths

## Project Objective

In this project, an analysis was done on whether the Covid Vaccinations led to a decline in Covid-19.

## Data Used

For this purpose, a Covid-19 dataset from the website <a href = "https://ourworldindata.org/covid-deaths"> Our World in Data </a> was used. This dataset contained various data on Covid Cases, Deaths, Testing and Vaccinations. The period chosen was January 1st, 2020 to November 21st, 2022. 

## Tools Used

1. Excel
2. Microsoft SQL Server Management Studio
3. Tableau
4. Python

## Data Transformations

The data used for the purpose of this analysis were:

1. Vaccination Data
2. Postivity Rates
3. Death Rates

Several records in the data had fields with null values which needed to be made into '0' for performing various mathematical calculations on them. So those fields were changed from null to '0'. Most of these null values were during the period prior to roll out of vaccines.

## Analysis

Using SQL Server Management Studio the data of Covid Vaccinations, Cases & Deaths by Date was extracted using the below query:

      --Vaccinations against Covid Cases and Deaths by date

      select d.date,sum(cast(d.new_cases as float)) as total_cases,
      sum(cast(d.new_deaths as float)) as total_deaths,
      sum(cast(v.new_vaccinations as float)) as total_vaccinations
      from ProjectPortfolio..[Covid Deaths] d join ProjectPortfolio..[Covid Vaccinations] v
      on d.location = v.location and d.date = v.date
      where d.continent is not null
      group by d.date
      order by d.date;

Using the data extracted from the above query, the following analysis was performed in Jupyter Notebooks - <a href = "https://github.com/rahulshankariyer/PortolioProject/blob/main/Covid%20Vaccination%20Effect%20on%20Cases%20%26%20Deaths/Covid%2019%20Vaccinations%20vs%20Cases%20%26%20Deaths.ipynb"> Covid Vaccinations, Cases & Deaths With Time (Python) </a>

A consolidated graph of the Dates against Vaccinations, Cases & Deaths, created in Tableau, is given below - 

   ![alt text](https://raw.githubusercontent.com/rahulshankariyer/Covid_Vaccination/main/Covid%20Vaccination%20-%20Effect%20on%20Cases%20%26%20Deaths.png)

## Insights

1. The spike in Covid-19 Vaccinations during the Summer of 2021 was followed by a decrease in the number of Cases & Deaths
2. There was a spike in Cases & Deaths in the Winter of 2021-2022 inspite of increased Vaccinations
3. The number of Vaccinations, Cases & Deaths all decreased consistently throughout the year of 2022

## Conclusion

1. The effect of the Vaccination was mild to negligible on Covid-19 Infections, ie, the spread of the disease
2. The Vaccination had a moderate effect on Deaths, ie, Covid-19 was milder.
3. It was the big spike in Infections in December 2021 that enabled herd immunity. This led to steep decline in new cases & deaths

## Accuracy of the Insights & Conclusions

The accuracy is moderate for the following reasons:

1. The reporting of data in many countries were not reliable. Eg. North Korea and China.
2. The level of vaccinations varied from country to country.
3. The efficacies of different vaccines were different.
