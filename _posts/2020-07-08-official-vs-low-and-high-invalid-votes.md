---
layout: post
title: 'Official result vs results from polling stations with low and high invalid votes - round 1
 - presidential election, Poland, 2020'
---
![official-vs-low-invalid-vs-high-invalid-votes]({{site.baseurl}}/assets/img/official-vs-low-invalid-vs-high-invalid-votes.png)
<!--more-->

## SQL queries
```sql
select avg(glosy_niewazne_proc) from runda1
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
from (select *
    from runda1
    where glosy_niewazne_proc <= 0.44011970855008),
    (select sum(glosy_wazne) as wazne
    from runda1
    where glosy_niewazne_proc <= 0.44011970855008);
```
And one more query with ">" instead of "<=".

## Results

|           |official|low invalid|low invalid, change|high invalid|high invalid, change|
|-----------|--------|-----------|------------------|------------|-------------------|
|biedron    |2.225   |2.293      |0.069             |1.964       |-0.260             |
|bosak      |6.781   |6.807      |0.025             |6.685       |-0.097             |
|duda       |43.502  |42.047     |-1.455            |49.018      |5.515              |
|holownia   |13.865  |14.083     |0.217             |13.041      |-0.824             |
|jakubiak   |0.173   |0.174      |0.001             |0.170       |-0.003             |
|kosiniak   |2.365   |2.318      |-0.047            |2.543       |0.178              |
|piotrowski |0.108   |0.108      |-0.001            |0.111       |0.002              |
|tanajno    |0.144   |0.143      |0.000             |0.145       |0.001              |
|trzaskowski|30.462  |31.644     |1.182             |25.980      |-4.482             |
|witkowski  |0.140   |0.146      |0.006             |0.119       |-0.022             |
|zoltek     |0.234   |0.236      |0.003             |0.224       |-0.009             |

![official-vs-low-invalid-vs-high-invalid-votes]({{site.baseurl}}/assets/img/official-vs-low-invalid-vs-high-invalid-votes.png)

![official-vs-low-invalid-vs-high-invalid-votes]({{site.baseurl}}/assets/img/official-vs-low-invalid-vs-high-invalid-votes-2.png)

## Discussion

We have two groups:
* for polling stations with low rate of invalid votes
    * **Biedroń, Bosak, Holownia, Jakubiak, Trzaskowski, Witkowski, Żółtek** had better results than official
    * **Duda, Kosiniak, Piotrowski** had worse results than official
* for polling stations with high rate of invalid votes
    * **Duda, Kosiniak, Piotrowski, Tanajno** had better results than official
    * **Biedroń, Bosak, Holownia, Jakubiak, Trzaskowski, Witkowski, Żółtek** had wore results than official

What is the reason of this? Hard to say. Probably there is some corelation between invalid votes and rural areas where Duda and Piotrowski had many voters.

Invalid votes rate for rural areas where Trzaskowski and Holownia had good result should be checked.

But once more we could see **Duda, Kosiniak, Piotrowski** in one group and **Biedroń, Bosak, Holownia, Trzaskowski, Witkowski** in another. Interesting!

One more thing, **Duda, Kosiniak, Piotrowski** have better result in polling stations with high ratio of invalid votes and polling stations with no invalid votes. At the same context **Biedroń, Bosak, Holownia, Trzaskowski, Witkowski** have worse result. Something very interesting is happening here, or I made some mistake somewhere.
