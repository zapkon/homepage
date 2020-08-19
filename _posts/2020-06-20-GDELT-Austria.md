---
title: "The GDELT Perspective - Austria in the Global News"
date: 2020-06-20
tags: [Austria, Diplomacy,  GDELT, News Media]
header:
  image: "/images/GDELT/map5.jpg"
excerpt: "GDELT, News Media, Diplomacy"
mathjax: "true"
---
1111111111111111111111111111111143532535353535311Like Leviathan. The [GDELT Project](https://www.gdeltproject.org/) is the largest, most comprehensive, and highest resolution open database of human society ever created and stands for "Global Dataset on Events, Languages and Tone".

This post [showcase](https://blog.gdeltproject.org/) what we can learn from GDELT about the country of Mozart, [Schnitzel](http://www.brigittenauerstadl.at/index.html) and Red Bull. Credits to [Viktor](https://twitter.com/martino_vic) for assistance!

News Media from all corners of the earth are crawled by the algorithm. It extracts and codifies systematically the information, such as Date, [CAMEO Event](http://data.gdeltproject.org/documentation/CAMEO.Manual.1.1b3.pdf), Sentiment, Entities (i.e. Persons, Organisations) GeoLocations Countries and much more.

![alt]({{ site.url }}{{ site.baseurl }}/images/GDELT/facet grid.png)
The plot indicates the 7 (out of 150) most frequent event categories in which context Austria was mentioned with one of the 5 countries. Dots represent the weekly sentiment (AvgTone). We see that during March/April the dots are very red - bad sentiment is explained simply by COVID-19 panic epidemy.

For constructing the plot I´ve processed the raw data, and I hope this final data frame give you more intuition about GDELT: ![alt]({{ site.url }}{{ site.baseurl }}/images/GDELT/data screenshot.jpg)

GDELT has a great ability for modelling network dynamics with packages like [visNetwork](https://cran.rstudio.com/web/packages/visNetwork/vignettes/Introduction-to-visNetwork.html). Here I´ve created a simple plot representing the average sentiment (color) and frequency (size) of the events and the countries in relationship with Austria!
![alt]({{ site.url }}{{ site.baseurl }}/images/GDELT/sna.png)
PS: Austria has also a size and sentiment, which represents the interaction of two entities within Austria e.g. Actor1 = Austrian Government and Actor2 = Red Bull company!

Overall GDELT is a powerful source, can be interpreted as a proxy, to study various aspects such as evolution or snapshot of international relationships and emerging topics.

You can download all GDELT Event Files on daily level [here](http://data.gdeltproject.org/events/index.html). Respectively the [codebook](http://data.gdeltproject.org/documentation/GDELT-Event_Codebook-V2.0.pdf).

The data was retrieved via API in .R and I know many people have problems with getting the data. Therefore I wrote a function to smoothly download data (~ 10 MB per day). A part of the GDELT project is also hosted on [Google BigQuery](https://console.cloud.google.com/bigquery?p=gdelt-bq&d=gdeltv2&page=dataset&project=gdelt-265500&folder=&organizationId=).
You can customize the function´s input: start_date, end_date, steps and country_code to get the data.
I´ve applied a filtering of 25 parameter and picked Austria data:

```r
library(GDELTtools)
library(data.table)
library(dplyr)
library(ggplot2)

folder = "~/Documents/GDELT"

get_GDELT_data = function(  start = Sys.Date()-2 , end = Sys.Date()-1 , merger_steps = 5, country_code = "AUT") {
  #browser()

  start = as.Date(start)
  end   = as.Date(end)

  time_diff = as.numeric( difftime(end, start, units= "days") )
  interval  = unique(  c( seq(0, time_diff,  merger_steps), time_diff) )

  datalist  = list()
  i2        = 0
  count     = 1

  for (i in interval  ) {

    start_tmp = start +i2
    end_tmp   = start +i

    temp_data <- GetGDELT(start.date = start_tmp, end.date = end_tmp, local.folder = folder ) %>%
      select(., SQLDATE,
             Actor1Code, Actor1Name, Actor1CountryCode, Actor1Type1Code,
             Actor2Code, Actor2Name, Actor2CountryCode, Actor2Type1Code,
             IsRootEvent, EventCode, EventRootCode, GoldsteinScale,
             NumMentions, NumSources, NumArticles, AvgTone, Actor1Geo_FullName, Actor2Geo_FullName,
             Actor1Geo_CountryCode, Actor2Geo_CountryCode,
             ActionGeo_FullName, ActionGeo_CountryCode, ActionGeo_Lat, ActionGeo_Long,
             SOURCEURL) %>%
      filter(Actor1CountryCode ==  country_code | Actor2CountryCode == country_code)

    i2                = i+1
    datalist[[count]] = temp_data
    count             = count+1
    Sys.sleep(20)
  }

  DF_gdelt = do.call(rbind, datalist)
  return(DF_gdelt)
}

DF_austria = get_GDELT_data( "2020-01-01" , "2020-06-19", 10, country_code = "AUT")   # Apply the function!
```

Happy Discovering!
