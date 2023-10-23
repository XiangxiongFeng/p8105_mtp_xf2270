MT_Project
================
Xiangxiong Feng
2023-10-23

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
    ## 
    ## 载入程辑包：'rvest'
    ## 
    ## 
    ## The following object is masked from 'package:readr':
    ## 
    ##     guess_encoding

# Part-1

The two raw datasets include `USPS CHANGES OF ADDRESS NYC` and
`Zip Codes`. The ‘USPS CHANGES OF ADDRESS NYC’ shows the aggregate
Change of Address (COA) data in New York City between 2018 and 2022. The
data includes 7 variables such as zip code. There are total 11845
observations. The ‘Zip Codes’ is a supplementary dataset which has
important variables such as name of county and its neighborhood. There
are 8 variables and 324 observation. The main goal of this report is to
have a insights into trends in moving and changes of population size in
different location in NYC.

The first part is data cleaning and combination. For COA data, a
variable `year` is added, and a variable `net_change` is created by
subtracting outbound COAs from inbound COAs. For Zip Codes data, a
variable `borough` is created using county names. Then, the two datasets
are combined together and irrelevant variables are dropped. The
resulting tidy dataset has 12168 observation and 9 variables. There are
320 unique ZIP codes and 42 unique neighborhood.

Then the `city` variable and \`borough variable is compared. The table
below shows the most common values of city in the borough of Queens.

| CITY                | Count |
|:--------------------|------:|
| JAMAICA             |   372 |
| FLUSHING            |   309 |
| ASTORIA             |   230 |
| QUEENS VILLAGE      |   165 |
| BAYSIDE             |   135 |
| LONG ISLAND CITY    |   120 |
| EAST ELMHURST       |   117 |
| OZONE PARK          |   116 |
| FRESH MEADOWS       |   107 |
| FAR ROCKAWAY        |   102 |
| LITTLE NECK         |    79 |
| RIDGEWOOD           |    70 |
| FLORAL PARK         |    68 |
| ELMHURST            |    63 |
| KEW GARDENS         |    62 |
| BELLEROSE           |    60 |
| BROOKLYN            |    60 |
| COLLEGE POINT       |    60 |
| CORONA              |    60 |
| HOWARD BEACH        |    60 |
| REGO PARK           |    60 |
| FOREST HILLS        |    59 |
| HOLLIS              |    59 |
| ROSEDALE            |    59 |
| WOODHAVEN           |    59 |
| WOODSIDE            |    59 |
| CAMBRIA HEIGHTS     |    58 |
| MASPETH             |    58 |
| MIDDLE VILLAGE      |    58 |
| SAINT ALBANS        |    57 |
| ARVERNE             |    56 |
| JACKSON HEIGHTS     |    56 |
| WHITESTONE          |    55 |
| RICHMOND HILL       |    54 |
| GLEN OAKS           |    52 |
| SUNNYSIDE           |    51 |
| ROCKAWAY BEACH      |    49 |
| SOUTH OZONE PARK    |    49 |
| BREEZY POINT        |    47 |
| SOUTH RICHMOND HILL |    47 |
| ROCKAWAY PARK       |    40 |
| DOUGLASTON          |    39 |
| OAKLAND GARDENS     |    38 |
| SPRINGFIELD GARDENS |    30 |
| LAURELTON           |    28 |
| LONG IS CITY        |    19 |
| BRIARWOOD           |    16 |
| NA                  |    16 |
| ROCKAWAY POINT      |    13 |
| BELLE HARBOR        |    11 |
| GLENDALE            |    11 |
| S RICHMOND HL       |     9 |
| QUEENS VLG          |     8 |
| S OZONE PARK        |     8 |
| BAYSIDE HILLS       |     6 |
| BROAD CHANNEL       |     5 |
| BEECHHURST          |     4 |
| KEW GARDENS HILLS   |     4 |
| NEPONSIT            |     4 |
| AUBURNDALE          |     2 |
| BELLEROSE MANOR     |     2 |
| SPRNGFLD GDNS       |     2 |
| CALVERTON           |     1 |
| CAMBRIA HTS         |     1 |
| JACKSON HTS         |     1 |
| MIDDLE VLG          |     1 |
| NEW YORK CITY       |     1 |
| ST ALBANS           |     1 |

The table below shows the most common values of city in the borough of
Manhattan(New York County).

| CITY             | Count |
|:-----------------|------:|
| NEW YORK         |  3477 |
| BRONX            |    60 |
| BROOKLYN         |    59 |
| NA               |    57 |
| CANAL STREET     |     4 |
| ROOSEVELT ISL    |     4 |
| ROOSEVELT ISLAND |     4 |
| BOWLING GREEN    |     1 |
| BROOKLYN HEIGHTS |     1 |
| NYC              |     1 |
| SECHEDATY        |     1 |
| WALL STREET      |     1 |

There are 60 months between 2018 and 2022. However, some of ZIP codes
have fewer 60 observations. The reason is that the records of some ZIP
codes for cerain months are missing in raw COA data. Moreover, most of
these are also missing neighborhood values, which are not given by the
origin Zip Codes data. For example, the records for ZIP code 10008 for
certain months are missing, and this ZIP cod has fewer 60 observations.
The neighborhood of this Zip code is also missing.

# Part-2

A table showing the average of `net_change` in each borough and year is
created and shown below. From this table, we can see that the overall
average net change keeps getting more negative from 2018 and reach an
unusual peak around 2020, then it begins to return to normal level. The
overall population size is dercreasing.

    ## `summarise()` has grouped output by 'borough'. You can override using the
    ## `.groups` argument.

| borough   | year | Average_net_change |
|:----------|:-----|-------------------:|
| Bronx     | 2018 |             -46.30 |
| Bronx     | 2019 |             -48.02 |
| Bronx     | 2020 |             -72.65 |
| Bronx     | 2021 |             -66.10 |
| Bronx     | 2022 |             -53.19 |
| Kings     | 2018 |             -46.18 |
| Kings     | 2019 |             -51.68 |
| Kings     | 2020 |            -110.67 |
| Kings     | 2021 |             -76.84 |
| Kings     | 2022 |             -55.38 |
| Manhattan | 2018 |             -39.80 |
| Manhattan | 2019 |             -52.54 |
| Manhattan | 2020 |            -127.70 |
| Manhattan | 2021 |             -39.47 |
| Manhattan | 2022 |             -46.18 |
| Queens    | 2018 |             -25.71 |
| Queens    | 2019 |             -28.09 |
| Queens    | 2020 |             -46.55 |
| Queens    | 2021 |             -43.30 |
| Queens    | 2022 |             -29.28 |
| Richmond  | 2018 |              -9.85 |
| Richmond  | 2019 |              -9.12 |
| Richmond  | 2020 |             -10.54 |
| Richmond  | 2021 |             -22.55 |
| Richmond  | 2022 |             -16.30 |

The table below shows the five lowest values of net change. We can see
that all see that all these five observation are made in 2020, which is
corresponding to our last table. The reason could be population loss and
death caused COVID pandemic.

| ZIPCODE | Neighborhood                  | year | month | net_change |
|--------:|:------------------------------|:-----|:------|-----------:|
|   10022 | Gramercy Park and Murray Hill | 2020 | 05    |       -983 |
|   10009 | Lower East Side               | 2020 | 07    |       -919 |
|   10016 | Gramercy Park and Murray Hill | 2020 | 06    |       -907 |
|   10016 | Gramercy Park and Murray Hill | 2020 | 07    |       -855 |
|   10009 | Lower East Side               | 2020 | 06    |       -804 |

The table below shows the five highest values of net change across data
observed before 2020. These neighborhoods could have higher commerical
value and value of further development.

| ZIPCODE | Neighborhood        | year | month | net_change |
|--------:|:--------------------|:-----|:------|-----------:|
|   11101 | Northwest Queens    | 2018 | 04    |        360 |
|   11101 | Northwest Queens    | 2018 | 06    |        344 |
|   11101 | Northwest Queens    | 2018 | 05    |        300 |
|   10001 | Chelsea and Clinton | 2018 | 07    |        225 |
|   11201 | Northwest Brooklyn  | 2018 | 04    |        217 |

A plot of overall average net change across boroughs at
neighborhood-level is shown below. For the plot, we can see that
Manhattan experienced the largest population loss during April to
September. There are many potential reasons such as Many college
students graduating and at this time. There are some limitations of this
dataset for understanding changes in ZIP code level population sizes.For
example, several different ZIP codes are used in one same neighborhood.

    ## `summarise()` has grouped output by 'borough', 'month'. You can override using
    ## the `.groups` argument.

<img src="mt_project_files/figure-gfm/unnamed-chunk-8-1.png" width="90%" />

    ## For information on available language packages for 'koRpus', run
    ## 
    ##   available.koRpus.lang()
    ## 
    ## and see ?install.koRpus.lang()

    ## 
    ## 载入程辑包：'koRpus'

    ## The following object is masked from 'package:readr':
    ## 
    ##     tokenize

| Method          | koRpus      | stringi       |
|:----------------|:------------|:--------------|
| Word count      | 499         | 488           |
| Character count | 2984        | 2984          |
| Sentence count  | 35          | Not available |
| Reading time    | 2.5 minutes | 2.4 minutes   |

# appendix

``` r
library(tidyverse)
library(ggridges)
library(patchwork)
library(rvest)
library(readxl)

