---
layout: post
title: Novi Naslovi.net
date: '2005-06-04 03:23:20 +0200'
mt_id: 132
post_id: 132
author: mileusna
---
![](http://naslovi.net/images/naslovi_logo_123.gif)Približava se druga godišnjica postojanja sajta [Naslovi.net](http://naslovi.net) i eto konačno je došlo do nekih većih promena na sajtu. Pa da krenemo redom.

Interno, ceo softver je većim delom prerađen i sada radi na mnogo višem nivou nego pre tako da je iz ažuriranje same baze totalno isključen ljudski udeo. Može da obradi i sajtove koji su pisani na ćirlici kao Politika, ažuriranje obavlja cron job periodično tako da su Naslovi.net uvek ažurni sa najnovijim vestima sa sajtova B92 i RTS. Podaci u bazi se skladište u UTF-8 kodnom rasporedu što je takođe razlika od starog sistema.

Novi softver povukao je sa sobom i izmene samog sajta najviše zbog toga da bi dnevne vesti koje pristižu tokom dana bile istaknute u prvi plan kako bi posetioci uvek videli da su vesti na naslovima ažurne i kako bi ponovo došli. Kompletan dizajn urađen je u trendu CSS-a korišćenjem stilova i mase DIVova umesto tabela. Ne toliko zbog mode koliko zbog efikasnosti. Naime, IE div elemente renderuje odmah nakon učitavanja za razliku od tabela koje renderuje tek kada učita sadržaj cele tabele. Sa ovakvim dizajnom, korisnici sa sporijom vezom imaju osećaj da se strana brže učitava, odnosno odmah imaju uvid u deo strane koji je IE svukao sa neta. Naravno tu je i ušteda u samoj količini HTML koda i CSS datoteka koje browseri najčešće keširaju tako da i to utiče na brzinu. I dalje mi ovaj novi način dizajna ide pomalo na živce jer ne mogu da odradim neke stvari koje su se sa tabelama jednostavno rešavale, ali uz par Java skriptova sve dođe na svoje mesto.

[Stari naslovi](http://64.37.86.111/) jesu koristili tabele, ali da bih zaobišao ovaj problem tada nisam koristio klasičan način korišćenja jedne velike tabele u kojoj se ispisuje skoro cela strana sto je čest način rada, već više manjih tabela, tako da su i stari naslovi imali zavidnu brzinu učitavanja i prikazivanja stranica.

Pored toga, par novih servisa kao što su [vremenska prognoza](http://naslovi.net/vreme), kursna lista i Google pretraga, pomeraju sajt malo više ka portalu i mestu odakle možete započeti svakodnevni surf.

Sistem nije mali a programer je samo jedan (i to prezauzet) tako da se još dosta stvari radi. Vremenom je svašta na brzaka natrpano na njega pa sada neke stvari želim da malo bolje napišem. Želim malo da promenim način pretrage, generisanje RSS-a, korisnike ePress klipinga treba prebaciti na novi server itd. Kad sve to legne kako treba, onda ću se možda opet posvetiti kvalitetu servisa, boljem algoritam za pretragu koji bi u obzir uzimao padeže, boljem povezivanju vesti, kategorizaciji itd.

