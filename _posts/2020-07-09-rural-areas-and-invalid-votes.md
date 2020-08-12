---
layout: post
title: Percentage of invalid votes when candidate had result above official, rural and urban areas - round 1 - presidential election, Poland, 2020
---
![invalid-votes-result-above-official-urban]({{site.baseurl}}/assets/img/invalid-votes-result-above-official-urban.png)
<!--more-->

## SQL queries
```sql
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_biedron_proc > 2.2245829788509;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_bosak_proc > 6.78136779580412;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_duda_proc > 43.5023228273371;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_holownia_proc > 13.8653193605736;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_jakubiak_proc > 0.173224922025876;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_kosiniak_proc > 2.36475776567495;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_piotrowski_proc > 0.108442538633394;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_tanajno_proc > 0.143675424197456;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_trzaskowski_proc > 30.4620110317439;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_witkowski_proc > 0.140488814588433;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="wieś" and wynik_zoltek_proc > 0.233806540570276;


select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_biedron_proc > 2.2245829788509;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_bosak_proc > 6.78136779580412;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_duda_proc > 43.5023228273371;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_holownia_proc > 13.8653193605736;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_jakubiak_proc > 0.173224922025876;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_kosiniak_proc > 2.36475776567495;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_piotrowski_proc > 0.108442538633394;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_tanajno_proc > 0.143675424197456;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_trzaskowski_proc > 30.4620110317439;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_witkowski_proc > 0.140488814588433;
select avg(glosy_niewazne_proc) from runda1 where typ_obszaru="miasto" and wynik_zoltek_proc > 0.233806540570276;
```

## Result

![invalid-votes-result-above-official-rural]({{site.baseurl}}/assets/img/invalid-votes-result-above-official-rural.png)
![invalid-votes-result-above-official-urban]({{site.baseurl}}/assets/img/invalid-votes-result-above-official-urban.png)

## Discussion

Mr. Bierdon... shame on you! :)

Once again we could see two groups **Duda, Kosianiak, Piotrowski, Jakubiak** and **Bosak, Holownia, Trzaskowski, Witkowski, Tantajno**.

The better result of any of them **Duda, Kosianiak, Piotrowski, Jakubiak**, the more invalid votes.

The better result any of them **Bosak, Holownia, Trzaskowski, Witkowski, Tantajno**, the less invalid votes.

Differences between groups, once more are not big, but significant. If we assume that in some polling stations some ballot cards were manipulated deliberately, there could also occurs other anomalies.
