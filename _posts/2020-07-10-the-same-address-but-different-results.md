---
layout: post
title: 'Polling stations with the same address but different results - round 1'
---

## SQL query

```sql
select symbol_kontrolny, typ_obszaru, numer_obwodu, siedziba, 
wyborcy_uprawnieni, glosy_niewazne + karty_niewazne as niewazne, 
wynik_duda_proc, wynik_trzaskowski_proc, wynik_holownia_proc, wynik_bosak_proc, wynik_kosiniak_proc 
from runda1 where siedziba in (SELECT siedziba FROM runda1 GROUP BY siedziba HAVING COUNT(siedziba)>1) 
order by siedziba;
```

Plus scripts calculating:
* weighted (by percentage result) second Pearson's skew coefficient for results of single candidate in one building (SPSC)
* standard deviation of SPSC for all polling stations in one building
* sum of second Pearson's SPSC for all polling stations in one building

## Results

JSON files (only for 4 candidates with highest results):
* [bosak-took-votes-address.json]({{site.baseurl}}/assets/json/02-skew-bosak-took-votes-address.json)
* [bosak-took-votes.json]({{site.baseurl}}/assets/json/02-skew-bosak-took-votes.json)
* [duda-took-votes-address.json]({{site.baseurl}}/assets/json/02-skew-duda-took-votes-address.json)
* [duda-took-votes.json]({{site.baseurl}}/assets/json/02-skew-duda-took-votes.json)
* [holownia-took-votes-address.json]({{site.baseurl}}/assets/json/02-skew-holownia-took-votes-address.json)
* [holownia-took-votes.json]({{site.baseurl}}/assets/json/02-skew-holownia-took-votes.json)
* [trzaskowski-took-votes-address.json]({{site.baseurl}}/assets/json/02-skew-trzaskowski-took-votes-address.json)
* [trzaskowski-took-votes.json]({{site.baseurl}}/assets/json/02-skew-trzaskowski-took-votes.json)


* [duda-bosak-holownia-trzaskowski-address-unique]({{site.baseurl}}/assets/json/02-skew-took-votes-duda-bosak-holownia-trzaskowski-address-unique.txt)
* [duda-bosak-holownia-trzaskowski-cities-count.txt]({{site.baseurl}}/assets/json/02-skew-took-votes-duda-bosak-holownia-trzaskowski-cities-count.txt)



If you are interested only in addresses of suspicious polling stations you can look at files with "addresses" in name.

Files with name of single candidate show results from suspicious polling stations, where the candidate "took" votes from others - and this fact is highly suspicious for statistical standpoint.

The higher position of in file (closer to the top) the more suspicious polling station is. The closer to the bottom of the file, the least suspicious polling station is.

The only file which contains data in radom order (deliberately) is deliberately [duda-bosak-holownia-trzaskowski-address-unique]({{site.baseurl}}/assets/json/02-skew-took-votes-duda-bosak-holownia-trzaskowski-address-unique.txt)


## Examples from the top of every file

<br/> <br/>
Bosak is "stealing" votes in one of the polling stations in **Liceum Ogólnokształcące nr VII, ul. Jemiołowa 57, 53-426 Wrocław**
![]({{site.baseurl}}/assets/img/one-polling-station-wroclaw-school-57.png)

```json
        "biedron": [
            4.26695842450766,
            5.58951965065502,
            2.45989304812834
        ],
        "bosak": [
            7.65864332603939,
            6.02620087336245,
            16.1497326203209
        ],
        "duda": [
            33.9168490153173,
            30.1310043668122,
            29.7326203208556
        ],
        "holownia": [
            12.800875273523,
            10.0436681222707,
            12.5133689839572
        ],
        "jakubiak": [
            0.218818380743982,
            0.262008733624454,
            0.53475935828877
        ],
        "kosiniak": [
            0.87527352297593,
            2.00873362445415,
            1.49732620320856
        ],
        "piotrowski": [
            0,
            0,
            0
        ],
        "tanajno": [
            0.218818380743982,
            0.349344978165939,
            0
        ],
        "trzaskowski": [
            39.4967177242888,
            44.8034934497817,
            35.8288770053476
        ],
        "witkowski": [
            0.218818380743982,
            0.349344978165939,
            0
        ],
        "zoltek": [
            0.328227571115974,
            0.436681222707424,
            1.28342245989305
        ],

```
<br/> <br/>
Duda is "stealing" votes in one of the polling stations in **Szkoła Podstawowa nr 84, ul. Łukasza Górnickiego 20, 50-337 Wrocław**

![]({{site.baseurl}}/assets/img/one-polling-station-wroclaw-school-84.png)

```sql
        "biedron": [
            2.68292682926829,
            5.94405594405594,
            4.14414414414414
        ],
        "bosak": [
            5.1219512195122,
            7.80885780885781,
            8.1981981981982
        ],
        "duda": [
            62.6829268292683,
            30.0699300699301,
            30.2702702702703
        ],
        "holownia": [
            9.02439024390244,
            14.9184149184149,
            12.3423423423423
        ],
        "jakubiak": [
            0.24390243902439,
            0.466200466200466,
            0.18018018018018
        ],
        "kosiniak": [
            0.24390243902439,
            1.28205128205128,
            1.98198198198198
        ],
        "piotrowski": [
            0.975609756097561,
            0.116550116550117,
            0
        ],
        "tanajno": [
            0,
            0.34965034965035,
            0.18018018018018
        ],
        "trzaskowski": [
            18.7804878048781,
            38.2284382284382,
            41.5315315315315
        ],
        "witkowski": [
            0,
            0,
            0.27027027027027
        ],
        "zoltek": [
            0.24390243902439,
            0.815850815850816,
            0.900900900900901
        ]
```
<br/> <br/>
Holownia is "stealing" votes in one of the polling stations in **Szkoła Podstawowa Nr 27, ul. Podedworze 16, 30-686 Kraków**
![]({{site.baseurl}}/assets/img/one-polling-station-krakow-school-27.png)


