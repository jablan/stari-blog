---
layout: post
title: CSS iskustvo
date: '2005-03-06 14:05:31 +0100'
mt_id: 121
post_id: 121
author: mileusna
---
Ko god prati šta se dešava u svetu web dizajna, zna da postoji trend da se web sajtovi prave uz što veće korišćenje CSS-a. O tome je i _jablan_ [pisao](http://www.radionica.co.yu/index.php?id=P109) pre nekoliko meseci. Isto tako, ko god je probao da napravi sajt putem CSS-a zna da to i ne mora da bude tako veselo.

Ja lično sam tri puta pokušavo da svoj način rada prebacim sa tebela na CSS i uvek sam zbog nedostatka vremena i gluposti koje su me mučile sa stilovima odustajao od toga i stvari završavao na klasičan način. Istina je da neke stvari koje brzo i lako radite putem tabela, preko stilova i ne mogu da se urade tako lako, kao npr. banalan primer footera koji bi uvek stajao na dnu ekrana odnosno sadržaja bez obzira da li se tekst na strani sastoji od jedne rečenice ili tri kucane strane.

    <table height='100%'>
      <tr>
         <td height='100%'> content </td>
      </tr>
      <tr>
         <td height='20'>footer </td>
      </tr>
    </table>

Da bi ste dobili isti efekat preko stilova postoje razna rešenja ali ni jedno nije prirodno, već se služe raznim trikovima.

Drugi problem donekle je i kompatibilnost. Dugo smo čekali da browseri na isti način počnu da tumače table, sada ćemo izgleda opet morati malo da sačekamo da na identičan način tumače i stilove.

Evo malog primera i rešenja koje će možda nekog spasiti muka. Podesio sam visinu DIV elementa i postavio mu padding za top i bottom. U Explorereu je radilo sve onako kako sam i očekivao, visina DIV elementa je bila fiksirana na ono što sam želeo, a tekst je bio pomeren unutar elementa na zadate padding vrednosti. To je po meni bilo prirodno da tako radi.

Međutim, FireFox je na zadatu visinu DIV objekta još dodavao padding vrednosti i totalno poremetio izgled strane. Zašto? Tražeči rešenje na netu pronašao sam da je po W3C, definicija padding elementa zapravo i jeste ono što radi FireFox, a ne ono što smo ja i Explorer mislili. Problem se može rešiti ukoliko se navede pravilan DOCTYPE, no na žalost tada će se i u Exploreru sadržaj prikazivati onako kako ne bi ste očekivali, barem ja nisam, ali šta ćete, to vam je standard.

Postoji i rešenje kojim FireFox-u možete specifirati da padding tumači drugačije, kao što to radi i Explorer bez navođenja DOCTYPE-a. U tu namenu, FireFox poseduje svoj specifičan stil -moz-box-sizing koji glasi:

    -moz-box-sizing:border-box;
    box-sizing:border-box;

što rešava sve probleme ali ako ne navodite DOCTYPE, jer ako ste već naveli DOCTYPE, sada će Explorer raditi po standardu, pa opet imate problem. Inače stil box-sizing bi uskoro trebalo da postane deo CSS standarda, ali ga IE još uvek ne podržava.

Zaključak... Na kraju sam sve ostavio da radi po standardu a svoj problem sam rešio na drugi način, dodavanjem još jednog DIP ili P elementa unutar postojećeg, sa ogovarajućim marginama. S ozirom da sajtovi na kojima trenutno radim poseduju spartanski dizajn, ostao sam čvrsto rešen da stvari isteram do kraja uz korišćenje stilova jer mogu da preživim i ako neke stvari ne budem umeo da uradim, a vremenom ću valjda i više toga naučiti. Obavezno koristite DOCTYPE ako radite sa stilovima jer vas, kao što vidite, može spasiti dosta muka u startu.

