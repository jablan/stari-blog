---
layout: post
title: Problemi sa CSS dizajnom
date: '2004-10-18 17:17:59 +0200'
mt_id: 109
post_id: 109
author: jablan
---
Već duže u svetu veb dizajna vlada trend dizajna strogo baziranog na CSS-ovima: ideja je da HTML sadrži samo "suve" podatke, bez ikakvih (ili sa što manje) naznaka kako se sadržaj treba prikazati. Generalno, ideja je jako dobra: na ovaj način svaki od uređaja kojim pristupamo vebu može da prikaže na način njemu adekvatan, sam HTML je čitak i jasan, a dizajn se menja samo izmenom CSS-a.

Iako sam ranije pisao više HTML-a, u poslednje vreme nemam toliko prilike da se susrećem sa dizajnom, tako da se sve što katkad i uradim bazira na dizajnu zasnovanom na tabelama. Sve nekako nisam imao vremena da se ovome posvetim malo ozbiljnije i vidim iz prve ruke šta predstavlja pravi CSS bazirani dizajn.

Igrom slučaja, firma u kojoj radim primila je novog (zasad prvog) veb dizajnera. Malo sam sarađivao sa njim i probao par stvari da uradim po novim pravilima, provalio sam _float_ CSS property, malo se igrao sa horizontalnim raspoređivanjem elemenata unordered liste (video sam da [svašta](http://www.aplus.co.yu/ADxMenu/) može da se uradi), svega par sati je potrebno da se pohvataju osnove. Ali...

Izgleda da je najveći problem kompatibilnost brauzera: mali primer koji sam pravio proveravao sam u tri: IE 6, Firefox-u i Operi. Kako Marfijev zakon obično kaže, uvek mi je korektno radilo u tačno dva od tri: ili radi u Operi i Mozili, ili u IE i Operi, sve u svemu, nikako da napravim to što sam hteo da radi u sva tri. Ranije verzije Internet Eksplorera nisam ni pokušavao da probam...

Tako sam izgubio par sati i nešto živaca i na kraju nisam dobio to što sam hteo, pa sam prepustio dizajn čoveku koji je plaćen za to i vratio se starom dobrom SQL-u [sigh].

