---
layout: post
title: ASP.NET za PHP programere
date: '2007-05-30 15:19:13 +0200'
mt_id: 209
post_id: 209
author: branimir
---
Na domaćem vebu vrlo je malo tekstova koji se trude na naprave most između različitih tehnologija. Kako sam prešao _put_ od PHP do ASP.NET programera, uz Jablanovu podršku, rešio sam da pokušam da podelim svoja iskustva. Dakle, pokušaću da predstavim Microsoft rešenje za razvijanje web aplikacija ASP.NET 2.0.

Za praćenje teksta dovoljno je osnovno poznavanje PHP-a i principa razvoja internet aplikacija.



<!--more-->

### Uvod

Posmatrano iz ugla developera, Microsoft .NET framework je jedna od najznačajnijih promena na Windows platformi od pojavljivanja windows-a. Pod pritiskom konkurencije ( [Java](http://en.wikipedia.org/wiki/Java_%28programming_language%29 "Java (programming language)"), frameworks [J2SE](http://en.wikipedia.org/wiki/J2SE TITLE=J2SE) and [J2EE](http://en.wikipedia.org/wiki/J2EE TITLE=J2EE)) Microsoft je bio primoran da značajno unapredi svoje razvojne alate. NET framework je razvijan prateći nekoliko osnovnih zahteva:

- **Zajednički Runtime Engine** za sve jezike (Common Language Runtime), osnovna ideja je da se kod (bez obzira na to koji od dostupnih programskih jezika koristite) prevodi u zajednički intermediate language (CIL). 
- **Nezavisnost jezika** , na nivou framework-a (Common Type System) definisani su svi podržani tipovi podataka i programskih struktura, što omogućava podršku za korišćenje različitih programskih jezika. 
- **Base Class Library** , biblioteka tipova dostupna svim jezicima koji koriste framework, enkapsulira mnoge često korišćene funkcije, npr. čitanje i pisanje fajlova, xml dokumenata,&nbsp; interakciju sa bazama podataka, prikazivanje grafičkih elemenata... 

Nas, pre svega, interesuje deo .NET platforme, pod nazivom ASP.NET ( [http://en.wikipedia.org/wiki/ASP\_.Net](http://en.wikipedia.org/wiki/ASP_.Net)), koji je namenjen web razvoju **. ASP.NET** je skup tehnologija za razvoj web aplikacija, koji omogućava razvoj dinamičkih web sajtova, web aplikacija i web servisa.

U primerima koristim programski jezik c#, jer je on najsličniji PHP-u, a i meni je bliži od visual basic, ili drugih dostupnih jezika.

### Okruženja za rad

Za razliku od LAMP platforme, ASP.NET ne daje toliko slobode u izboru razvojnih alata, mada postoje i alternative, uobičajeno se koristi Microsoft Visual Studio, ili Visual Web Developer koji je besplatan u tzv. Express varijanti ( [Visual Web Developer Express](http://www.asp.net/downloads/getvwd/default.aspx?tabid=62)).

Iako Visual Web Developer Express ima ograničenja u odnosu na VS, dovoljan je za naš cilj, upoznavanje sa alatom i razvoj jednostavnih web sajtova. Bez obzira na varijantu dobijate integrisano okruženje za razvoj (ide), sa svim neophodnim alatima za razvoj funkcionalne aplikacije. Developeru koji poznaje neko slično rešenje tranzicija neće predstavljati preveliki problem.

### Razlike samih jezika

Kako C# i PHP imaju sintaksu nastalu na osnovu jezika C, one su slične. Ne treba zaboraviti da između ova dva jezika postoje velike razlike u samom pristupu. U najboljoj nameri pojednostaviću stvari, pa neka mi oni upućeniji ne zamere.

C# je nastao kao jednostavnija verzija C++ za potrebe web aplikacija. Zadržao je osnovne osobine C++, dakle:

- objektni jezik;
- 
- strongly typed, promenljivama se određuje tip pri deklarisanju;
- kompajlira se pre izvršenja;
- sa sintaksom sličnom C++, odnosno C, kao što sam već pomenuo.

Sa druge strane, PHP je zamišljen kao zamena za Perl, znači jednostavan interpreterski jezik, koji omogućava brzi razvoj dinamičkih web stranica, koje nemaju prevelike zahteve. Tako da je PHP u prvim verzija bio na potpuno suprotnoj strani u odnosu na familiju C, C++, C#, ukratko:

- proceduralni (imperativ) jezik;
- typing: [dynamic](http://en.wikipedia.org/wiki/Type_system#Static_and_dynamic_typing TITLE=), [weak](http://en.wikipedia.org/wiki/Type_system#Strong_and_weak_typing TITLE=) – promenljive se ne deklarišu, dozvoljeni su operacije nad različitim tipovima, naprimer: sabiranje stringova i celih brojeva; 
- interpreterski jezik (dynamic, refleksion);
- sintaksa slična C.

Međutim, u poslednjim verzijama ove razlike mnogo manje.

U C# je uvedena tzv. reflection, tako da je moguće dinamički dodati metod ili properti klasi, a nešto ranije u PHP-u su uvedeni objekti, sa kojima od verzije 5.0 već možemo ozbiljno računati. Takođe i sam način izvršavanja koda može biti sličan, uzimajući u obzir da je C# kod moguće kompajlirati u run time, a da za PHP postoje tzv. Accelerators koji kompajliraju i/ili keširaju PHP skript da bi povećali performanse izvršenja skripta.

Zaključak je da su jezici koji su nastali na različitim idejama, u poslednjim verzijama&nbsp; suštinski počeli da se približavaju. Pretpostavljam da će u budućnosti ovaj trend da se nastavi, tako da nije na odmet pratiti dešavanja u protivničkom taboru. Možda je vreme da i developeri počnu da prave manju razliku između ove dve tehnologije.

### Organizacija koda

U ASP.NET web strana se sastoji od dva dela:

- Vizuelnih elemenata – markup, serverske kontrole i statični tekst 
- Programska logika strane – event handlers i ostali kod 

Mada je moguće spojiti programski (server side) kod i markup kod, logičniji izbor je Code-Behind model, gde je c# kod u zasebnom fajlu (ekstenzija .cs), a markup u .aspx falju. Najbliža analogija u PHP svetu je korišćenje templejt engine, gde su web strane organizovane po sličnom principu, ukoliko je za jednu web strani vezan jedan fajl sa programskim kodom i jedan fajl koji sadrži definiciju templejta.

### Događaji i forme

Najčešće, pozivamo PHP skrip sa nekim argumentima (POST, GET...), uradimo procesiranje argumenata u PHP-u koji kao izlaz daje HTML, i prestaje sa izvršavanjem. Ovo je linerni programski model, sa kojim ste dobro upoznati.

ASP.NET koristi event-driven model, koji možete videti u većini GUI&nbsp; (npr. windows) aplikacija, gde su događaji asinhroni, npr.: klik mišem, događaj sa tastature...

Ovi događaji se obrađuju odgovarajućim event handler-om (delegate u ASP.NET).

Ovakav model donosi neke prednosti, potrebno je manje koda, koji je pregledniji, jer je očiglednije na koju korisnikovu akciju će se kod izvršiti.

### Klasa Page

<!--<IMG SRC="ASPNETzaPHPprogramere01_images/ddf4mvwf_3c8ppvnfv.gif">--> ![image]({{ site_url }}/images/code_behind.gif)

Slika 1

Kada pravite stranicu u ASP.NET-u, kreirate klasu koja nasleđuje Page (System.Web.UI.Page), nazvaćemo je **SamplePage,** definisanu u fajlu SamplePage.cs, koja sadrži sav server side kod. Markap (design) kod je smešten u .aspx fajlu (SamplePage.aspx), koji nasleđuje našu klasu&nbsp; SamplePage, umesto da direktno nasleđuje klasu Page. Donekle pojednostavljen, ovaj _postupak_ kreiranja html izlaza prikazan je na slici 1.

Na prvi pogled ovaj pristup može da izgleda složeno, ali u toku razvoja ne morate misliti o tome. Okruženje se stara o većini stvari, a model brzo donosi prednosti u brzini razvoja i preglednosti koda, što ćemo brzo videti. Imajte u vidu da je uvođenjem parcijalnih klasa (ASP.NET 2.0) situacija nešto složenija, bez izmene osnovne ideje.

### Web Server Controls

Osnovna ideja je proširenje markap koda, tako da je osim statičnih HTML tagova u dizajnu stranice moguće koristiti i dve vrste serverskih kontrola:

- HTML Server Controls 
- Web Server Controls 

Slično kao i kod kreiranja stranice cilj je bolja organizacija koda i brži razvoj, ovaj kod kreira kontrolu tipa Button na stranici:

\<asp:button attributes runat="server" id="Button1" /\>

Ovaj kod ne morate kucati u editoru dovoljno je _prevu__ći_ kontrolu iz toolbox-a, obično sa leve strane u okruženju.

Pri generisanju stranice ovaj tag će biti zamenjenim odgovarajućim HTML tagom ili tagovima (odnos ne mora biti 1-1, neke kontrole generišu više različitih HTML tagova), osim toga u server side kodu _vidite_ objekat Button1 pomoću koga možete izmeniti izgled i sadržaj kontrole (properties). Da biste definisali tekst koji je ispisan na kontroli Button dovoljan je kod:

Button1.Text = "tekst";

Još jedna vrlo bitna razlika u odnosu na html tagove je što kontrola može imati definisane događaje (events), za odgovarajući događaj se vezuje event handler koji je odgovor na tu akciju korisnika. Kao što možete videti u primeru reakciju na događaj je definisan u samom markup kodu kontrole, mada je to moguće uraditi i iz koda, ili izmeniti event handler za neki događaj.

Mada na LAMP platformi ne vidim analogon serverskim kontrolama, verujem da ste sličan princip imali prilike da vidite u nekom od razvojnih okruženja za razvoj desktop aplikacija (Delphi, VB...).

### Hello World

Prikazaću, na jednostavnom primeru, kako ASP.NET funkcioniše u praksi.

Primer 1 (Hello World) sadrži jednu stranicu, koja prikazuje dve kontrole: Label (kontrola za prikaz teksta) i Button (html analogon: \<input type=submit\>). Kada korisnik _klikne_ na kontrolu _Button1_ poziva se event handler _Button1\_Click_ u kome ćemo izmeniti properti _Text_ kontrole _Label1_. Primer je pisan u Visual Studio 2005, ali uz minimalne izmene može raditi u bilo kojoj verziji.

Ovako jednostavan primer možete napisati u PHP-u za vrlo kratko vreme i sa manje koda. npr. Listing 3. PHP i jeste zamišljen za brz razvoj ukoliko su zahtevi dovoljno jednostavni. Ali već vrlo jednostavni dodatni zahtevi bi počeli da komplikuju život, npr. dodajte još jedno dugme kojim će koristnik moći da dobije neku drugu poruku? U ASP.NET okruženju je dovoljno prevući još jednu kontrolu Button u dizajn modu, kliknuti na njega, što će generisati odgovarajući event handler, i upisati kod po uzoru na postojeći Label1.Text = nesto. U php-u bi dodatni zahtev izazvao više promena, prvo analogne ovima koje sam naveo, zatim izmenu u strukturi provere get ili post parametara u zavisnosti šta ste koristili. Znači više nebi bilo dovoljno jednostavno proveravanje da li je get parametar action prosleđen, već posle toga i koja je njegova vrednost, da li je to click ili click2...

Samo potrebno vreme za izmenu ovog delu koda nije preveliki gubitak, u složenijoj situaciji gubitak može biti mnogo veći, jer je pitanje da li će izmene biti u skladu sa strukturom ostatka koda na stranici. U trenutku kada je stranica dovoljno složena da ne možemo da držimo njenu strukturu u _malom prstu,_ nastaje situacija koju, interno u timu u kome radim, nazivamo _krpljenje koda_, što označava izmene nastale u žurbi da bi se ispoštovali zahtevi, ili jednostavno zbog svima nama zajedničke osobine lenjosti. Takav način rada osim sasvim nepreglednog koda koji je značajno _skuplji_ za održavanje, drastično povećava i mogućnost pojave grešaka, tj. možete lako napraviti da nova funkcionalnost nekim od _bočnih efekata_ napravi problem u već postojećoj funkcionalnosti stranice.

Da napomenem da postoje metode da se na LAMP platformi izbegnu ovakve pojave, koje su, iskreno rečeno, mnogo češće izazvane _ljudskim faktorom_ nego razvojnim okruženjem, ali nije na odmet da alat izvorno bude projektovan tako da minimizira ovakve pojave. Takođe, u situaciji gde je na projektu angažovan jedan developer koji je odgovoran i raspolaže dovoljnim znanjem takvi problemi biće retki, ali je samo pitanje dana kada ćete početi da radite u timu, ako već niste.

  

[Listing 1 (Primer1.aspx)](http://blog.radioni.ca/images/articles/listing1.txt)

[Listing 2 (Primer1.cs)](http://blog.radioni.ca/images/articles/listing2.txt)

[Listing 3 (HelloWorld.php)](http://blog.radioni.ca/images/articles/listing3.txt)

