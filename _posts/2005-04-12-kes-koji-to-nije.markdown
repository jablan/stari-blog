---
layout: post
title: Keš koji to nije...
date: '2005-04-12 16:27:35 +0200'
mt_id: 123
post_id: 123
author: jablan
---
Jedan post takoreći pro forme, čisto da korisnici vide da sam i ja živ (za mileusnu ne treba ni postavljati pitanje, vidi se iz postova da je alive & kickin')...

Ovako, pre nekog vremena u projektu na kome radim (ASP.NET) pojavila se potreba za kešom koji [System.Web.Caching.Cache](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfsystemwebcachingcacheclasstopic.asp) klasa nije mogla da zadovolji - ukratko, u pitanju je keširanje na veb farmama - pošto taj keš koristi lokalnu memoriju kao ostavu (repository), stvar se komplikuje ako se na jednom od servera objekat koji se kešira promeni, pa ta promena treba da se odrazi i na ostalim serverima. Očigledno, server na kome se objekat promenio treba da "obavesti" ostale servere da objekat koji oni drže u kešu više nije validan.

Problem se može zaobići korišćenjem [Microsoft Caching Application Block-a](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dnpag2/html/caching1.asp), koji može da čuva keširane objekte i u SQL bazi. U tom slučaju, koristila bi se centralizovana baza za keširanje, te ne bi ni bilo potrebe za invalidacijom promenjenih objekata na ostalim serverima.

Dakle, prešli smo na korišćenje Application Block-a. No, ne lezi vraže, primeto sam da se klasa za keširanje, čak i kad se objekti nalaze u kešu, ponaša kao da ih nema, to jest sve vreme ih nanovo povlači iz baze... Nakon par sati razbijanja glave i guglovanja, zahvaljujući [jednom sapatniku](http://objectsharp.com/Blogs/bruce/archive/2004/10/26/978.aspx) sa istim problemom, našao sam problem: primer konfiguracije (uzgred, jako slabo dokumentovan) keša koji dolazi uz Application Block, podešen je da u kešu čuva samo 5 (!) objekata. Uz drugu direktivu da se stalno održava slobodno 20% keša, blok je keširao svega 2-3 objekta. Jednostavna promena setovanja u web.config fajlu rešila je problem...

Naravoučenije je da se ne oslanjate potpuno na gotova rešenja, čak ni kad dolaze iz renomiranih kuhinja, poput Majkrosoftove.

