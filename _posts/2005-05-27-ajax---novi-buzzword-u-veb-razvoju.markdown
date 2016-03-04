---
layout: post
title: AJAX - novi buzzword u veb razvoju
date: '2005-05-27 11:22:51 +0200'
mt_id: 131
post_id: 131
author: jablan
---
Ako, poput mene, ne pratite sport niti se drogirate reklamama za deterdžente, reč AJAX vam ne znači puno. Sve do skoro, kad je uzeta kao skraćenica za [asinhroni JavaScript i XML](http://www.adaptivepath.com/publications/essays/archives/000385.php) (Asynchronous JavaScript + XML). Ukratko, noviji brauzeri omogućavaju pristup serveru iz javaskripta, bez potrebe za ponovnim učitavanjem cele stranice. Server zatim vraća informaciju koju skript "ugrađuje" na potrebno mesto u stranici.

Najbolji primer za ovo je [Google Suggest](http://www.google.com/webhp?complete=1&hl=en) koji vam, kako kucate string za pretragu, nudi najčešće korišćenje stringove koji počinju onim što ste otkucali. Dakle, na svaki novi otkucani karakter, skript u pozadini šalje zahtev Google-u, ovaj pretraži svoju bazu i vrati listu najkorišćenijih vašem brauzeru. Zatim, [GMail](http://gmail.google.com) koristi isti pristup za minimizaciju saobraćaja sa serverom, pa je odziv aplikacije munjevit. Treba naglasiti i da je Microsoft pre par godina upotrebio AJAX koncept u nekim svojim proizvodima ( [Outlook Web Access](http://www.microsoft.com/exchange/evaluation/clients.mspx), [IE Web Controls](http://www.asp.net/IEWebControls/Download.aspx?tabindex=0&tabid=1))

Očigledno je da ovaj pristup veb razvoju drastično poboljšava performanse sajta i omogućava stvari koje su se dosad sretale samo u svetu desktop aplikacija. No, ono što brine nas programere je koliko je cela stvar laka za izvedbu. Po mom ličnom mišljenju, tu je situacija prilično sumorna... AJAX je, pre svega, kombinacija nekoliko tehnologija i, kao takav, podložniji greškama i zahtevniji za kodiranje. Zatim, zbog nepostojanja adekvatne standardizovane tehnologije i gotovih rešenja, predstavlja potencijalnu zamku za loše programere i projektante; drugim rečima, vrlo je lako napraviti od sopstvenog programa haos nemoguć za debagiranje i održavanje. Takođe, postavlja se pitanje kako bi išla integracija ovog pristupa u postojeće frejmvorke za veb aplikacije, što je frejmvork kompleksniji (tipa ASP.NET), teže je elegantno integrisati asinhroni pristup... Pored svega ovoga, rešenje za asinhroni poziv serveru iz javaskripta još uvek nije standardizovano među proizvođačima brauzera, pa se izrada komplikuje i sa te strane.

Google očigledno nema problema sa kvalitetom i brojem kadra koji zapošljava, poznato je da u svoje redove [prima](http://www.google.com/search?q=google+hires) praktično samo genijalce i proverene gurue. Zato njima verovatno nije problem da prave i održavaju efikasne AJAX aplikacije. Ja se lično ne bih usudio da se previše oslonim na AJAX, barem dok se ne pojave pouzdani Toolkit-ovi koji "mašineriju" cele stvari koliko-toliko sakrivaju od prstiju programera, i dok se AJAX ne počne standardno ugrađivati u veb frejmvorke.

