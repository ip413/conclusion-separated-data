---
layout: post
title: Official result vs results from polling stations with all votes and ballots valid - round 1
---

## SQL queries
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
from (select *
    from runda1
    where glosy_niewazne = 0 and karty_niewazne = 0 ),
    (select sum(glosy_wazne) as wazne
    from runda1
    where glosy_niewazne = 0 and karty_niewazne = 0);
```

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

## Result

| ------    | biedron | bosak | duda  | holownia | jakubiak | kosiniak | piotrowski | tanajno | trzaskowski | witkowski | zoltek |
|-----------|---------|-------|-------|----------|----------|----------|------------|---------|-------------|-----------|--------|
| official  | 2.22    | 6.78  | 43.50 | 13.87    | 0.17     | 2.36     | 0.11       | 0.14    | 30.46       | 0.14      | 0.23   |
| all valid | 2.02    | 6.75  | 47.26 | 13.30    | 0.17     | 2.57     | 0.11       | 0.14    | 27.32       | 0.12      | 0.22   |

![]({{site.baseurl}}/assets/img/results-official-vs-polling-stations-with-all-votes-valid.png)
![]({{site.baseurl}}/assets/img/results-official-vs-polling-stations-with-all-votes-valid-2.png)

## Discussion

If we take votes only from polling stations with all votes valid, then **Duda, Kosiniak, Piotrowski** whould have higher resutls than official.
On the other hand **Biedron, Bosak, Holownia, Trzaskowski, Witkowski, Żółtek** would have lower results, if we took votes only from polling stations without single invalid vote or ballot.

And again we have similar situation, for some reason **Duda, Kosiniak, Piotrowski** are in one group, and **Biedron, Bosak, Holownia, Trzaskowski, Witkowski** in another.

Maybe if something looks too good to be true (no invalid votes or ballots) it's not true?
Maybe it's somehow related to Abranham Wald work in Statistical Research Group (SRG) during WWII ([link](https://medium.com/@penguinpress/an-excerpt-from-how-not-to-be-wrong-by-jordan-ellenberg-664e708cfc3d
))? I don't know!