knitr::opts_chunk$set(
    echo = TRUE,
    warning = FALSE,
    fig.width = 8, 
  fig.height = 6,
  out.width = "90%"
)

theme_set(theme_minimal() + theme(legend.position = "bottom"))

options(
  ggplot2.continuous.colour = "viridis",
  ggplot2.continuous.fill = "viridis"
)

scale_colour_discrete = scale_colour_viridis_d
scale_fill_discrete = scale_fill_viridis_d
#import data and clean data
zip_code =
  read.csv('data/Zip Codes.csv') |>
  mutate(borough = County.Name)|>
  rename(ZIPCODE = ZipCode)

change_address_2018 = 
  read_excel('data/USPS CHANGE OF ADDRESS NYC.xlsx', sheet = 1)
change_address_2019 = 
  read_excel('data/USPS CHANGE OF ADDRESS NYC.xlsx', sheet = 2)
change_address_2020 = 
  read_excel('data/USPS CHANGE OF ADDRESS NYC.xlsx', sheet = 3)
change_address_2021 = 
  read_excel('data/USPS CHANGE OF ADDRESS NYC.xlsx', sheet = 4)
change_address_2022 = 
  read_excel('data/USPS CHANGE OF ADDRESS NYC.xlsx', sheet = 5)

change_address = 
  bind_rows(change_address_2018,change_address_2019,change_address_2020,change_address_2021,change_address_2022)|>
  separate(MONTH, into = c('year','month'), sep = 4)|>
  mutate(
    month = str_replace(month,'\\-',''),
    net_change = `TOTAL PERM IN`- `TOTAL PERM OUT`)|>
  separate(month, into = c('month', 'day'),sep = 2 )|>
  select(-day)


