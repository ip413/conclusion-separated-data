---
layout: post
title: 'Polling stations with the same address and high and low standard deviation and skew in results - round 1'
---

{{site.url}}


## SQL query

```sql
select symbol_kontrolny, typ_obszaru, numer_obwodu, siedziba, wyborcy_uprawnieni, glosy_niewazne + karty_niewazne as niewazne, wynik_duda_proc, wynik_trzaskowski_proc, wynik_holownia_proc, wynik_bosak_proc, wynik_kosiniak_proc 
from runda1 where siedziba in (SELECT siedziba FROM runda1 GROUP BY siedziba HAVING COUNT(siedziba)>1) 
order by siedziba;
```

Plus node scripts calculating standard deviation, Pearson's second skewness coefficient.

## Results and discussion

Eight files: 
* [{{site.baseurl}}/assets/json/02-skew-standard-deviation-address-asc.json]({{site.baseurl}}/assets/json/02-skew-standard-deviation-address-asc.json) 
* [{{site.baseurl}}/assets/json/02-skew-standard-deviation-address-desc.json]({{site.baseurl}}/assets/json/02-skew-standard-deviation-address-desc.json) 
* [{{site.baseurl}}/assets/json/02-skew-standard-deviation-asc.json]({{site.baseurl}}/assets/json/02-skew-standard-deviation-asc.json) 
* [{{site.baseurl}}/assets/json/02-skew-standard-deviation-desc.json]({{site.baseurl}}/assets/json/02-skew-standard-deviation-desc.json) 
* [{{site.baseurl}}/assets/json/02-standard-deviation-address-asc.json]({{site.baseurl}}/assets/json/02-standard-deviation-address-asc.json) 
* [{{site.baseurl}}/assets/json/02-standard-deviation-address-desc.json]({{site.baseurl}}/assets/json/02-standard-deviation-address-desc.json) 
* [{{site.baseurl}}/assets/json/02-standard-deviation-asc.json]({{site.baseurl}}/assets/json/02-standard-deviation-asc.json) 
* [{{site.baseurl}}/assets/json/02-standard-deviation-desc.json]({{site.baseurl}}/assets/json/02-standard-deviation-desc.json)

Files with "skew" in name are using using Pearson's second skewness coefficient but are sorted by standard deviation of skew for all voting points at the same address.

Files with "desc" should contain the most different results at the top. "Asc" the least different. Since skew works for three or more values, all "skew" files contains at least three voting points at the same address.

If you want to look for suspicious polling stations you should look at files with "desc" in name and search from the top - the higher position in file, the more suspicious polling station, at least form standard deviation's point of view.

If you are interested only in addresses of suspicious polling stations you can look at files with "addresses" in name.

Some sample from the top of the [{{site.baseurl}}/assets/json/02-skew-standard-deviation-desc.json]({{site.baseurl}}/assets/json/02-skew-standard-deviation-desc.json) file:

```json
        "biedron": [
            1.6726403823178,
            1.54711673699015,
            2.95774647887324,
            1.68269230769231
        ],
        "bosak": [
            9.08004778972521,
            8.15752461322082,
            9.01408450704225,
            8.29326923076923
        ],
        "duda": [
            49.1039426523298,
            35.5836849507736,
            40.4225352112676,
            40.5048076923077
        ],
        "holownia": [
            19.9522102747909,
            25.5977496483826,
            22.9577464788732,
            23.1971153846154
        ],
        "jakubiak": [
            0.2389486260454,
            0.281293952180028,
            0.422535211267606,
            0.240384615384615
        ],
        "kosiniak": [
            1.0752688172043,
            0.843881856540084,
            1.40845070422535,
            0.721153846153846
        ],
        "piotrowski": [
            0.1194743130227,
            0.140646976090014,
            0,
            0
        ],
        "tanajno": [
            0.3584229390681,
            0,
            0,
            0
        ],
        "trzaskowski": [
            18.2795698924731,
            27.7074542897328,
            22.2535211267606,
            25
        ],
        "witkowski": [
            0,
            0,
            0.28169014084507,
            0.240384615384615
        ],
        "zoltek": [
            0.1194743130227,
            0.140646976090014,
            0.28169014084507,
            0.120192307692308
        ],
```

It looks like someone took 10 pp from **Trzaskowski** and put it into **Duda** result. Why all polling stations at the same address have the same result except one? All stations are placed in one building! Of course, it could be coincidence. But I don't think so.

These are the other examples:

Address: Zespół Szkolno-Przedszkolny Nr 5, ul. Magnoliowa 13, 15-669 Białystok ![Zespół Szkolno-Przedszkolny Nr 5, ul. Magnoliowa 13, 15-669 Białystok]({{site.baseurl}}/assets/img/one-polling-station-bialystok-school-5.png)

Address: Szkoła Podstawowa nr 30 im. Króla Kazimierza Wielkiego, ul. Nałkowskich 110, 20-470 Lublin ![Szkoła Podstawowa nr 30 im. Króla Kazimierza Wielkiego, ul. Nałkowskich 110, 20-470 Lublin]({{site.baseurl}}/assets/img/one-polling-station-lublin-school-30.png)

And this is show it should like for polling stations with hundreds of votes.

Address: Szkoła Podstawowa Nr 357, ul. Zachodzącego Słońca 25, 01-495 Warszawa ![Szkoła Podstawowa Nr 357, ul. Zachodzącego Słońca 25, 01-495 Warszawa]({{site.baseurl}}/assets/img/one-polling-station-warsaw-school-357.png)
