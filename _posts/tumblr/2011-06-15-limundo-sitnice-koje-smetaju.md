---
layout: post
title: Limundo, sitnice koje smetaju
date: '2011-06-15T09:26:13+02:00'
tags:
- Limundo
- rant
- usability
- security
tumblr_url: http://jablan.radioni.ca/post/6548544794/limundo-sitnice-koje-smetaju
---
Redovno koristim Limundo i, iako je u pitanju sasvim funkcionalan sajt sa sada već vrlo velikim komjunitijem, ima par stvari koje čine da Limundo i dalje odaje utisak nedovršenog i poluamaterskog proizvoda. U pitanju su sitnice koje bi bilo lako ispraviti, a znače puno:

### Two-level security

Ne želim da moram da se logujem _uvek_ kad pristupam sajtu. Ni GMail ne zahteva logovanje pri svakom pristupu. Umesto toga, treba omogućiti dva nivoa pristupa: prvi nivo sa trajnom sesijom za “soft” pristup sajtu - posmatranje svojih i tuđih aukcija, čitanje pošte, i drugi nivo, sa dodatnim logovanjem i kratkotrajnom sesijom - za postavljanje aukcija, bidovanje itd. Ovaj sistem koriste i GMail i Amazon, recimo.

### Auth token u email linkovima

Ako mi Limundo pošalje email (npr, kada primim novu poruku), želim da se klikom na link u mejlu automatski prijavim u prvi security nivo na Limundu, bez potrebe da kucam svoj username i password ponovo. Sama činjenica da imam pristup svom mejlu znači da imam pristup i svom Limundo nalogu.

### Automatsko produžavanje aukcije pri bidovanju u poslednjim minutima

Popularni “fazon” na Limundu je bidovanje u poslednjim sekundama aukcije. Na ovaj način kupci se dovode u neravnopravnu situaciju (od aukcije pravi se igra na sreću), a predmet prodaje ne uspe da dostigne punu vrednost, tako da je i prodavac, a posredno i Limundo s obzirom da radi na procenat, oštećen.

Aukcija treba da se automatski produži za par minuta, ako je ponuda postavljena u poslednjim minutima (tako npr. funkcionišu neki onlajn sportski menadžeri tipa hattrick.org). Na taj način predmet će prirodno dostići svoju tržišnu cenu a niko od kupaca neće se osećati frustrirano ako je bio spreman da ponudi višu cenu od ostalih.

### Izmena lozinke treba da ide kroz verifikacioni link

Trenutno bilo ko ko zna moju email adresu može da promeni moju šifru. To nije ok. Umesto ovog, u mejlu koji dobijem kad kliknem “zaboravio sam šifru”, treba da stoji jedinstveni link kojim potvrđujem izmenu šifre, tj. šifra treba da se promeni tek kad ja, vlasnik email naloga, odradim svesnu akciju. U suprotnom, šifra treba da ostane ista kao ranije.