```sql
        "biedron": [
            2.02702702702703,
            3.63214837712519,
            3.26666666666667
        ],
        "bosak": [
            7.13213213213213,
            5.17774343122102,
            10.4
        ],
        "duda": [
            35.8858858858859,
            35.548686244204,
            22.6666666666667
        ],
        "holownia": [
            13.963963963964,
            14.2194744976816,
            25.8
        ],
        "jakubiak": [
            0.075075075075075,
            0.154559505409583,
            0.333333333333333
        ],
        "kosiniak": [
            2.02702702702703,
            3.40030911901082,
            3.8
        ],
        "piotrowski": [
            0.15015015015015,
            0,
            0.066666666666667
        ],
        "tanajno": [
            0.075075075075075,
            0,
            0.2
        ],
        "trzaskowski": [
            38.2132132132132,
            37.0170015455951,
            32.9333333333333
        ],
        "witkowski": [
            0.075075075075075,
            0.540958268933539,
            0.133333333333333
        ],
        "zoltek": [
            0.375375375375375,
            0.309119010819165,
            0.4
        ],
```

<br/> <br/>
Trzaskowski is "stealing" votes in one of the polling stations in **Szkoła Podstawowa nr 5, ul. Żwirki i Wigury 1, 87-100 Toruń**
![]({{site.baseurl}}/assets/img/one-polling-station-torun-school-5.png)

```sql
        "biedron": [
            2.04545454545455,
            2.41042345276873,
            2.86561264822134
        ],
        "bosak": [
            3.63636363636364,
            6.18892508143323,
            7.60869565217391
        ],
        "duda": [
            20.4545454545455,
            32.8338762214984,
            30.4347826086957
        ],
        "holownia": [
            16.5909090909091,
            16.2214983713355,
            16.2055335968379
        ],
        "jakubiak": [
            0.227272727272727,
            0,
            0.197628458498024
        ],
        "kosiniak": [
            1.36363636363636,
            1.23778501628665,
            3.06324110671937
        ],
        "piotrowski": [
            0,
            0,
            0
        ],
        "tanajno": [
            0.227272727272727,
            0.260586319218241,
            0
        ],
        "trzaskowski": [
            55.2272727272727,
            40.3908794788274,
            38.9328063241107
        ],
        "witkowski": [
            0,
            0.130293159609121,
            0.296442687747036
        ],
        "zoltek": [
            0.227272727272727,
            0.325732899022801,
            0.395256916996047
        ],
```

<br/> <br/>

And here you can see very nice example when all results from polling stations placed in one building are almost the same. It is possible!

![]({{site.baseurl}}/assets/img/one-polling-station-katowice-mdk-40-111.png)
![]({{site.baseurl}}/assets/img/one-polling-station-warszawa-szkola-366.png)
![]({{site.baseurl}}/assets/img/one-polling-station-rzeszow-szkola-28.png)

Just compare it to one of the suspicious examples

![]({{site.baseurl}}/assets/img/one-polling-station-torun-school-5.png)


<br/> <br/>
If you are interested which cities have most of the "strange" results, here you have:
![]({{site.baseurl}}/assets/img/number-of-suspicious-polling-stations-in-city.png)

## Summary
This analysis is not a proof that results in specific polling station was achieved by cheating. At the time we can't determine which results could happen because of distribution of voters which belongs to specific polling station and which were cheated.

But, it's is better to have some insight into probability of fraud than not having it at all.

There is 27 000 points in Poland where voters can vote, and controlling all of them is beyond discussion. But, taking some effort to control about 400 of them is much more doable. It's only 1.4% off all polling stations. 

Consider that on average single polling point have 700 valid votes, if only 5% of votes were cheated it would be ```400 (suspicious polling stations) x 700 (votes on average in one polling station) x 0.05 (5% cheated votes) = 14 000 votes in whole country```. And this is with assumption that **only** 1.4% of polling stations cheats.

In 2019 The Senate, the upper house of the Polish parliament was "taken" by opposition with only **903 votes** (sic!).

So if you are:
* Duda voter - take care of polling stations from the top of the files:
    * [trzaskowski-took-votes-address.json]({{site.baseurl}}/assets/json/02-skew-trzaskowski-took-votes-address.json)
    * [holownia-took-votes-address.json]({{site.baseurl}}/assets/json/02-skew-holownia-took-votes-address.json)
* Trzaskowski voter - take care of polling stations from the top of the files:
    * [duda-took-votes-address.json]({{site.baseurl}}/assets/json/02-skew-duda-took-votes-address.json)
    * [bosak-took-votes-address.json]({{site.baseurl}}/assets/json/02-skew-bosak-took-votes-address.json)