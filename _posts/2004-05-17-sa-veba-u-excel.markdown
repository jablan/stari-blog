---
layout: post
title: Sa veba u Excel
date: '2004-05-17 10:42:57 +0200'
mt_id: 91
post_id: 91
author: jablan
---
MS Excel danas predstavlja najkorišćeniji program za tabelarne kalkulacije (spreadsheet). Iako je prosečan, pa i natprosečan korisnik sasvim zadovoljan skupom funkcionalnosti koji je nudio još pre par verzija (već Office 6 mi pada na pamet kao prilično moćan skup alata). Međutim, Excel od verzije XP (2002 ili 9, svejedno kako je ko zove) ima jednu praktičnu osobinu, ne toliko vidljivu običnim korisnicima ali izuzetno zgodnu za nas programere: Excel čita XML, to jest poseban XML dijalekt pod imenom XML spreadsheet (XMLSS).

I sad nebitno da li ste ASP, .NET, PHP, JSP, Python programer, imate mogućnost da ponudite korisnicima kulturno formatiran Excel izlaz. Kombinacija XML-a koga "ume" da vrati baza podataka (a ni da ga pravite ručno od rezultata upita nije neki veći problem) i XSL transformacije koji ovaj rezultat prevodi u Excel kompatibilan svodi neophodan kood (ne računajući XSL) na par linija. XSL možete praviti od nule, koristeći Majkrosoftov [opis](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dnexcl2k2/html/odc_xmlss.asp) Excel-razumljivih nejmspejsova (namespace), ili napraviti templejt u Excelu, eksportovati u XML i od tog XML-a napraviti XSL.

Ne zaboravite da pre slanja generisanog XML-a korisniku pošaljete HTTP header [Content-type](http://www.faqs.org/rfcs/rfc1521.html) "application/vnd.ms-excel" koji će klijentskom brauzeru reći da je u pitanju Excel fajl, kao i header [Content-disposition](http://www.faqs.org/rfcs/rfc1806.html) pomoću koga možete regulisati to da li će se tabela automatski otvoriti u Excel-u, ili biti ponuđena korisniku za snimanje na disk, kao i podrazumevano ime pod kojim će fajl biti snimljen.

