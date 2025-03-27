# H2 Komentaja Pingviini
## x) Command line basics revisited
Karvinen Tero 2020, Command line basics revisited: https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited
-	Komentorivin avulla voidaan liikkua ja tutkia hakemistoa eli mennä eri kansioiden sisälle ja etsiä niistä tiedostoja.
-	Komentoriviin pitää asentaa jokin tekstieditori, jotta uusia tiedostoja voi luoda sekä muokata. Näitä on esim. pico ja nano.
-	Komentorivillä voi avata SSH-etäyhteyden jollekin toiselle koneelle ja ohjata sitä samoilla komennoilla kuin ohjaisi omaa konettakin.
-	Kaikkia komentoja ei tarvitse muistaa ulkoa tai välttämättä edes tietää. Tabulaattorilla voi täyttää vajaan komennon ja se antaa kaikki mahdolliset vaihtoehdot sille, mitä voi seuraavaksi kirjoittaa.
-	Komennot, jotka vaativat korkeampia oikeuksia, voidaan suorittaa ’sudo’ komennon avulla.

## a) Micron asennus
Asennetaan micro -tekstieditori. Koska olen jo asentanut sen, saadaan komentoon vastaukseksi alla näkyvä teksti.

![Näyttökuva 2025-01-27 160357](https://github.com/user-attachments/assets/340d4996-a17b-4b9a-9418-8077ca933136)

## b) Apt
### Traceroute
Asennetaan traceroute, mikä avulla voidaan selvittää reitti, mitä pitkin paketit kulkevat tiettyyn koneeseen, ja kuinka kauan jokaiseen hyppyyn kuluu aikaa. Asennetaan se alla näkyvällä komennolla.

![Näyttökuva 2025-01-27 160254](https://github.com/user-attachments/assets/36211129-531d-4625-a46d-9d491d987af2)


Testataan sitä Haaga-Helian verkkosivuille.

![Näyttökuva 2025-01-27 160331](https://github.com/user-attachments/assets/ce39638b-1f19-4e83-a092-e90316c9ec8c)


Kuvassa näkyvät tähdet voivat tarkoittaa sitä, että reititin on liian kiireinen, jolloin se ei sen vuoksi vastaa. Jotkin organisaatiot voivat myös konfiguroida omat reitittimensä siten, että ne eivät vastaa tracerouteen, koska ne eivät halua, että muut voivat selvittää niiden sisäisen verkon toimintaa liian yksityiskohtaisesti. (Lähde: https://www.baeldung.com/linux/traceroute-three-stars#2-some-routers-dont-want-to-respond)

### Tree
Asennetaan seuraavaksi Tree -ohjelma alla näkyvällä komennolla. Sen avulla voidaan näyttää hakemisto puumaisessa muodossa.

![Näyttökuva 2025-01-27 161842](https://github.com/user-attachments/assets/04b63971-f62d-4c47-b92a-e04e2087db12)

![Näyttökuva 2025-01-27 161958](https://github.com/user-attachments/assets/263a2de1-c6d0-4500-95d5-30142a2aa624)


### Cowsay
Asennetaan viimeiseksi cowsay -ohjelma, jonka avulla saa komentoriville lehmän, jolla on puhekupla. Tätä käyttää ainakin kurssin opettaja Tero Karvinen kertomaan, monelta tunti jatkuu tauon jälkeen.

![Näyttökuva 2025-01-27 162459](https://github.com/user-attachments/assets/35ca33b7-a500-48a7-a83b-3aee09fbf49b)

![Näyttökuva 2025-01-27 162534](https://github.com/user-attachments/assets/d7ce696e-447d-4ba9-af74-ebaf14a21e36)


## c) Important directories
cd .. komennolla pääsee juurihakemistoon, mikä on kaikista ylimpänä.

![Näyttökuva 2025-01-27 163251](https://github.com/user-attachments/assets/c050d3d2-48d7-42b7-8b5a-f2f120e9a31b)


Juurihakemistosta pääseen home -hakemistoon cd home -komennolla, josta löytyy oma käyttäjä.

![Näyttökuva 2025-01-27 163413](https://github.com/user-attachments/assets/c9d46a62-4e61-40d1-b733-0dab7704df41)


/home/ronja hakemistoon pääsee alla näkyvällä komennolla. Tähän hakemistoon voi lisätä dataa, joka säilyy pysyvästi.

![Näyttökuva 2025-01-27 163546](https://github.com/user-attachments/assets/0c2bb8ff-f12f-4f29-bfd2-6e9a40cb629f)


/etc/ hakemistoon pääsee juurihakemistosta. Siellä säilytetään asetuksia.

![Näyttökuva 2025-01-27 163926](https://github.com/user-attachments/assets/842e4538-c421-45cd-8644-dcccfb6a2b6a)


/media/ -hakemistoon pääsee myös juurihakemistosta. Siellä säilytetään mediaa, kuten CD-levyjen sisältöä.

![Näyttökuva 2025-01-27 164115](https://github.com/user-attachments/assets/c92ecdb2-9491-4912-930f-4efca2fa348f)


/var/log/  -hakemistossa säilytetään lokitietoja.

![Näyttökuva 2025-01-27 164333](https://github.com/user-attachments/assets/27dcd732-e687-4d14-9d13-c15d6d97a70b)


## d) Grep
Grep komennon avulla voidaan etsiä tiedostoista yhdenmukaisuuksia ja samoja rakenteita.
Sen avulla voi etsiä tietyn sanan tiedostosta.

![Näyttökuva 2025-01-27 165849](https://github.com/user-attachments/assets/fa8bf608-7b47-4051-87d7-cec10423cbeb)


Kun lisää edelliseen komentoon -n, saadaan myös selville rivinumerot, joilla kyseinen sana on.

![Näyttökuva 2025-01-27 170012](https://github.com/user-attachments/assets/c5c0de7d-6d1b-4e0b-9852-5a4f9d825e19)


## e) Putki
| -merkki tarkoittaa putkea. Sen avulla voidaan yhdistää kaksi tai useampi komento. 

(Lähde: https://www.geeksforgeeks.org/piping-in-unix-or-linux/)

 Alla olevassa kuvasta näkee, että ls -komento listaa kaikki kyseisessä kansiossa olevat tiedostot. Kun siihen lisätään putki ja grep komento, saadaan listattua ainoastaan ne tiedostot, joiden nimessä on ’ko’.
 
![Näyttökuva 2025-01-27 170801](https://github.com/user-attachments/assets/067ccd9f-34bd-438e-88a6-c9d582478141)


## f) Rauta
Asennetaan ensin lshw.

![Näyttökuva 2025-01-27 171311](https://github.com/user-attachments/assets/7b6f2a69-bc5c-4cf3-b026-58fa6fa60171)

![Näyttökuva 2025-01-27 171503](https://github.com/user-attachments/assets/640c3b16-5121-47d0-83e6-47d6992dfd5e)
![Näyttökuva 2025-01-27 171526](https://github.com/user-attachments/assets/bf38fc65-31bc-44f7-9c3a-5ee08c5a5c3d)


-	Kone on VirtualBoxin virtuaalikone, jolla on Linuxin käyttöjärjestelmä
-	BIOS muisti on 128 KiB
-	RAM muisti on 4 GiB
-	Koneessa, jolla virtuaalikone on luotu, on suorittimena AMD Ryzen 9 5900HS Creator Edition
-	SVGA II Adapter on näytönohjain
-	enp0s3 on virtuaalikoneen verkkokortti, joka tarvitaan mahdollistamaan internettiin pääsy.




## Lähteet
Tero Karvinen: https://terokarvinen.com/linux-palvelimet/#h2-komentaja-pingviini
Tero Karvinen: https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited
Baeldung 18.3.2024: Meaning of *** in the Output of traceroute: https://www.baeldung.com/linux/traceroute-three-stars#2-some-routers-dont-want-to-respond
Oracle 27.7.2022 man pages section 1: User Commands: https://docs.oracle.com/cd/E88353_01/html/E37839/grep-1.html
Geeks for geeks 22.7.2024 Pipin in Unix or Linux: https://www.geeksforgeeks.org/piping-in-unix-or-linux/

28.1.2025 muokattu a-kohtaa: Vaihdettu väärä kuva oikeaan.
11.3..2025 muokattu lähdeviitteitä
