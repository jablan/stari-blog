---
layout: post
title: Zlatna pravila za pisanje Windows aplikacija
date: '2004-01-06 13:49:39 +0100'
mt_id: 54
post_id: 54
author: jablan
---
Ma koliko da ste iskusan programer i ma koliko linija kooda imate iza sebe, vrlo je moguće da (sve vreme) pravite programe sa očajnim korisničkim interfejsom. Programeri, posebno oni sa dugogodišnjim iskustvom u radu sa računarima, jednostavno nisu obični korisnici i teško se mogu staviti u njihov položaj. Sa druge strane, u našim krajevima razvoj softvera je nešto što se ne uči u školama, već stihijski, nesistematično, s kolena na koleno takoreći, pa se dizajn korisničkog interfejsa i koristivost softvera uopšte često zapostavljaju, kao nešto što nije presudno za samu funkcionalnost proizvoda.

Prelistavajući [MSDN](http://msdn.microsoft.com/default.asp), naleteo sam na kratak i jasan [skup pravila](http://msdn.microsoft.com/library/en-us/dnwue/html/ch01f.asp) koje jednostavno _morate_ poštovati da biste pravili aplikacije lake za korišćenje.

Ovde dajem ona pravila koja su, po mom mišljenju, najbitnija, a najčešće se krše:

- Korisnici ne moraju da pročitaju _readme_ fajl pre korišćenja programa
- Aplikacija se povinuje promenama boja koje je korisnik napravio u Control Panel-u
- Aplikacija se može koristiti pomoću tastature, i to koristeći [standardne kombinacije tastera](http://msdn.microsoft.com/library/en-us/dnwue/html/appxb.asp)
- Aplikacija se prilagođava kad korisnik promeni rezoluciju

Pročitajte ovo, pa se setite programa koje ste pisali...

