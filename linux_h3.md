# h3 Hello Web Server
## x) Name-based Virtual Host Support
The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support: https://httpd.apache.org/docs/2.4/vhosts/name-based.html

-	IP-pohjaisessa virtuaalipalvelimessa jokaisella verkkosivulla on oma IP-osoitteensa. Sen sijaan nimi-pohjaisessa virtuaalipalvelimessa monet verkko-osoitteet voivat jakaa saman IP-osoitteen. Tämä tulee tehdä lisäämällä eri verkko-osoitteita saman IP-osoitteen ja portin alle.
-	Nimi-pohjainen virtuaalipalvelin on usein yksinkertaisempi kuin IP-pohjainen, koska silloin riittää, että konfiguroi DNS-palvelimen ohjaamaan liikenteen vain yhteen IP-osoitteeseen. Tällöin pitää vain konfiguroida Apache tunnistamaan eri nimiä. Nimi-pohjainen verkkopalvelin säästää myös IP-osoitteita, joita on vain rajattu määrä.

Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
-	Yhteen IP-osoitteeseen voidaan sisällyttää useampi eri nettisivu.
-	Asenna ensin web palvelin eli Apache → Lisää uusi nimi-pohjainen virtuaali host. → Luo web sivu normaali käyttäjänä. → Testaa sivun toimivuus

## a) Webpalvelimen testaus
Testataan vastaako webpalvelin localhost-osoitteesta. Kirjoitetaan selaimen hakukenttään localhost ja sieltä pitäisi aueta sivu.

