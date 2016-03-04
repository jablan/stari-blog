---
layout: post
title: 'Komentari ponovo rade II: Osveta IP filtera'
date: '2005-01-04 19:31:53 +0100'
mt_id: 117
post_id: 117
author: jablan
---
Kao što danas obećah, dodao sam i farmaceutske vruće ključne reči na cenzurisanu listu, i opravio sistem IP banovanja pri ostavljanju komentara. Detaljnije o ovom drugom možete pročitati u nastavku teksta. Sad izvolite pišite, komentari ponovo rade.



<!--more-->

Pomnijim pregledom kooda koji pokreće pMachine, ustanovio sam da IP filtriranje funkcioniše, ili treba da funkcioniše, i pri ostavljanju komentara. Međutim, u koodu koji ovo radi potkrala im se prilično krupna greška koja praktično čini da ova provera ne radi. Naime, ovo je parče kooda koje je proveravalo IP adresu prilikom ostavljanja komentara:

    function ipbancheck()
    {
    	global $db_ipbanning;
    	
    	$ip = get_ipaddress();
    
    	$db = new DB();
        
    	$q = "select ipaddress from $db_ipbanning";
    	$query = new DB_query($db, $q);
    
    	while ($query->db_fetch_object()) 
    	{
    		$uip = $query->obj->ipaddress;
    
    		if (ereg("^$uip", $ip))
    		{
    			return true;
    		}
    		else 
    		{
    			return false;
    		}
    	}
    }

Pažljiviji čitaoci će sigurno odmah uočiti bag: IP korisnika se upoređuje samo sa prvim banovanim IP-jem iz baze. Na stranu to što je ceo način provere loš: iterira se kroz sve IP adrese u bazi i svaka se upoređuje sa aktuelnom, umesto da se aktuelna adresa prosledi kroz WHERE uslov SQL. Takođe, struktura

    if (uslov) return true else return false;

 ne ukazuje na preveliku profesionalnost programera.

Ovaj kood zamenio sam sa efikasnijim (i pre svega, ispravnim)

    function ipbancheck()
    {
    	global $db_ipbanning;
    	$ip = get_ipaddress();
    	$db = new DB();
        
    	$q = "select count(*) as bannedcount from $db_ipbanning where ipaddress = '$ip'";
    	$query = new DB_query($db, $q);
    	
    	if ($query->db_fetch_object()) {
    		$bannedcount = $query->obj->bannedcount;
    		return $bannedcount > 0;
    	}
    	return false;
    }

Trebalo bi da je ovo OK, ako neko ima još neku sugestiju, rad sam da saslušam.

