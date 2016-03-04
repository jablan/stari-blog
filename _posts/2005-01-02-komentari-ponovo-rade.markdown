---
layout: post
title: Komentari ponovo rade
date: '2005-01-02 08:42:50 +0100'
mt_id: 115
post_id: 115
author: jablan
---
Kao prvo, svim posetiocima radionice želim srećnu novu 2005. godinu, u njoj dovoljno para, manje bagova u koodu i manje sati provedenih za računarom, a više sa bližnjima.

Komentari na radionici su ponovo omogućeni. Pre toga sam ručno iz baze obrisao sve spamentare (na svu sreću svi su sadržali jednu od dve ključne reči: "poker" i "casino", tako da nije bilo problema izdvojiti samo njih). Nažalost, samo brisanje slogova iz baze nije bilo dovoljno, jer pMachine, koji pokreće radionicu, broj komentara za svaki članak drži i u samom slogu u tabeli članaka, tako da sam morao i tu da ispravim. MySQL ne podržava složene upite sa kojima je moguće nešto ovako uraditi jednim upitom, već sam morao da pravim mali PHP skript koji radi to što treba. Na sreću, izgleda da je kodiranje u PHPu kao vožnja bicikla - nikad se ne zaboravlja, pa sam se posle više godina kodiranja u drugim alatima začas snašao.

Što se tiče trajnijeg rešenja za eliminaciju [spamentara](http://en.wikipedia.org/wiki/Blog_spam), prvo sam razmišljao o nekom rešenju sa generisanim slikama sa kojih korisnik treba pročitati i prekucati neki random tekst (tzv. [CAPTCHA](http://en.wikipedia.org/wiki/Captcha) test, vrsta [Tjuringovog testa](http://en.wikipedia.org/wiki/Turing_test)), zatim o nešto banalnijem rešenju sa uvek jednom te istom slikom i konstantnim tekstom. Na kraju sam zapazio da i pMachine ima sistem cenzurisanja nekih reči u komentarima, ali na taj način što uvek prihvati komentar, samo ga pre prikazivanja isparsira i "osetljive" reči zameni zvezdicama. Ja sam uzeo i malo izmenio taj sistem, tako da se komentari sa "osetljivim" rečima u startu odbijaju, sa prigodnom porukom korisniku. Rešenje naravno nije 100% sigurno, ali bi odbilo prethodni nalet spamentara, i ne opterećuje korisnike sa još jednim poljem koje moraju da popunjavaju pri ostavljanju komentara.

