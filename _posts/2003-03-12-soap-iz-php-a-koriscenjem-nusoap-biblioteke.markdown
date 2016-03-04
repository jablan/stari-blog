---
layout: post
title: SOAP iz PHP-a korišćenjem NUSOAP biblioteke
date: '2003-03-12 10:24:21 +0100'
mt_id: 16
post_id: 16
author: jablan
---
Malo sam se igrao (dobro de, trebalo mi je, ali ne bezuslovno) sa web servisima, [SOAP-om](http://www.soapware.org/bdg) i pristupom istima iz različitih klijentskih sredina. Za pristup iz PHP-a koristio sam [NUSOAP](http://dietrich.ganx4.com/nusoap/index.php) biblioteku, to je prva na koju sam naišao iako verovatno nije ni najbolja ni najpopularnija. PHP, s obzirom da se interpretira, daje neke lepe mogućnosti, npr. da "u hodu" kreirate pravi proxy objekat direktno iz WSDL-a web servisa, na foru

    require_once('nusoap.php');
    $soapclient = new soapclient('http://someSOAPServer.com/hello.wsdl','wsdl');
    $soap_proxy = $soapclient->getProxy();
    echo $soap_proxy->hello('dietrich');

Sve u svemu, zgodna stvar ako vam trebaju web servisi; doduše, nije sve proradilo iz prve kako treba: na serverskoj strani (implementirano u MS .NET-u) morali smo da dodamo atribut [[SoapRpcMethod]](http://msdn.microsoft.com/library/en-us/cpguide/html/cpconxmlserializationwithwebservices.asp) odgovarajućoj web-metodi, nisam imao vremena da ulazim detaljnije u razloge, ispalo je da je u pitanju nešto sa namespace-ovima i serijalizacijom parametara. Takođe, morao sam da tweak-ujem NUSOAP da bi u SOAP zahtevu prosledio Unicode ćirilične stringove...

Dakle, iako kompatibilnost web-servisa još nije dostigla idealan nivo, oni su već podržani na svim razvojnim platformama i nude nama developerima dosta toga. Ako već niste, upoznajte se s njima što pre!

