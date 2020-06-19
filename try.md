# GDELT Media Coverage on COVID-19

## Project Charactersitics:
+ Contributer: Konstantin Zapolski, Viktor Martinovic
+ Data: GDELT
+ [GDrive Link](https://drive.google.com/drive/u/0/folders/1U0QTGgv34uHzYKed3HBYWbDmtbaEgETe)
+ [Project flow @drow.io Last update: 22.04.](https://drive.google.com/file/d/11XIyuuC6KXdi9XHKYks8MOS6xIB2dlxv/view?usp=sharing)

## GDELT
|*Name*|*Data*|*Comments*|
|--------------|-----------|--------------------------------|
|GDELT GKG|[data](http://data.gdeltproject.org/gkg/index.html)|40mb -> 120mb per day [entitis, locations, persons, organisations]|
|[GDELT Event Database](https://blog.gdeltproject.org/gdelt-2-0-our-global-world-in-realtime/)|[data](http://data.gdeltproject.org/events/index.html)| [Codebook](http://data.gdeltproject.org/documentation/GDELT-Event_Codebook-V2.0.pdf) 5mb -> 30mb per day [country1, country2]|
|[GDELT Blog](https://blog.gdeltproject.org/) | | Inspiration! ;) |
|---------------------------------|---------------------|-------------------------------------------------------------------------|
|Entitry DB| [Google BQ](https://console.cloud.google.com/bigquery?GK=gdelt-bq&page=table&t=geg_gcnlapi&d=gdeltv2&p=gdelt-bq&redirect_from_classic=true&project=gdelt-265500&folder=&organizationId=)||
|GDELT Online News Summary|[UI](https://api.gdeltproject.org/api/v2/summary/summary)|every news|
|[GDELT Analysis - not online yet](http://analysis.gdeltproject.org/module-gkg-exporter.html)||
|Blogs/ Info| |  [UK_GOV,  ](https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/deaths/methodologies/globaldatabaseofeventslanguageandtonegdeltappendix)      [Knoema_BI_country/events](https://knoema.com/GDELTED2016Sep/gdelt-event-database-total-number-of-events-by-country-monthly-update)|  
|[CAMEO EventCodes](https://www.gdeltproject.org/data/lookups/CAMEO.eventcodes.txt)| | |
|[Full API Search last 24 h](http://api.gdeltproject.org/api/v1/search_ftxtsearch/search_ftxtsearch?query=austria&output)|[Tone](https://api.gdeltproject.org/api/v1/search_ftxtsearch/search_ftxtsearch?query=russia&output=timeline&outputtype=tone&timelinesmooth=1) [Volume](https://api.gdeltproject.org/api/v1/search_ftxtsearch/search_ftxtsearch?query=austria&output=timeline&outputtype=vol&timelinesmooth=5) [Img](https://api.gdeltproject.org/api/v1/search_ftxtsearch/search_ftxtsearch?query=austria&output=artimglist&dropdup=true)|other sources available (heute, vol, orf, etc.)|
|[Live Map of News](http://live.gdeltproject.org/) | | |
|Last 15 Minutes| [Eng](http://data.gdeltproject.org/gdeltv2/lastupdate.txt) [Translated](http://data.gdeltproject.org/gdeltv2/lastupdate-translation.txt)|
|Entity Graphs|[page](https://blog.gdeltproject.org/announcing-the-global-entity-graph-geg-and-a-new-11-billion-entity-dataset/)||
|Geo Query JSON|[Link](https://api.gdeltproject.org/api/v2/geo/geo?query=austria&format=GeoJSON)||
|domain by country| [.txt](http://data.gdeltproject.org/supportingdatasets/DOMAINSBYCOUNTRY-ENGLISH.TXT)||
|CAMEO coutry codebook| [git](https://github.com/carrillo/Gdelt/blob/master/resources/staticTables/CAMEO.country.txt)||
|[Global Geographic Graph ggg](https://blog.gdeltproject.org/announcing-the-global-geographic-graph/)|[MASTERFILELIST.txt](http://data.gdeltproject.org/gdeltv3/ggg/MASTERFILELIST.TXT) | |
| [COVID-19 DATASET](https://blog.gdeltproject.org/announcing-a-massive-new-geographic-news-database-of-the-locations-mentioned-in-covid-19-news-coverage/) |[GBQ interface](https://console.cloud.google.com/bigquery?p=gdelt-bq&d=covid19&t=onlinenewsgeo&page=table&project=gdelt-265500&folder=&organizationId=) | |
|---------------------------------|---------------------|-------------------------------------------------------------------------|
|[WorldCloud_leader_by_country](https://www.gdeltproject.org/gallery-word-cloud-countries.html) | | |


## Mission:
- This project targets to visualize the relationship of media during the COVID-19 period (Jan2020 - April2020)

## Target Benefit:
- Insight information about countries, tone sentiment, volume

## Stakeholder:
- Media, Politician, Tourism Industry, etc.

## Challanges and Problems:
- GDELT GKG data availability - 11.5 TB of data need sophisticated SQL queries to avoid high billing ( 1 TB = 5euro)


## TEST ZONE
Markdown formatting: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

```
test
```

![](https://github.com/zapkon/GDELT_COVID19/blob/master/pictures/BBVA.jpg)

