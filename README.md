# Data and code for analyzing COVID-19 excess mortality in northern Italian towns, January - April 2020


**Working paper** https://medrxiv.org/cgi/content/short/2020.06.10.20125005v1

**Data** 


* Overview of data used
  + Deaths from 1 January to 15 April for the years 2017, 2018, 2019, 2020 (The ISTAT data extract includes deaths through 30 April for the years before 2020, so observations for days after 15 April are excluded.)
  + Deaths by five age groups: 0-14 years, 15-54, 55-64, 65-74, 75+ (aggregated from raw ISTAT data)
  + Deaths for Male, Female, Total 
  + Select the provinces of Milano, Bergamo, Brescia, and Lodi which were particularly badly hit by the coronavirus, giving 612 towns
* Mortality from ISTAT, extracted first week of June 2020: 
  + https://www.istat.it/it/archivio/240401 – a cover page titled _Decessi e Cause di Morte: Cosa Produce L’ISTAT_ (Deaths and Causes of Death: What ISTAT Produces)
  + Detailed mortality data under _Dataset analitico con i decessi giornalieri in ogni singolo comune di residenza_ (Analytical dataset with daily deaths in each single municipality of residence (https://www.istat.it/it/files//2020/03/Dataset-decessi-comunali-giornalieri-e-tracciato-record.zip)
  + Deaths by day from 1-jan -> 30-apr for the years 2015, 2016, 2017, 2018, 2019, and for 1-jan -> 15-apr for 2020
    + Must exclude 16-apr -> 30-apr
  + Deaths by 5-year age group: code in 8th column “CL_ETA”: 0= 0 1=1-4 2=5-9 3=10-14 4=15-19 5=20-24 6=25-29 7=30-34 8=35-39 9=40-44 10=45-49 11=50-54 12=55-59 13=60-64 14=65-69 15=70-74 16=75-79 17=80-84 18=85-89 19=90-94 20=95-99 21=100+
  + Deaths for Male, Female, Total
  + By town
* Population from ISTAT, extracted first week of June 2020:
  + Source: Web: http://demo.istat.it/pop2019/index3.html
  + Download individual Provinces (Milano, Bergamo, Brescia, Lodi) under region Lombardia, 
  + Change the “2019” to “2018” etc in the URL above
  + ID "Denominazione" matches the mortality ID "NOME_COMUNE"
  + by male and female
  + by single years 
  + Must sum up to above ages in R. 
  + Only have population for 2019, so use this for 2020 
* Zipped version of data files (created first week of June 2020) 
  + Zipped file _data.zip_ which will exapnd to a subdirectory "data" with the following .csv files:
  + Population files: Bergamo2017.csv, Bergamo2018.csv, Bergamo2019.csv, Brescia2017.csv, Brescia2018.csv, Brescia2019.csv, Lodi2017.csv, Lodi2018.csv, Lodi2019.csv, Milano2017.csv, Milano2018.csv, Milano2019.csv
  + Mortality counts: comuni_giornaliero.csv



**RStudio notebooks**, each with explanation and code. 

* _ItalyTown_master.Rmd_ is the master, to be run in RStudio, and will call the others (by converting them to .r on-the-fly and then executing them via a "source" command)
* _ItalyTown_functions.Rmd_ contains functions used
* _ItalyTown_readdata.Rmd_ code for reading and transforming data

btw, if you want to extract just the R code, run
- library (knitr)
- knit('_notebook.Rmd_', tangle=TRUE)

and this will save _notebook.R_ under your working directory

**Output**, each with explanation and code. 

* The regression results are embedded in the _ItalyTown_master.Rmd_ notebook
* Town-by-town excess mortality, 2020 actual and predicted, and 2019 actual a predicted mortality are written out in .csv files _xpred_FE_town2020_age2020_excess.csv_, _xpred_FE_town2020_age2020_mort.csv_, _xpred_FE_town2020_age2019_mort.csv_
* The Excel file _results1_55.xlsx_ **must** be in the working direcgtory - various summary tables are written to and formatted in that file. 