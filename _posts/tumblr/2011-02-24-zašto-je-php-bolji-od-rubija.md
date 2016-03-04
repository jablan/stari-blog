---
layout: post
title: Zašto je PHP bolji od Rubija
date: '2011-02-24T18:30:00+01:00'
tags: []
tumblr_url: http://jablan.radioni.ca/post/3485417396/zašto-je-php-bolji-od-rubija
redirect_from: "/post/3485417396/zašto-je-php-bolji-od-rubija"
---
[Prevod članka Alija Nadžafa, britanskog programera. Original je ovde: [Why PHP is better than Ruby](http://najafali.com/php-is-better-than-ruby.html)]

21.2.2011.

#### PHP je bolji od Rubija. Eto, rekao sam. U ovom članku ću vam objasniti zbog čega, i usput verovatno iznervirati neke hipi fanove od dvadeset i kusur sa japankama i Mekovima.

### U Rubiju sve je objekat… čak i literali!

Ovo je prosto bolesno. Ne znam kako Rubi developeri mogu da sebe nazivaju programerima. U PHP-u nismo pobornici standardnog interfejsa. Mi slavimo svoju šarolikost. Da li je `plast, igla` ili `igla, plast`? Da li treba da zovemo metodu nad objektom ili da ga prosledimo funkciji? Ili treba da radimo i jedno i drugo i kodiramo različitim stilovima da bismo učinili život veselijim?

U poređenju sa svakodnevnom avanturom provaljivanja kako PHP radi, Rubi je dosadan. Uzmite kao primer funkcije za rad sa stringovima. Da biste uradili najobičniju zamenu stringa u Rubiju, morate da pozovete metodu na svom stringu, a ne da ga prosledite funkciji za rad sa stringovima. Kakav objektno orijentisani krek je pušio Matz? To ubija svako uživanje u programiranju!

    <?php
    //zameni foo sa bar na razuman, PHP način
    str_replace('foo', 'bar', 'I eat food and play football')
    # I eat bard and play bartball
    
    # Kakav pacijent je smislio ovo objektno-orijentisano iživljavanje?
    "I eat food and play football".gsub('foo', 'bar')

Pored toga, imam osećaj da su developeri Rubija bili posebno duhoviti kad su smišljali jezik. Hajde da odemo dotle da se složimo da je sve objekat. Ali i klase? “Klase su objekti klase `Class`”? Neko sigurno umire od smeha na račun ovih ubogih Rubi developera.

### Sintaksu Rubija je nemoguće razumeti!

Rubi poseduje takve sumanute i uvrnute začkoljice koje normalno ljudsko biće nije sposobno razumeti. Pogledajte ovo, recimo:

    class Address
      attr_accessor :name, :line1, :line2, :county, :postcode, :country
    
      def Address.valid_postcode?(string)
        #true for valid postcode, false otherwise
      end
    
      def initialize(data)
        if data[:postcode]
          raise "Invalid postcode" unless Address.valid_postcode?(data[:postcode])
        end
      end
    end

Ovaj kod je potpuno nerazumljiv… Kao prvo, nigde nema vitičastih zagrada. Vitičaste zagrade me čine sigurnim i voljenim, a ja ovde ne vidim nijednu. Takođe, gubim osećaj ravnoteže kad nemam zagrade. Iako je suviše zagrada loša stvar (ne podsećajte me na to koliko mrzim LISP), naravno da su nam neophodne za grananja? Argumente funkcija? Zar niko ne uočava ludilo ovde?!

### PHP mi omogućava da vežbam svoju veštinu slepog kucanja a Rubi ne

Kao zaluđenik za slepo kucanje, volim da se vežbam. Problem sa Rubijem je što mi dozvoljava da radim iste stvari koje mogu u PHP-u, samo sa mnogo manje kucanja. Pogledajte ovaj primer jednostavne klase sa geterima i seterima u PHP-u, a zatim u Rubiju: <?php </p>

    class Address
    {
        private $name;
        private $line1;
        private $line2;
        private $county;
        private $postcode;
        private $country;
    
        public function getName() {
            return $this->name;
        }
    
        public function getLine1() {
            return $this->line1;
        }
    
        public function getLine2() {
            return $this->line1;
        }
    
        public function getCounty() {
            return $this->county;
        }
    
        public function getPostcode() {
            return $this->postcode;
        }
    
        public function getCountry() {
            return $this->country;
        }
    
        public function setName($newName) {
            $this->name = $newName;
        }
    
        public function setLine1($newLine1) {
            $this->line1 = $newLine1;
        }
    
        public function setLine2($newLine2) {
            $this->line2 = $newLine2;
        }
    
        public function setCounty($newCounty) {
            $this->county = $newCounty;
        }
    
        public function setPostcode($newPostcode) {
            $this->postcode = $newPostcode;
        }
    
        public function setCountry($newCountry) {
            $this->country = $newCountry;
        }
    }

A sada pogledajte istu stvar sa istim pristupom u Rubiju…

    class Address
      attr_accessor :name, :line1, :line2, :county, :postcode, :country
    end

Ovo je previše kratko da bi bilo kome bilo od koristi. Ako tako lako mogu da pravim klase sa public geterima i seterima na svom poslu, prsti će mi odumreti i neću imati ništa za vežbanje. Hoću da mi se tastatura dimi pošto otkucam definiciju klase, a tri patetične linije Rubi koda nisu ni od kakve koristi.

Takođe, bagovi koji su posledica grešaka u kucanju su vrhunac mog dana i preferiram sintaksu koja mi omogućava da napravim što više takvih. Batalite taj svetogrdni Rubi kod sa svojom konciznom i izražajnom sintaksom. Usredsredite se na ove tople i sigurne vitičaste zagrade. Eto, tako je bolje…

### Rubi vam ne dozvoljava da pravite proizvoljne public atribute na objektima!

Jedna od pobedničkih stvari kod PHP-a je po defaultu mogućnost da postavite proizvoljni javni (public) atribut na objektu. Pogledajte sledeći PHP kod:

    class Address {
          // vidi gore..
    }
    
    $address = new Address();
    $address->xCoordinate = 54;
    $address->yCoordinate = 73;

Ovo znači da možete da ugurate proizvoljne podatke u objekat gdegod želite u svom kodu! Povrh toga, ne morate da to deklarišete, dokumentujete ili ukažete na to na bilo koji način. Slobodno pišite kod u ostalim delovima sistema koji se oslanja na to da su ove public vrednosti postavljene. Ovo je odlično za očuvanje posla, jer niko osim vas neće moći da razume kako vaš kod radi.

### Rubi vam dozvoljava da redefinišete klase, gdegod vam padne na pamet, uključujući i one iz standardne biblioteke!

U Rubiju, možete da uradite ovo:

    # klasa za cele brojeve u Rubiju
    class Fixnum
      def +(adder)
        self - adder
      end
    end
    ## tako je rođaci, upravo sam pretvorio sabiranje u oduzimanje

Mora da nešto nije u redu sa jezikom koji vam dozvoljava da podrijete osnovna pravila aritmetike!

Šalu na stranu, developeri su po definiciji glupi. I zli. Dajte im priliku, komitovaće suvu konjsku balegu u svn i naprosto se ne može računati na njihovo ponašanje. Ako im pružite mogućnost da menjaju osnove jezika kako im se ćefne, sami tražite frku od svih glupih i zlonamernih developera iz vaše firme.

U nekim ekstremnim slučajevima, primećeno je da Rubi developeri u svom prirodnom okruženju umeju da prave čitave poddijalekte jezika, prilagođavajući jezik svom određenom domenu. Štagod radili, ne dozvolite ovakve jeretičke gluposti u svojoj organizaciji.

### Zaključak

Sve sam ispričao, Rubi je nemoguće razumeti, a daje developerima naizgled potpunu kontrolu nad jezikom. Najiskrenije vam predlažem da još jednom razmislite pre nego pokušate da naučite Rubi. To je slično zombi infekciji, dok kažete keks koristićete git za čuvanje koda, radićete od kuće u Textmate-u i bizarne funkcionalne paradigme će početi da se uvlače u način na koji pišete PHP.

Upozoreni ste.

