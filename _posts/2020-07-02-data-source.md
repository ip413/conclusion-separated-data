---
layout: post
title: 'Data source - round 1 - presidential election, Poland, 2020'
---
![assets/img/data_mismatch/service-2.png]({{site.baseurl}}/assets/img/data_mismatch/service-2.png)
<!--more-->

## Official results

* [https://wybory.gov.pl/prezydent20200628/](https://wybory.gov.pl/prezydent20200628/)
* [dane_w_arkuszach](https://wybory.gov.pl/prezydent20200628/pl/dane_w_arkuszach)
* [wyniki_gl_na_kand_po_obwodach_xlsx.zip](https://wybory.gov.pl/prezydent20200628/data/1/csv/wyniki_gl_na_kand_po_obwodach_xlsx.zip)


You have be aware that although downloaded zip  and xlsx files inside have different checksum from day to day, when you extract and transform content to csv files the checksum should be the same (md5).
I don't know why... 

```
f8cb98a933841c2c120d6d4aabbc466e  wyniki_gl_na_kand_po_obwodach_utf8-1.csv
f8cb98a933841c2c120d6d4aabbc466e  wyniki_gl_na_kand_po_obwodach_utf8-2.csv

2adabb0a686ec17b8b5bfc651c56448b  wyniki_gl_na_kand_po_obwodach_utf8-1.xlsx
92fadaa59a8cfe9940885da194bceb20  wyniki_gl_na_kand_po_obwodach_utf8-2.xlsx
```

You can also work with official service for searching polling stations
* [first round](https://wybory.gov.pl/prezydent20200628/pl/organy_wyborcze/obwodowe/1/pl)
* [second round](https://wybory.gov.pl/prezydent20200628/pl/organy_wyborcze/obwodowe/2/pl)

but... somehow data doesn't match with csv/xlsx files. I don't know what is happening here.

Proof 1
![assets/img/data_mismatch/service-1.png]({{site.baseurl}}/assets/img/data_mismatch/service-1.png)
![assets/img/data_mismatch/excel-1.png]({{site.baseurl}}/assets/img/data_mismatch/excel-1.png)

Proof 2
![assets/img/data_mismatch/service-2.png]({{site.baseurl}}/assets/img/data_mismatch/service-2.png)
![assets/img/data_mismatch/excel-2.png]({{site.baseurl}}/assets/img/data_mismatch/excel-2.png)

Even more, if you find some polling station in both spreadsheet file and web service some data could not match, like number of people entitled to vote. Don't ask me why.

It's safer to use lists of polling districts, but it's not possible to generate such a list for the whole country, example: [https://wybory.gov.pl/prezydent20200628/pl/organy_wyborcze/obwodowe/1/pow/26400](https://wybory.gov.pl/prezydent20200628/pl/organy_wyborcze/obwodowe/1/pow/26400). At least numbers of polling stations match.

## Data I'm working with

The only differences between files I'm working with and official data are:
* 7 rows were removed due to malformed spreadsheet formulas,
* columns with percentage results and invalid votes (suffix "proc") were added,
* addresses of electoral commission were stripped of in csv ',' (comma) character, because of how gnuplot works.

You can these files:
* [assets/data/columns-number.json]({{site.baseurl}}/assets/data/columns-number.json)
* [assets/data/columns-number.txt]({{site.baseurl}}/assets/data/columns-number.txt)
* [assets/data/data.csv]({{site.baseurl}}/assets/data/data.csv)
* [assets/data/data.ods]({{site.baseurl}}/assets/data/data.ods)
* [assets/data/data.sqlite3]({{site.baseurl}}/assets/data/data.sqlite3)

How do I know that I'm working with correct data? Simple: I don't!

But, when I calculated results of first round from my sqlite database with
```
select (100.0 * sum(wynik_biedron)/wazne) as biedron,
    (100.0 * sum(wynik_bosak)/wazne) as bosak,
    (100.0 * sum(wynik_duda)/wazne) as duda,
    (100.0 * sum(wynik_holownia)/wazne) as holownia,
    (100.0 * sum(wynik_jakubiak)/wazne) as jakubiak,
    (100.0 * sum(wynik_kosiniak)/wazne) as kosiniak,
    (100.0 * sum(wynik_piotrowski)/wazne) as piotrowski,
    (100.0 * sum(wynik_tanajno)/wazne) as tanajno,
    (100.0 * sum(wynik_trzaskowski)/wazne) as trzaskowski,
    (100.0 * sum(wynik_witkowski)/wazne) as witkowski,
    (100.0 * sum(wynik_zoltek)/wazne) as zoltek
from runda1,
    (select sum(glosy_wazne) as wazne
    from runda1);
```
I got result:


|my database    |official result ([source](https://wybory.gov.pl/prezydent20200628/))|
|---------------|---------------|
|43,5023228273371|43,50          |
|30,4620110317439|30,46          |
|13,8653193605736|13,87          |
|6,78136779580412|6,78           |
|2,36475776567495|2,36           |
|2,2245829788509|2,22           |
|0,23380654057028|0,23           |
|0,17322492202588|0,17           |
|0,14367542419746|0,14           |
|0,14048881458843|0,14           |
|0,10844253863339|0,11           |


|my database    |official result|diff|diff [%]|
|---------------|---------------|----|--------|
|8,450,341   |8,450,513   |172 |0.0020  |
|5,917,256   |5,917,340   |84  |0.0014  |
|2,693,343   |2,693,397   |54  |0.0020  |
|1,317,283   |1,317,380   |97  |0.0074  |
|459,355     |459,365     |10  |0.0022  |
|432,126     |432,129     |3   |0.0007  |
|45,417      |45,419      |2   |0.0044  |
|33,649      |33,652      |3   |0.0089  |
|27,909      |27,909      |0   |0.0000  |
|27,290      |27,290      |0   |0.0000  |
|21,065      |21,065      |0   |0.0000  |

so... good enough, I think.