#data combination
full_data = 
  full_join(change_address,zip_code, by ='ZIPCODE')|>
  select(-State.FIPS, -County.Code, -County.FIPS, -County.Name, -File.Date)|>
  mutate(
    borough = str_replace(borough, 'New York', 'Manhattan')
  )
#most common values of city in the borough of Queens
full_data |>
  filter(borough == 'Queens')|>
  group_by(CITY)|>
  summarise(Count = n())|>
  arrange(desc(Count))|>
  knitr::kable()
#most common values of city in the borough of Manhattan
full_data |>
  filter(borough == 'Manhattan')|>
  group_by(CITY)|>
  summarise(Count = n())|>
  arrange(desc(Count))|>
  knitr::kable()
#table showing the average of net_change in each borough and year
full_data |>
  group_by(borough, year)|>
  summarize(Average_net_change = mean(net_change))|>
  drop_na()|>
  knitr::kable(digits = 2)
  
#a table showing, across all observed data, the five lowest values of net_change
full_data |>
  arrange(net_change)|>
  head(5)|>
  select(ZIPCODE, Neighborhood, year, month, net_change)|>
  knitr::kable()
#five highest values of net change across data observed before 2020
full_data |>
  filter(year%in% c('2018', '2019'))|>
  arrange(desc(net_change))|>
  head(5)|>
  select(ZIPCODE, Neighborhood, year, month, net_change)|>
  knitr::kable()
#verall average net change across boroughs at neighborhood-level
overall_average_net_change =
  full_data|>
  group_by(borough, month,Neighborhood)|>
  summarize(Average_Net_Change = mean(net_change))|>
  drop_na()|>
  ggplot(aes(x= month, y= Average_Net_Change))+ geom_point(aes(color = borough))+
  facet_grid(.~borough)+
  labs(title = 'overall average net change across boroughs')
overall_average_net_change
ggsave("results/overall_average_net_change.pdf", overall_average_net_change, width = 8, height = 5)
wordcountaddin::text_stats("mt_project.Rmd")
```
