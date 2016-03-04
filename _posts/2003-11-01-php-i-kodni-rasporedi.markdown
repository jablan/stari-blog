---
layout: post
title: PHP i kodni rasporedi
date: '2003-11-01 14:08:09 +0100'
mt_id: 40
post_id: 40
author: mileusna
---
Iako je [PHP](http://www.php.net) moj omiljeni web alat, moram malo da ih kritikujem usled nedostatka kvalitetnih funkcija za konverziju kodnih strana. Naime, želeo sam da RSS na [Naslovima](http://www.naslovi.net) ponudim i u [UTF-8](http://www.utf-8.com/) kodnom rasporedu a ne samo u [Win1250](http://www.microsoft.com/globaldev/reference/sbcs/1250.htm) koji je default za ceo sajt, ali sam nakon desetak minuta traženja shvatio da u PHP-u ne postoji gotovo rešenje za ovakav problem, barem ne za nas programere sa ovih prostora. Da, funkcija [utf8\_encode()](http://yu.php.net/manual/en/function.utf8-encode.php) postoji, ali ona vrši konverziju iz ISO-8859-1 kodne strane u UTF8, ali o Windows1250 ili ISO-8859-2 nema ni govora. Na kraju se neko rešenje putem štapa i kanapa pronašlo, ali ne preterano kvalitetno, pa ako je neko imao sličan problem, zanimaju me vaše ideje. Da li sam ja možda nešto prevideo u PHP dokumentaciji, ili je ipak neophodno da sačekamo novi PHP?!?

