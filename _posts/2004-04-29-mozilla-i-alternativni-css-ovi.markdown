---
layout: post
title: Mozilla i alternativni CSS-ovi
date: '2004-04-29 11:50:35 +0200'
mt_id: 89
post_id: 89
author: jablan
---
Posle višegodišnje vernosti [Operi](http://www.opera.com), rešio sam da isprobam Mozillu, tačnije [Firefox](http://www.mozilla.org/products/firefox/), i - tu ostao (ne računam korišćenje IE za potrebe firme). Firefox stvarno ima sve što i Opera i prilično više; neću da elaboriram ovde, ima dosta informacija na netu, istakao bih samo sistem [ekstenzija](http://texturizer.net/firefox/extensions/) kojih, zahvaljujući open-source koncepciji, ima pregršt, za sve i svašta. RSS agregator naprimer, koga sam odmah instalirao. Proces instalacije ekstenzija, tema i [plugin-ova za pretragu](http://mycroft.mozdev.org/download.html) je neverovatno lak, ne uključuje nikakvo (ručno) pokretanje izvršnih programa i kopiranje fajlova, brauzer sve radi sam.

Zadržao bih se međutim malo više na alternativnim stylesheet-ovima. Za neupućene, W3C standard [predviđa](http://www.w3.org/TR/REC-html40/present/styles.html) mogućnost da se na jednoj veb stranici navedu linkovi ka više CSS fajlova, od kojih će u jednom trenutku aktivan biti samo jedan. Na ovaj način, uz kulturno korišćenje stilova, može se za isti sadržaj ponuditi nekoliko različitih rešenja za dizajn (recimo, različite kolor šeme ili verzija sa većim fontovima za slabovide korisnike). Mozilla, nakon pristupanja ovakvoj stranici, daje korisniku mogućnost da odabere onaj CSS koji mu najviše odgovara.

Nažalost, problem ovakvog definisanja različitih načina prikazivanja je u tome što ne postoji (barem koliko ja znam) način da se odabrani CSS "upamti" i koristi kod ponovnih pristupa ovoj strani ili stranama na istom sajtu. Razlog je taj što se alternativni CSS-ovi nude na jednoj stranici i pristupom nekoj drugoj stranici na istom sajtu (ili čak istoj stranici sa različitim parametrima) server može poslati sasvim drugi set alternativnih stilova.

[Rešenje postoji](http://www.alistapart.com/articles/alternate/), ali se nažalost svodi na Java Script i kukije, što onda dovodi u pitanje i samu potrebu za postojanje alternativnih stilova u HTML standardu.

