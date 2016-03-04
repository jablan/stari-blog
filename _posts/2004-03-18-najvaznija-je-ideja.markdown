---
layout: post
title: Najvažnija je ideja
date: '2004-03-18 10:25:00 +0100'
mt_id: 76
post_id: 76
author: mileusna
---
Nedavno sam naleteo na [članak](http://www.wired.com/news/business/0,1367,62637,00.html) o servisu [TinyURL](http://www.tinyurl.com), koji vam omogućava da napravite skraćenice za dugačke URL-ove.

Na primer, recimo da želim putem emaila ili neke news grupe da vam prestavim Forbsovu listu najbogatijih ljudi na planeti koja se nalazi na adresi:

    http://www.forbes.com/maserati/billionaires2004/rank.html?passListId=10
    &passYear=2004&passListType=Person&searchParameter1=unset&
    searchParameter2=unset&resultsStart=1&resultsHowMany=25
    &resultsSortProperties=%252Bnumberfield1%252C%252Bstringfield2
    &resultsSortCategoryName=Rank&passKeyword=&category1=category

U velikom broju slučajeva emali klijent bi verovatno dati URL prelomio na više redova, tako da bi bilo nemoguće klikom na adresu otići na dati sajt. Slično je i sa news grupama a o čitkosti i da ne govorimo.

Zato možete otići na TinyURL i od ovog URL-a napraviti kratki URL za redirekciju koji glasi [http://tinyurl.com/yvr7x](http://tinyurl.com/yvr7x), potpunо čitko i trajno, s obzirom da redirekcije ostaju u TinyURL bazi koja do sada sadrži nekih 2 miliona URL-ova.

Sajt trenutno beleži **80 miliona** pregledanih stranica mesečno! Tehničko znanje potrebno za ovakav projekat je minimalno. Sve se može svesti na dva jednostavna skripta, jedan koji upisuje URL-ove u bazu, i drugi skript koji se koristi za samu redirekciju. Krajnje jednostavno, složićete se, samo se trebalo toga setiti.

