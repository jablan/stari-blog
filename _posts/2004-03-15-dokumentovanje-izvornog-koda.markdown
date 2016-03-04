---
layout: post
title: Dokumentovanje izvornog koda
date: '2004-03-15 14:41:24 +0100'
mt_id: 73
post_id: 73
author: mileusna
---
Lepa osobina Visual Studia .NET su i XML komentari u zaglavlju metoda i osobina od kojih kasnije možete posebnim alatom napraviti dokumentaciju. Međutim, HTML dokumentacija kreirana na ovaj način putem Visual Studia je pomalo siromašna i nedorečena, kao da su ovaj deo projekta zbrzili zbog roka (ili su se opredelili za outsourcing u Indiju).

Pošto ja nisam jedini koji je to primetio, logično je da su programeri pre mene već došli do rešenja, a ono se zove [NDoc](http://sourceforge.net/projects/ndoc/), open source projekat kojim od vaših XML komentara možete napraviti dokumentaciju u CHM, HTML ili nekom drugom formatu. Krajnje jednostavan za upotrebu i a rezultat je upravo onakav kakav očekujete.

Ukoliko vam je potrebno nešto slično za [PHP](http://www.php.net), preporučio bih [phpDocumentor](http://phpdocu.sourceforge.net/) koji obrađuje komentare pisane u [JavaDOC](http://java.sun.com/j2se/javadoc/) stilu. Na raspolaganju imate direktive tipa @return, @author i sl. koje postavljate u komentare u zaglavljima skriptova i funkcija, od kojih će phpDocumentor napraviti preglednu dokumentaciju i to u formatu koji izaberete, a za HTML postoji i nekoliko templejta, sa frejmovima ili bez njih, pa možete odabrati onaj koji vam se najviše sviđa.

