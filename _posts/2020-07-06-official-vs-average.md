---
layout: post
title: 'Official result vs average result in polling stations - round 1'
---
![results-official-vs-average]({{site.baseurl}}/assets/img/results-official-vs-average.png)
<!--more-->

## SQL queries
Official:
```sql
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
Average:
```sql
select avg(wynik_biedron_proc) as biedron,
    avg(wynik_bosak_proc) as bosak,
    avg(wynik_duda_proc) as duda,
    avg(wynik_holownia_proc) as holownia,
    avg(wynik_jakubiak_proc) as jakubiak,
    avg(wynik_kosiniak_proc) as kosiniak,
    avg(wynik_piotrowski_proc) as piotrowski,
    avg(wynik_tanajno_proc) as tanajno,
    avg(wynik_trzaskowski_proc) as trzaskowski,
    avg(wynik_witkowski_proc) as witkowski,
    avg(wynik_zoltek_proc) as zoltek
from runda1;
```

## Result

|          | biedron | bosak | duda  | holownia | jakubiak | kosiniak | piotrowski | tanajno | trzaskowski | witkowski | zoltek |
|----------|---------|-------|-------|----------|----------|----------|------------|---------|-------------|-----------|--------|
| official | 2.22    | 6.78  | 43.50 | 13.87    | 0.17     | 2.36     | 0.11       | 0.14    | 30.46       | 0.14      | 0.23   |
| avgerage | 2.03    | 6.51  | 48.99 | 12.81    | 0.20     | 2.60     | 0.13       | 0.15    | 26.19       | 0.13      | 0.24   |


![results-official-vs-average]({{site.baseurl}}/assets/img/results-official-vs-average.png)
![results-official-vs-average]({{site.baseurl}}/assets/img/results-official-vs-average-2.png)

## Discussion

Why **Duda, Jakubiak, Kosiniak, Piotrowski, Tanajno, Żółtek** have higher average than official result?

Why **Biedron, Bosak, Holownia, Trzaskowski, Witkowski** have higher official than average?

I don't know.

Why average results could be meaningful, anyway? I don't know.