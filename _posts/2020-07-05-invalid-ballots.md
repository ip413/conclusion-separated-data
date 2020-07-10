---
layout: post
title: 'Invalid ballots - round 1'
---

## SQL query
```sql
select symbol_kontrolny, karty_niewazne, siedziba
from runda1
where karty_niewazne > 3
order by karty_niewazne desc;
```


## Result

```
71,"Zespół Szkół Salezjańskich w Poznaniu, os. Bohaterów II Wojny Światowej 29, 61-387 Poznań"
44,"Londyn III, Ambasada RP w Londynie 47 Portland Place London, W1B 1JH, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej"
43,"Londyn II, Ambasada RP w Londynie 47 Portland Place London, W1B 1JH, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej"
43,"Londyn IV, Wydział Konsularny Ambasady RP w Londynie 10 Bouverie Street London, EC4Y 8AX, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej"
40,"Szkoła Podstawowa nr 64 im. Marii Konopnickiej, os. Orła Białego 120, 61-251 Poznań"
39,"LIX Liceum Ogólnokształcące Mistrzostwa Sportowego, S. B. Lindego 20, 01-952 Warszawa"
39,"Poland House 90 Gloucester Place London W1U 6HS, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej"
27,"Liceum Ogólnokształcące, ul. Podwale 16, 68-200 Żary"
27,"Rokietnicki Ośrodek Sportu, ul. Szamotulska 29, 62-090 Rokietnica"
25,"Budynek Ochotniczej Straży Pożarnej, ul. Krakusa 14, 44-321 Marklowice"
24,"XXXIV Liceum Ogólnokształcące im. Krzysztofa Kieślowskiego, ul. Wapienna 17, 91-078 Łódź"
23,"Budynek starej Szkoły Podstawowej w Chorowicach, Chorowice ul. Doboszyńskiego 48, 32-031 Mogilany"
23,"Szkoła Podstawowa Nr 8, ul. Janasa 11, 42-612 Tarnowskie Góry"
22,"Biblioteka Miejska w Łodzi Filia nr 73, ul. Piękna 35/39, 93-558 Łódź"
22,"Londyn V, Wydział Konsularny Ambasady RP w Londynie 10 Bouverie Street London, EC4Y 8AX, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej"
21,"AAI-Polska AIKIDO, ul. Immanuela Kanta 15A, 10-691 Olsztyn"
20,"Urząd Gminy w Suchożebrach, Aleksandry Ogińskiej 11, 08-125 Suchożebry"
20,"Szkoła Podstawowa im. Henryka Sienkiewicza, ul. Polna 40, 05-082 Stare Babice"
19,"Świetlica Wiejska w Goraju, Goraj 24, 66-340 Przytoczna"
19,"Manchester II, Konsulat Generalny RP, 51 Portland Street, Manchester, M1 3LD, Manchester, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej"
18,"Gminny Ośrodek Kultury w Pomiechówku, Jana Kilińskiego 1, 05-180 Pomiechówek"
18,"Republika Irlandii, Dublin, Wydział Konsularny Ambasady RP w Dublinie 4 - 8 Eden Quay Dublin 1, D01 N5W8, Dublin, Irlandia"
17,"Szkoła Podstawowa Nr 5, ul. Chramcówki 27, 34-500 Zakopane"
17,"Monachium I, Konsulat Generalny RP Röntgenstrasse 5 81679 München, Monachium, Republika Federalna Niemiec"
15,"Szkoła Podstawowa Nr 1, ul. Idzikowskiego 2a, 05-070 Sulejówek"
15,"Szkoła Podstawowa Nr 70 z Oddziałami Integracyjnymi im. Bohaterów Monte Cassino, ul. G. Bruna 11, 02-594 Warszawa"
15,"Moniecki Ośrodek Kultury w Mońkach, ul. Białostocka 25, 19-100 Mońki"
14,"Kolonia II, Konsulat Generalny RP Im Media Park 5 C 50670 Köln, Kolonia, Republika Federalna Niemiec"
14,"Zespół Szkolno-Przedszkolny Nr 2 - Publiczna Szkoła Podstawowa Nr 16, ul. Zofii Nałkowskiej 16, 45-558 Opole"
13,"Szkoła Podstawowa w Wilkołazie Pierwszym, Wilkołaz Pierwszy 7, 23-212 Wilkołaz"
13,"Monachium II, Konsulat Generalny RP Röntgenstrasse 5 81679 München, Monachium, Republika Federalna Niemiec"
13,"Kino Morena, ul. Przybrzeżna 1, 73-140 Ińsko"
```
More data here [{{site.baseurl}}/assets/sqlcsv/01-invalid-ballots.csv]({{site.baseurl}}/assets/sqlcsv/01-invalid-ballots.csv)
## Discussion

Because everyone is able to put into ballot box whatever he want... I think co conclusion could be made about this aspect. Maybe analysis about how many ballots were given to people and how many were pulled out from the box could answer some questions here.