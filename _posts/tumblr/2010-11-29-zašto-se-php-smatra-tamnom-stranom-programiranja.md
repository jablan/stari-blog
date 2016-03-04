---
layout: post
title: Zašto se PHP smatra tamnom stranom programiranja
date: '2010-11-29T23:36:00+01:00'
tags:
- php
- programiranje
- prevod
tumblr_url: http://jablan.radioni.ca/post/1730587462/zašto-se-php-smatra-tamnom-stranom-programiranja
redirect_from: '/post/1730587462/zašto-se-php-smatra-tamnom-stranom-programiranja/'
---
U pitanju nije moj tekst, već moj prevod, original možete naći [ovde](http://programmers.stackexchange.com/questions/2323/why-is-php-considerd-the-darkside-of-programing/6024#6024). Preveo sam ga jer dobro formuliše moj lični stav o PHP-u.

PHP ima puno problema. Većina ima istorijske korene ali, u krajnjoj liniji, oni su razlog što ga dosta programera smatra užasnim jezikom.

### `<?php` i `?>` “tagovi” i sva njihova rodbina

Oni uglavnom potiču od rane prirode PHP-a kao templejt jezika. Iako većina (iskusnih) PHP programera danas započinje gotovo svaki svoj fajl otvorenim tagom, oni nameću linearni stil programiranja, koji je jako loš izbor za bilo šta veće od CGI-skripte.

Ovi tagovi pomažu ako želite da koristite PHP kao templejt jezik, ali u suprotnom vas u najboljem slučaju zavaravaju (npr. smatra se dobrom praksom da se zatvoreni tag ne navede jer on implicira štampanje spejsova koji se nalaze iza njega).

### Nedostatak konvencija

Standardne biblioteke PHP-a su uglavnom evoluirale spontano, bez ikakvih konzistentnih pravila imenovanja. Kao posledica toga, šeme imenovanja i redosleda argumenata su u najmanju ruku nekonzistentne, često neujednačene unutar istog paketa. PEAR je uspeo da izbegne ove probleme namećući striktnu politiku ali to ne pomaže puno kad se dvoumite u kom redosledu idu igla i plast sena u `strpos` ili postoji li donja crta u `htmlspecialchars`.

### Uključene baterije

Pridošlici standardna biblioteka verovato izgleda jako bogato. Problem je da, uprkos svojoj gigantskoj veličini, često nije baš toliko od pomoći. Funkcije se često trude da obezbede dodatnu funkcionalnost koja ih čini komplikovanijim za korišćenje nego što je potrebno, ili su specijalizovanije nego što je potrebno. Nedostatak imenskih prostora (namespaces) čini ovaj problem još gorim.

### Iznuda tipova (type coercion)

Nema šta puno da se priča o ovom. PHP je slabo tipizirani dinamički jezik, što znači da vrlo lako prašta (i pravi se “pametan”) po pitanju tipova promenljivih. Ovo nije veliki problem u kodu koji sastavljate na brzaka, ali lako dovodi do nepredviđenih posledica i zahteva vrlo odbrambeni stil programiranja za složenije aplikacije, čineći tako sve prednosti dinamičkog jezika uglavnom beznačajnim.

### Užasna podrška za Unikod

Iako u standardnoj biblioteci postoje “multibyte” funkcije koje obezbeđuju ne-ASCII alternative ostatku biblioteke, ovakvo tretiranje “odvojenih ali jednakih” Unikod stringova često izaziva probleme čak i naprednim korisnicima jezika. Postoji diskusija o prebacivanju PHP stringova na potpuni Unikod u nekoj od idućih verzija, ali imajući u vidu sporo prihvatanje prethodnih verzija, ne bih bio preterano optimističan da ćemo ikada videti nativnu podršku za Unikod u PHP-u.

Tačno je da dosta drugih jezika takođe zasnovano na ASCII-ju, ali imajući u vidu da je PHP dobrim delom glavni serverski veb-jezik današnjice, ova mana je konstantan trn u oku svakog (ne-američkog?) veb programera. Postoje zaobilazna rešenja u međuvremenu, ali sva izgledaju kao budževine u poređenju sa tim kako se snalaze ostali jezici.

### Jezik i frejmvork

Jedna od najvećih prednosti PHP je ujedno i jedan od najvećih problema - njegova standardna biblioteka igra ulogu veb frejmvorka. “Superglobalne promenljive”, recimo, imaju smisla ako PHP posmatrate kao frejmvork, ali mogu da iskomplikuju stvari ako želite da koristite neki drugi frejmvork nad njim.

Povezani problem je to što PHP podrazumeva smeštanje skripti u koreni veb direktorijum (web-root) (što je loša ideja), čineći da dosta deljenih hosting provajdera obezbeđuju samo web-root kao home direktorijum (tj. sve što je na serveru, automatski je i na vebu).

### Jednokratna sintaksa

Usled načina na koji je originalni PHP interpreter bio napisan, PHP nameće politiku da operatori i sintaksa moraju biti potpuno nedvosmisleni: pristupanje nizovima/heševima (razlika između običnih nizova i onih “asocijativnih” je magična, mada nažalost ne i nepostojeća) koristi različit operator od onog za pristup atributima objekta, za koji se koristi različit od onog za pristup statičkim članovima klase, za koji se koristi različit od onog za pristup imenskom prostoru (namespace).

Iako ovaj nedostatak nedvosmislenosti čini PHP lakšim za interpretiranje (što nije tačno, što su mnogi naučili težim putem), takođe dodaje nepotreban naglasak na detalje implementacije, što je potpuno suprotno onom što ostali jezici rade nudeći magične metode za pristup (accessor methods) (tj. tako što getter i setter metode oponašaju pristup običnim atributima). Ovo je možda subjektivno, ali to je i razlog koji je u krajnjoj liniji doveo do izbora obrnute kose crte (backslash) za pristup imenskom prostoru (namespace) (što čak i PHP programeri uglavnom smatraju nesrećnim, mada neizbežnim).

### “Laka droga”

Sveprisutnost PHP-a znači i veliku potražnju za PHP programerima (iako je i zasićenje tržišta prilično visoko). Ovo takođe znači da je mnogo PHP programera izabralo PHP za svoj prvi programski jezik, često bez prethodnog iskustva ili formalne obuke (a često i bez stvarnog interesovanja za programiranje; npr. veb dizajneri koji žele da edituju templejt ili admini kojima je rečeno da izmene WordPress instalaciju). Ovo dalje znači da postoji mnogo “programera” koji aktivno učestvuju u “komjunitiju” jezika, a da su pritom neiskusni i/ili bez da poznaju najbolja rešenja (best practices). Rezultat je nepregledna količina zaista užasnog koda.

Iako se loš kod može pisati u bilo kom jeziku, veličina PHP komjunitija i njen nizak prosečan nivo znanja su omogućile upliv lošeg koda na Internet više nego u bilo kom danas živom jeziku. Ovo ne znači automatski i krivicu jezika i ne znači da nema dobrih PHP programera, samo da je jako niza odnos signala i šuma.

Zbog svega ovoga, dosta dobrih programera se ne drže PHP-a, već se premeštaju na druge jezike. Ovo još više pogoršava problem, jer znači da pored upliva nestručnih programera, oni stručni imaju velike šanse da napuste (ili izbegnu) PHP na duže staze.

### I sve ostalo

Ova lista je daleko od kompletne. Postoje gomile i gomile drugoj problema i par pretraga na vebu će vam dati dosta razloga zašto “PHP sucks” sa tehničke strane. Iako ima dosta (kvalifikovanih) ljudi koji mu staju u odbranu, većina protivnika ga jednostavno smatra aljkavim, i ja smatram da ga takav epitet najbolje opisuje.

Najveća prednost PHP-a je verovatno to što je toliko prisutan i relativno lak za učenje (barem za osnove). Malo veb developera mogu sebi da priušte da ga potpuno ignorišu, čak i ako se trude da ga izbegnu kadgod je moguće. Dosta govori to što se većina PHP firmi danas reklamiraju kao Typo3/WordPress/Drupal eksperti, i fokusiraju na prilagođavanje i održavanje postojećih OpenSource alata, radije nego da pišu nove aplikacije ispočetka.

TLDR: PHP je za veb programiranje ono što je Majkrosoft Vord za pravljenje veb stranica.