![Näyttökuva 2025-02-03 145252](https://github.com/user-attachments/assets/a9ebbf54-251a-408a-bf1d-60dcea97414b)


Selaimesta aukesi viime tunnilla default-sivun tilalle vaihdettu nettisivu, joten webpalvelin vastaa.

Apache mahdollistaa tämän, että samalla IP-osoitteella on useampi eri domain-nimi. Apache asennetaan alla näkyvän komennon avulla.

![Näyttökuva 2025-02-03 145950](https://github.com/user-attachments/assets/ab88d4e7-ed4c-434a-8568-305e6781e18e)


## b) Loki
Siirrytään ensin oikeaan hakemistoon eli /var/log/apache2. Apache2 lokitietoihin pääsee ainoastaan sudo-komennon avulla. Alimmalla rivillä on listattuna kaikki apache2 lokihakemiston tiedostot.

![Näyttökuva 2025-02-03 150459](https://github.com/user-attachments/assets/eb2182f4-1626-458b-9d67-4e5cf67165bf)


Käydään lataamassa äsken avattu nettisivu uudestaan ja katsotaan sen jälkeen lokitietoja. Alla olevalla komennolla saadaan näkyviin access.log -tiedoston viimeiset kymmenen riviä.

![Näyttökuva 2025-02-03 151426](https://github.com/user-attachments/assets/0acee7d9-e240-48c8-804d-c1727b7354b4)

![Näyttökuva 2025-02-03 165348](https://github.com/user-attachments/assets/e16e85c1-fe4e-422a-b05e-15768126dc5a)


Selitykset: (Lähde: https://www.sumologic.com/blog/apache-access-log/)

[28/Jan/2025:20:09:27] pyynnön päivämäärä ja kellon aika

”GET / http/1.1” pyynnön tyyppi ja resurssi jota pyydetään

200 http vastaus status koodi

3380 palautettavan objektin koko

”http://localhost/” osoite josta pyyntö on peräisin

”Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0”  yksilöi informaation selaimesta, jota client käyttää

## c) Etusivun vaihto
Siirrytään hakemistoon, jossa nähdään kaikki saman IP-osoitteen alle lisätyt domain-nimet. Lisätään sinne uusi domain hattu.example.com

![Näyttökuva 2025-02-03 154810](https://github.com/user-attachments/assets/30bee7a4-f567-423e-a535-4640f37dafb0)

(Edit: 11.3.2025 Konfiguraatiotiedostoon merkatut hakemistot ovat väärin. xubuntu -hakemiston tilalla pitäisi olla ronja -hakemisto eli käyttäjän oma kotihakemisto.)

![Näyttökuva 2025-02-03 154713](https://github.com/user-attachments/assets/7915f301-31ea-43c7-bc66-cc5b6914ce6b)


Aktivoidaan uusi verkkosivu.

![Näyttökuva 2025-02-03 154908](https://github.com/user-attachments/assets/bb01821f-e931-4256-a646-d06c9b172617)


Luodaan uudelle sivulle oma hakemisto ja tiedosto johon sen sisältöä voi muokata.

![Näyttökuva 2025-02-03 155733](https://github.com/user-attachments/assets/1c4ba8b7-a04d-4ec7-9216-687985a07a4f)

![Näyttökuva 2025-02-03 161042](https://github.com/user-attachments/assets/b211431f-fc2d-4c41-b700-f5d2f57c589e)



Testataan sivun toimivuutta lisäämällä sivun sisällöksi alla oleva teksti.

![Näyttökuva 2025-02-03 161106](https://github.com/user-attachments/assets/a768dc27-1a57-476c-b02e-758d6fb44e81)


Testataan sivun toimivuus. Sivu toimii, koska juuri lisätty testiteksti näkyy.

![Näyttökuva 2025-02-03 161241](https://github.com/user-attachments/assets/ee9f9f35-1ce7-46f3-b34e-1e3b1e1676c0)


## e) html5
Muokataan edellisessä osiossa luotua index.html sivua siten, että se on validi Tero Karvisen ohjeen mukaan (Karvinen Tero 2012: Short HTML5 page: https://terokarvinen.com/2012/short-html5-page/).

![Näyttökuva 2025-02-03 164113](https://github.com/user-attachments/assets/617a53c1-ed88-44f6-bbb2-0328dfdc0492)


Sivun sisältö päivittyy.

![Näyttökuva 2025-02-03 170921](https://github.com/user-attachments/assets/ddf7799e-fe73-4f43-898b-088f1f1a2ac0)


Testataan onko se validi sivulla https://validator.w3.org/

![Näyttökuva 2025-02-03 163736](https://github.com/user-attachments/assets/876f5bff-5fa5-4129-8678-d30305a1cf74)


Haetaan tiedosto.

![Näyttökuva 2025-02-03 163804](https://github.com/user-attachments/assets/002c01b5-02da-4d45-9cb3-6dd6f95d6c53)


Ei valituksia, joten sivu on validi.

![Näyttökuva 2025-02-03 164226](https://github.com/user-attachments/assets/4165aa15-1cb2-4eb7-bee2-437b6877d84f)


## f) Curl
curl -komento näyttää halutun verkkosivun html-koodin (https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/).

![Näyttökuva 2025-02-03 164631](https://github.com/user-attachments/assets/16b21d3e-42a1-45ea-9710-590276d9fade)


curl -I näyttää halutun verkkosivun otsakkeen, joka on siis sivun metadataa. Alla olevasta kuvasta voidaan esimerkiksi nähdä millä palvelimella verkkosivu toimii, milloin sitä on viimeksi muokattu ja mikä on sen sisällön tyyppi.

![Näyttökuva 2025-02-03 164653](https://github.com/user-attachments/assets/cd198cb2-0bdc-43c7-a47e-319b90ba7cc3)


## Lähteet
Karvinen Tero: Linux Palvelimet 2025 alkukevät: https://terokarvinen.com/linux-palvelimet/#h3-hello-web-server

Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: https://httpd.apache.org/docs/2.4/vhosts/name-based.html

Karvinen Tero 2012: Short HTML5 page: https://terokarvinen.com/2012/short-html5-page/

GeeksforGeeks 2024: curl Command in Linux with Examples: https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/

Sumo logic 2020: Understanding the Apache Access Log: View, Locare and Analyze: https://www.sumologic.com/blog/apache-access-log/

Muokattu 11.3.2025 lähdeviitteitä ja konfiguraatiotiedoston sisältöä
