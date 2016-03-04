---
layout: post
title: Kad se kontrole otmu kontroli...
date: '2003-02-20 12:33:18 +0100'
mt_id: 11
post_id: 11
author: jablan
---
Detaljna disekcija jednog užasno lošeg korisničkog interfejsa: kako ne treba raditi, na primeru programa za kontrolu FM radio kartice

  
 ![image]({{ site_url }}/images/radioaktiv_tn.png)

<!--more-->

FM tjuner (radio) kartica je zgodna stvar za ovo malo preostalih poklonika ovog staromodnog medija. Kartica koju trenutno imam u računaru radi pristojno; naravno, hvata manji broj stanica nego neki kvalitetni samostalni radio (ovo verovatno i zato što se nalazi vrlo blizu jakih izvora zračenja), no sa pozicije na kojoj sam bez problema hvata [B92](http://www.b92.net). Uz samu karticu i drajver, dobija se i odgovarajući softver za kontrolu kartice. Pogledajmo malo kako to izgleda:

![]({{ site_url }}/images/radioaktiv.gif "panel doticnog programa")

Nije mi jasna jedna stvar. U razvoj ovog programa neko je verovatno uložio dosta vremena, primećujete da nema nijedne standardne windows kontrole, sve je čovek pravio ispočetka. Meni nikako ne ide u glavu **zašto** se ljudi toliko trude na naprave tako loš korisnički interfejs. Pokušaću ovde da analiziram zašto je interfejs baš ovakav i zašto kao takav **ne valja** , deo po deo.

Jedna stvar je očigledna: program je napisan da što više podseća na FM tjunere koje viđamo po automobilima. Auto-tjuneri su dizajnirani po principima koji odgovaraju odgovarajućim uslovima. Cilj pri projektovanju auto-radija verovatno treba da bude da se može lako koristiti jednom rukom, bez puno gledanja (zbog sigurnosti vožnje). Dakle, komande koje se najčešće koriste (paljenje/gašenje, promena jačine i izbor stanice) treba da budu najizraženije, lako dostupne i dovoljno različite međusobno i od ostalih kontrola.

Tačno je da sličan princip isticanja najčešće korišćenih kontrola treba slediti i pri pisanju softvera, ali to ne znači da treba koristiti isti **tip** kontrola. Zašto, videćemo. Idemo redom...

### 1. "Potenciometar" za regulisanje jačine zvuka

Zamislite da treba da smanjite preglasnu muziku u svom automobilu, ali tako da ne koristite prste desne ruke, već vrh olovke koju njome držite. Mislite da je izvodljivo? Čak i da jeste, mislite da biste lako mogli da nabodete baš onu jačinu koja vam odgovara?

Autor programa je zaboravio to da je korisniku današnjeg računara na raspolaganju samo šiljati kursor miša umesto milenijumima usavršavanog sistema senzorno-motoričkih, mišićnih i skeletnih usko povezanih procesa koji se odigravaju u trenutku kad nam palac i kažiprst lagano "odvrnu" [omiljenu pesmu za vožnju](http://www.geocities.com/unitedtabs/tabs/stealers_wheel-stuck_in_the_middle_with_you.html). Dok se ne razviju neki novi metodi interakcije sa računarom i dok smo većinom osuđeni na korišćenje miša, najbolji način za imitaciju potenciometra je stara dobra kombinacija klizača (i to horizontalnog, jer su horizontalni pokreti mišem, odnosno rukom koja njime upravlja, udobniji i bolje kontrolisani od vertikalnih) i tastera na tastaturi. Klizači, s druge strane, nisu zgodni za ugrađivanje u auto-radije (zbog trešenja automobila u pokretu).

### 2. Nema title bar-a

Verovatno da bi program što više podsećao na "pravi" radio, možda i zbog nekih izvitoperenih estetskih nazora, autor je iz programa izostavio ni pet ni šest nego title bar, to jest gornji deo prozora uz pomoć koga se prozor pomera po ekranu i na kome se nalaze jako bitne kontrole svakog programa, dugmad za minimizaciju i zatvaranje programa. Ove kontrole autor je premestio u donji levi (?) ugao radio panela, pa treba neko vreme da se novi korisnik snađe, a i redovnom korisniku treba nešto vremena da "prevede" akciju koju je dosad radio automatski, bez razmišljanja na jezik novog korisničkog interfejsa. Zahtevanje od korisnika da protiv svoje volje troši vreme i vijuge na program nije ništa drugo do bezobrazluk autora.

Pored toga, kad hoćemo da pomerimo panel na neko drugo mesto, treba da pogađamo za koji deo treba da ga hvatamo (da slučajno ne bismo aktivirali neku neželjenu akciju - recimo splash-screen, kao kod MicroDVD-a, još jednog programa sa užasnim interfejsom), a pored toga i da razmišljamo da li se program uopšte može pomerati na ovaj način.

Još jedan problem koji može a i ne mora imati veze sa navedenim je taj da se program, po startovanju, uopšte ne pojavljuje u task baru, tako da je, u slučaju da je njegov prozor prekriven nekim drugim (meni je u proseku startovano oko 10-ak prozora), potrebno da ih sve minimiziramo da bismo pristupili radio panelu. Još jedan nezamisliv bezobrazluk.

### 3. "Klackalica" dugmići

Po ugledu na (po meni lošu) praksu kod raznih uređaja, pa i radio tjunera, autor programa je za kontrole za menjanje stanice i traženje susedne aktivne frekvencije izmislio novu kontrolu, pa tako ako kliknemo levu stranu dugmeta, potražiće se prva stanica sa manjom, a ako kliknemo desnu sa većom frekvencijom od trenutne. To je možda i logično kod pravih uređaja. Na računaru tako nešto ne treba raditi. Gde je granica levog dela dugmeta, a gde desnog? Šta će se desiti kad kliknemo na sredinu ovog dugmeta? Opet se traži od korisnika da razmišlja, pogađa i eksperimentiše, samo da bi promenio stanicu.

### 4. "LCD" displej

Nekad su proizvođači digitalnih uređaja, kalkulatora, satova, pa i tjunera, bili prinuđeni da, zbog tehnologije (čitaj: cene), koriste ovakve "štapićaste" LCD displeje za prikaz cifara. Ovakve cifre se mogu pročitati, ali samo blago podsećaju na prave brojke. Na sreću, ta vremena su prošla. Uglavnom. Autor programa se odlučio za povratak u tehnološku prošlost. Na modernim monitorima sa pristojnom rezolucijom, prinuđeni smo da gledamo fluorescentne "LCD" cifre. Opet mučenje korisnika.

Ono što je autor prevideo je još jedna razlika između računara i auto radija: Računar ima tastaturu, na kojoj se može otkucati ime stanice. Ili se može napraviti zanimljiv i koristan internet sajt sa koga se mogu automatski "prevući" nazivi stanica na određenoj lokaciji. Normalno, onda bi se umesto (ili pored) frekvencije, ispisivalo, daleko "humanije" od broja, ime stanice. Onda se i pri izboru stanice čovek lakše snađe. No, nesrećni se autor zadržao na "portovanju" radija iz svog automobila...

### Šta reći, bez teških reči

Pored navedenih, program obiluje i drugim greškama; pomenimo samo nekorišćenje sistemskih boja i fontova (bez obezbeđivanja nekog rezervnog metoda tipa "skinova"). Generalno, treba izbegavati kreiranje sopstvenih kontrola, praveći se pametniji od stotina inženjera koji su kreirali standardnu paletu kontrola. Kontrolu treba kreirati samo kad ne postoji adekvatna postojeća. Svetao primer potpuno ispočetka napisanog interfejsa je [winamp](http://www.winamp.com), gde su autori bili prinuđeni na ovaj korak zbog minijaturnog prozora. Treba primetiti da su u pitanju takođe standardni tipovi kontrola (dugmad, klizači), samo redizajnirani. Takođe, programeri winamp-a obezbedili su odličan sistem skin-ova, omogućivši tako da korisnik izabere više ili manje konvencionalan izgled.

