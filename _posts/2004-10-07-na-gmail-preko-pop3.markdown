---
layout: post
title: Na GMail preko POP3
date: '2004-10-07 15:53:17 +0200'
mt_id: 107
post_id: 107
author: jablan
---
[GMail](http://gmail.google.com/gmail) stvarno jeste najbolji veb mejl koji sam koristio, ima sve što čoveku treba, ali ima jednu ozbiljnu manu - i dalje je veb mejl. To za zapadnjake koji su non-stop na internetu možda i nije veliki problem, ali za nas Balkance zarobljene iza telefonskih centrala iz doba "Otpisanih" bogami jeste. Da bih preko GMail-a poslao duži mejl od kuće, obično moram da poteram editor, natenane sastavim poruku, kopiram na klibord, konektujem se (ovo je složen proces, sastavljen iz beskrajnih okretanja broja provajdera, ručno, jer naravno signal zauzeća modem ne ume da prepozna), otvorim GMail u brauzeru i "nalepim" tekst koji sam pisao. Nije preterano elegantno, je l'? Da ne pominjem to što, bez ponovnog kačenja na net, ne mogu da pretražujem i čitam poruke koje sam slao i primao. Jednom rečju, užas.

Zato mi je primaran e-mail bio i još uvek jeste onaj dobijen od provajdera, sa normalnim POP3 pristupom, sa kojim koristim manje više konforan e-mail klijent koji radi i bez modema na računaru.

Međutim, izgleda da nismo samo mi ovde frustrirani kad moramo da koristimo veb mejl: momci iz ne više susedne Italije napravili su besplatno parče softvera, [FreePOPs](http://freepops.sourceforge.net/en/) koje posreduje između vašeg omiljenog e-mail klijenta i veb mejla na taj način što "glumi" POP3 server, samo na vašoj sopstvenoj mašini, a POP3 zahteve prevodi u HTTP upite kojima skine vaš mejl sa veb mejl servera i vama isti vrati kroz POP3 protokol. Drugim rečima, ovaj koristan komad softvera vam omogućava da iz Calypsa, Outlook Express-a, KMail-a, [Thunderbirda](http://www.mozilla.org/products/thunderbird/) ili bilo kog drugog POP3 klijenta skidate mejl sa GMail-a.

Što je još lepše, program radi na principu plaginova: za novi (ili promenjeni) veb mejl dovoljno je skinuti plagin, i stvar radi. Tako već postoje plagini za GMail, Yahoo, Hotmail i druge popularne veb mejl servise.

Inače, kao jezik za pisanje plaginova, FreePOPs interpretira [LUA](http://www.lua.org/about.html), za one koje mrzi da prate link, "lagani" C-oliki jezik namenjen izgleda baš ovakvim stvarima: makroima za različite aplikacije. Veliko hvala momcima koji stoje iza FreePOPs-a!

