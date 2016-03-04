---
layout: post
title: ASP.NET - glomazno ali komplikovano
date: '2004-02-10 18:12:29 +0100'
mt_id: 65
post_id: 65
author: jablan
---
Već duže radim u ASP.NET-u i vrlo sam zadovoljan platformom: ugodan i [inteligentan](http://msdn.microsoft.com/library/en-us/vsintro7/html/vxoriintellisensefeatures.asp) editor, [odličan](http://genamics.com/developer/csharp_comparative.htm) [jezik](http://msdn.microsoft.com/vcsharp/language), moćan [API](http://msdn.microsoft.com/library/en-us/cpref/html/cpref_start.asp) i, sve u svemu, prva Majkrosoftova razvojna platforma kojom sam zadovoljan.

Ali ma koliko je .NET sa jedne strane olakšao programiranje i razvoj veb aplikacija, sa druge strane je ceo mehanizam postao strašno komplikovan. User kontrole, codebehind, runat="server" atributi, povrh svega razulareni JScript, daju mnogo kontrole ali i predstavljaju potencijalne zamke, svaki za sebe, ali i u sadejstvu. Ono što se meni neretko događa je da naiđem na grešku, ali se ona ispolji na potpuno neočekivanom mestu. Na kraju, posle par sati ispitivanja i debagiranja, ispostavi se da je form dizajner svojevoljno upario neke html tagove i zbog toga dobijam runtime grešku na potpuno trećem mestu.

Izgleda da, na kraju krajeva, alat, ma koliko bio moćan i savršen, nikad neće moći da nadomesti programersko iskustvo i njuh bagolovca.

