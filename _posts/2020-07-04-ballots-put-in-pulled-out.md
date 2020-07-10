---
layout: post
title: 'Difference between votes from envelopes put in ballot box and pulled out - round 1'
---

## SQL query
```sql
select symbol_kontrolny, koperty_wrzucone_do_urny, karty_z_kopert, karty_z_kopert - koperty_wrzucone_do_urny as roznica_glosy_z_kopert, siedziba 
from runda1 where koperty_wrzucone_do_urny <> karty_z_kopert 
order by (koperty_wrzucone_do_urny - karty_z_kopert) desc
```

## Results
```csv
-125    Haga II, Ambasada RP (dawny WPHI) Van Lennepweg 51 2597 LG Den Haag, Haga, Królestwo Niderlandów
-92 Londyn V, Wydział Konsularny Ambasady RP w Londynie 10 Bouverie Street London, EC4Y 8AX, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej
-38 Nowy Jork II, Konsulat Generalny RP 233 Madison Avenue (Jan Karski Corner) New York, NY 10016, Nowy Jork, Stany Zjednoczone Ameryki
-28 Zespół Szkół Odzieżowych Nr 1, ul. Cechowa 57, 30-614 Kraków
-20 Republika Irlandii, Dublin, Wydział Konsularny Ambasady RP w Dublinie 4 - 8 Eden Quay Dublin 1, D01 N5W8, Dublin, Irlandia
-16 Szkoła Podstawowa Nr 124, ul. Weigla 2, 30-898 Kraków
-7  Przedszkole nr 267, ul. Witolda Małcużyńskiego 4, 02-793 Warszawa
-5  Republika Irlandii, Dublin, Rezydencja Ambasadora RP 12 Ailesbury Road, Ballsbridge Dublin 4, D04 C659, Dublin, Irlandia
-5  Berlin I, Ambasada RP Lassenstraße 19 – 21 14193 Berlin, Berlin, Republika Federalna Niemiec
-5  Berlin III, Ambasada RP Lassenstraße 19 – 21 14193 Berlin, Berlin, Republika Federalna Niemiec
-5  Dom Kultury w Szówsku, Szówsko ul. Sportowa 5, 37-522 Wiązownica
-4  Los Angeles, Konsulat Generalny RP 12400 Wilshire Blvd, Suite 555 Los Angeles, CA 90025, Los Angeles, Stany Zjednoczone Ameryki
-4  Belfast, Konsulat Generalny RP 67 Malone Road Belfast, BT9 6SB, Belfast, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej
-4  Poland House 90 Gloucester Place London W1U 6HS, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej
-3  Hamburg III, Konsulat Generalny RP Gründgensstraße 20 22309 Hamburg, Hamburg, Republika Federalna Niemiec
-3  Berlin IV, Ambasada RP Lassenstraße 19 – 21 14193 Berlin, Berlin, Republika Federalna Niemiec
-3  Szkoła Podstawowa Nr 2, ul. Misiągiewicza 10, 37-200 Przeworsk
-3  Zespół Szkolno-Przedszkolny Nr 4, ul. Powstańców Warszawskich 42, 42-680 Tarnowskie Góry
-2  Szkoła Podstawowa Nr 4 w Myślenicach, ul. Zdrojowa 14, 32-400 Myślenice
-2  Szkoła Podstawowa nr 323, ul. Ludwika Hirszfelda 11, 02-776 Warszawa
-2  Bruksela, Wydział Konsularny Ambasady RP Rue des Francs 28 1040 Bruxelles, Bruksela, Królestwo Belgii
-2  Kopenhaga, Ambasada RP Richelieus Allé 12 2900 Hellerup, Kopenhaga, Królestwo Danii
-2  Kanada, Vancouver, Konsulat Generalny RP 1177 West Hastings Street, Suite 1600, Vancouver, BC V6E 2K3, Vancouver, Kanada
-2  Szkoła Podstawowa im. Św. Jana Kantego w Grzegorzówce, Grzegorzówka 173, 36-025 Dylągówka
-2  Biuro Nadleśnictwa, ul. Kopytko 13, 43-300 Bielsko-Biała
-2  Miejski Dom Kultury Filia Nr 2, Świnoujście, Warszów Sosnowa 18, 72-602 Świnoujście
-1  Liceum Ogólnokształcące nr VII, ul. Krucza 49, 53-410 Wrocław
-1  Liceum Ogólnokształcące nr XIII, ul. gen. Józefa Haukego-Bosaka 33 - 37, 50-447 Wrocław
-1  Szkoła Podstawowa nr 33, ul. Kolista 17, 54-152 Wrocław
-1  Szkoła Podstawowa nr 44, ul. Wilanowska 31, 51-206 Wrocław
-1  Ośrodek Pomocy Społecznej w Skwierzynie, ul. Stefana Batorego 15, 66-440 Skwierzyna
-1  Miejski Ośrodek Sportu i Rekreacji Hala Akrobatyczna, ul. Urszuli 22, 65-147 Zielona Góra
-1  Samorządowe Przedszkole w Sulejowie, ul. Konecka 29, 97-330 Sulejów
-1  Oświęcimskie Centrum Kultury, ul. Jędrzeja Śniadeckiego 24, 32-600 Oświęcim
-1  XIII Liceum Ogólnokształcące, ul. Sądowa 4, 31-542 Kraków
-1  Zespół Szkolno-Przedszkolny Nr 7, ul. Skotnicka 86, 30-394 Kraków
-1  Zespół Szkolno-Przedszkolny Nr 5, os. Oświecenia 30, 31-636 Kraków
-1  Państwowa Wyższa Szkoła Zawodowa, ul. Chruślicka 6, 33-300 Nowy Sącz
-1  Publiczna Szkoła Podstawowa Nr 1 w Kozienicach, ul. Tadeusza Kościuszki 1, 26-900 Kozienice
-1  Szkoła Podstawowa Nr 1, ul. Ostrowska 58, 07-320 Małkinia Górna
-1  Samorządowe Przedszkole w Jabłonnie Lackiej, ul. Kubusia Puchatka 1, 08-304 Jabłonna Lacka
-1  S. B. M. "WARDOM", J. Kochanowskiego 49, 01-864 Warszawa
-1  Klub WSBM "Chomiczówka", P. Nerudy 1, 01-926 Warszawa
-1  Praga, Wydział Konsularny Ambasady RP Truhlářská 13 - 15 110 00 Praha 1, Praga, Republika Czeska
-1  Kolonia II, Konsulat Generalny RP Im Media Park 5 C 50670 Köln, Kolonia, Republika Federalna Niemiec
-1  Kolonia III, Konsulat Generalny RP Im Media Park 5 C 50670 Köln, Kolonia, Republika Federalna Niemiec
-1  Oslo I, Ambasada RP Olav Kyrres plass 1 0244 Oslo, Oslo, Królestwo Norwegii
-1  Chicago II, Konsulat Generalny RP 1530 N Lake Shore Drive Chicago, IL 60610, Chicago, Stany Zjednoczone Ameryki
-1  Publiczna Szkoła Podstawowa w Pilźnie, ul. Adama Mickiewicza 1, 39-220 Pilzno
-1  Zespół Szkolno-Przedszkolny, Siemianice ul. Słupska 42, 76-200 Słupsk
-1  Przedsiębiorstwo Wodociągów i Kanalizacji, ul. Witomińska 29, 81-311 Gdynia
-1  Zespół Szkolno-Przedszkolny nr 4, ul. Chwaszczyńska 26, 81-571 Gdynia
-1  Szkoła Podstawowa nr 2 im. Tadeusza Kościuszki, ul. Henryka Pobożnego 2, 76-200 Słupsk
-1  Szkoła Podstawowa Nr 7, ul. Ławczana 12, 43-600 Jaworzno
-1  Szkoła Podstawowa nr 36, ul. Iłłakowiczówny 13, 40-134 Katowice
-1  Świetlica wiejska, Łęgno 18, 11-040 Dobre Miasto
-1  Szkoła Podstawowa Nr 3 im. Powstańców Wielkopolskich, ul. Jana Kochanowskiego 1, 64-800 Chodzież
-1  Szkoła Podstawowa im. Jana Pawła II w Mroczeniu, Szkoła Filialna w Grębaninie, Grębanin 87, 63-604 Baranów
-1  Zespół Szkół i Placówek Oświatowych w Lubiniu, Lubiń ul. Powstańców 23, 64-010 Krzywiń
-1  Gminny Ośrodek Kultury, ul. Sienkiewicza 3, 63-020 Zaniemyśl
-1  Szkoła Podstawowa Nr 5 im. Polskich Noblistów w Śremie, ul. Dezyderego Chłapowskiego 12A, 63-100 Śrem
-1  Liceum Ogólnokształcące Mistrzostwa Sportowego im. Poznańskich Olimpijczyków, os. Tysiąclecia 43, 61-255 Poznań
-1  Szkoła Podstawowa Nr 35, ul. Świętoborzyców 40 (Hala Sportowa), 71-665 Szczecin
1   Zespół Szkół Ponadpodstawowych im. Tadeusza Kościuszki w Kamieńsku (sala gimnastyczna), ul. Szkolna 4, 97-360 Kamieńsk
1   Zespół Szkół Ogólnokształcących Nr 18, ul. Senatorska 35, 30-106 Kraków
1   Szkoła Podstawowa Nr 4, Grodzisk Mazowiecki, Łąki ul. Zielony Rynek 2, 05-825 Grodzisk Mazowiecki
1   Szkoła Podstawowa Nr 321, ul. ppłk W. Szadkowskiego 3, 01-493 Warszawa
1   LXVIII Liceum Ogólnokształcące im. Tytusa Chałubińskiego, ul. L. Narbutta 65/71, 02-524 Warszawa
1   Szkoła Podstawowa nr 215, ul. Kwatery Głównej 13, 04-330 Warszawa
1   Sydney, Konsulat Generalny RP 10 Trelawney St. Woollahra, 2025 NSW, Sydney, Związek Australijski
1   Kolonia V, Konsulat Generalny RP Im Media Park 5 C 50670 Köln, Kolonia, Republika Federalna Niemiec
1   Uniwersytet Rzeszowski, al. Rejtana 16c, 35-310 Rzeszów
1   Szkoła Podstawowa Nr 45, ul. Łagodna 10, 15-757 Białystok
1   Urząd Gminy (Sala Posiedzeń), ul. Lipowska 730, 43-374 Buczkowice
1   Publiczna Szkoła Podstawowa Nr 9, ul. Niewiadoma 19, 27-400 Ostrowiec Świętokrzyski
1   Szkoła Podstawowa nr 2 w Kórniku, ul. Armii Krajowej 11, 62-035 Kórnik
1   Szkoła Podstawowa nr 25 z Oddziałami Integracyjnymi i Specjalnymi, ul. Ignacego Prądzyńskiego 53, 61-527 Poznań
2   Szkoła Podstawowa Nr 53, ul. Skośna 8, 30-383 Kraków
2   Szkoła Podstawowa Nr 103, os. Kolorowe 29, 31-941 Kraków
2   Integracyjne Centrum Dydaktyczno-Sportowe, ul. Staszica 2, 05-092 Łomianki
2   Szkoła Podstawowa im. Jana Pawła II w Łopusznie, ul. Strażacka 5, 26-070 Łopuszno
2   Szkoła Podstawowa w Kuźni, Kuźnia 36, 63-313 Chocz
3   Budynek Ochotniczej Straży Pożarnej, ul. Krakusa 14, 44-321 Marklowice
3   Szkoła Podstawowa Nr 2 im. „Ewarysta Estkowskiego”, ul. Wrocławska 51, 63-400 Ostrów Wielkopolski
7   Londyn III, Ambasada RP w Londynie 47 Portland Place London, W1B 1JH, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej
8   Zespół Szkół Zawodowych Huty im. T. Sendzimira, os. Złotej Jesieni 2, 31-826 Kraków
17  Londyn I, Ambasada RP w Londynie 47 Portland Place London, W1B 1JH, Londyn, Zjednoczone Królestwo Wielkiej Brytanii i Irlandii Północnej
```

## Discussion

Why more ballots were pulled out from ballot box in Londyn I, Ambasada RP w Londynie 47 Portland Place London than it was put in? I don't know!

Why 125 votes were missing in Haga II, Ambasada RP (dawny WPHI) Van Lennepweg 51? I don't know!

Why 87 polling stations had problems with with putting in and pulling out the same amount of votes from envelopes? Maybe some envelopes "with" votes were empty? Maybe some envelopes had more votes than one? Indeed, interesting! Even fascinating.