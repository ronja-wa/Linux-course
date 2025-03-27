# Oma Linux
## Raportin kirjoittaminen
Karvinen Tero: 4.6.2006 Raportin kirjoittaminen https://terokarvinen.com/2006/raportin-kirjoittaminen-4/
-	Raportoinnin avulla jonkun toisen henkilön on mahdollista toteuttaa samat toimenpiteet ja päätyä samoihin lopputuloksiin kuin itse. Sen pitää siis olla riittävän yksityiskohtainen, jotta se olisi toistettavissa.
-	Täsmällisessä raportissa kerrotaan käytetyt komennot, työvaiheisiin kulunut aika, työkalut, onnistumiset ja epäonnistumiset sekä virheilmoitukset ja mahdolliset ratkaisut niihin.
-	Jotta raportti olisi mahdollisimman helppolukuinen, siinä tulee käyttää väliotsikoita, välttää kirjoitusvirheitä, kirjoittaa julkaisukanavaan sopivalla tavalla sekä halutessaan kirjoittaa raportin alkuun tiivistelmän.
-	Raportissa tulee olla lähdeluettelo ja lähteisiin pitää viitata tekstissä.
-	Täysin kiellettyä on tehdä valheellinen raportti, plagioida ja käyttää luvattomasti muiden kuvia.

## Vapaa ohjelmisto
GNU: 1.1.2024  What is Free Software? https://www.gnu.org/philosophy/free-sw.html
-	Vapaa ohjelmisto tarkoittaa sitä, että käyttäjällä on vapaus käyttää, kopioida, jakaa, tutkia, muokata ja parannella ohjelmistoa. Tämän vastakohta on omisteinen ohjelmisto.
-	Ohjelmisto on vapaa, jos se täyttää neljä kriteeriä:
o	Ohjelmistoa voidaan käyttää mihin tarkoitukseen tahansa.
o	Ohjelmiston toimintaa voidaan vapaasti tutkia, ja muokata omiin käyttötarkoituksiin sopiviksi.
o	Ohjelmistosta voidaan vapaasti jakaa kopioita muille.
o	Ohjelmistosta voidaan vapaasti jakaa itse muokkaamia versioita muille.
-	Vapaan ohjelmiston tulee olla käytettävissä myös kaupallisiin tarkoituksiin.

## Virtuaalikoneen asennus
Asennetaan ensin Debianin jakelupaketti Tero Karvisen ohjeen (https://terokarvinen.com/2021/install-debian-on-virtualbox/) mukaisesti. Sen jälkeen Virtualbox, jotta voidaan luoda uusi virtuaalikone, jonne asennetaan Linux. Asennetaan versio debian-live.12.9.0-amd-xfce.iso, joka löytyy osoitteesta https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/.

Tiedoston lataukseen meni noin 40 minuuttia.
Asennetaan seuraavaksi VirtualBox osoitteesta https://www.virtualbox.org/wiki/Downloads. Valitaan Windowsille sopiva versio, joka näkyy alla. Tiedoston lataukseen kului noin kaksi minuuttia.
 ![Näyttökuva 2025-01-20 151308](https://github.com/user-attachments/assets/43c362a0-a30f-48fb-87da-4919518c9e9f)
VirtualBox on nyt asennettu. Siinä kesti noin viisi minuuttia. Painetaan aloitusnäkymästä ”Expert Mode” päälle ja sen jälkeen valitaan ”New”, josta päästään luomaan uusi virtuaalikone.
Tehdään virtuaalikoneeseen alla näkyvät konfiguraatiot.
![Näyttökuva 2025-01-20 152625](https://github.com/user-attachments/assets/ce5f5be2-22c9-400e-82ea-203bcf98393f)
![Näyttökuva 2025-01-20 152808](https://github.com/user-attachments/assets/98cc275e-27d1-401c-aba4-fcafe843a358)
![Näyttökuva 2025-01-20 152824](https://github.com/user-attachments/assets/f3f976dc-150a-4138-8746-b3c6d28ae7ee)
Virtuaalikone on nyt luotu.
![Näyttökuva 2025-01-20 153016](https://github.com/user-attachments/assets/ad870a1e-f759-4c6e-9163-ac3cb108b446)
Tuplaklikataan virtuaalikone päälle.
![Näyttökuva 2025-01-20 153119](https://github.com/user-attachments/assets/aebedebd-1ce4-4e38-9aa2-8751ce4e7838)
Valitaan Boot menusta Live system (amd64).
![Näyttökuva 2025-01-20 154644](https://github.com/user-attachments/assets/4433c90e-080c-460d-b3d3-cd61f2c85ffe)
Virtuaalikone ei suostunutkaan käynnistymään. Tuli alla näkyvä virheilmoitus.
![Näyttökuva 2025-01-20 153827](https://github.com/user-attachments/assets/38f571d5-587e-4fc0-89ad-0d348c3f2cf7)
Kokeilin uuden virtuaalikoneen luomista, jossa jätän ISO image -kohdan vielä tyhjäksi ja en laita rastia ”Skip Unattended Installation”.
![Näyttökuva 2025-01-20 154441](https://github.com/user-attachments/assets/c7111ed3-b60c-4ced-8486-c2c9dd1568d0)
Lisätään ISO image jälkikäteen asetuksista alla olevan kuvan mukaisesti.
![Näyttökuva 2025-01-20 154522](https://github.com/user-attachments/assets/6df96167-ea33-4076-a4d6-2dc6d2077f9d)
Nyt uusi virtuaalikone on luotu.
Virtuaalikoneiden kuvakkeiden yläreunassa on eri numerot, joten uudessa koneessa on jokin erilailla. Testataan käynnistää se samalla tavalla kuin aikaisemmin.
![Näyttökuva 2025-01-20 154541](https://github.com/user-attachments/assets/c6879c8e-a66a-4862-9f60-fffdd7863058)
Virheilmoitusta ei tullut ja kone aukesi oikein.
![Näyttökuva 2025-01-20 155020](https://github.com/user-attachments/assets/c44be927-16ee-477d-ad21-40bab69527f8)
Web Browserilla pääsi Haaga-Helian nettisivuille, joten internet, hiiri, näppäimistö ja näyttö toimivat.
![Näyttökuva 2025-01-20 160903](https://github.com/user-attachments/assets/ff9abd1a-ab9f-4497-8619-83b97227da98)
Asennetaan seuraavaksi Debian.
![Näyttökuva 2025-01-20 161129](https://github.com/user-attachments/assets/d8d94f79-27c5-4433-a01e-8146ce02bdd9)
Tehdään alla olevien kuvien mukaiset valinnat asennusta varten.
![Näyttökuva 2025-01-20 161313](https://github.com/user-attachments/assets/f2e47911-60d1-451f-8dae-1c313c7fc98a)
![Näyttökuva 2025-01-20 161427](https://github.com/user-attachments/assets/9d9cf65d-dbdf-4b1a-a905-9267db28f387)
![Näyttökuva 2025-01-20 161549](https://github.com/user-attachments/assets/bd7e618c-7939-40f4-a794-a75340b7cc6a)
![Näyttökuva 2025-01-20 161646](https://github.com/user-attachments/assets/0cc8a9cb-3db3-4549-85c7-6cbc772c9e2b)
![Näyttökuva 2025-01-20 162204](https://github.com/user-attachments/assets/e739a9b9-cc87-4bd1-a649-bef457e5cae2)
![Näyttökuva 2025-01-20 162254](https://github.com/user-attachments/assets/066dae01-a680-4878-8cf7-d33b8727a64b)
![Näyttökuva 2025-01-20 163121](https://github.com/user-attachments/assets/9955760d-11a4-4d02-85da-53273843ef79)
Debian on nyt asennettu.
Kirjaudutaan sisään, kun kone käynnistyy uudelleen.
![Näyttökuva 2025-01-20 163531](https://github.com/user-attachments/assets/b2c8188d-f0a1-4ad9-a7cf-575bf77cb1b9)
Testataan koneen toimivuutta Web Browserilla. Kaikki toimi kuten piti.
Avataan seuraavaksi Terminal Emulator. Päivitetään lista siitä, mikä kaikki on saatavilla Debianille alla olevalla komennolla.
![Näyttökuva 2025-01-20 163906](https://github.com/user-attachments/assets/e8713ed2-171b-4b1f-88c1-058629dacf02)
![Näyttökuva 2025-01-20 164113](https://github.com/user-attachments/assets/11ecd869-6309-473a-9518-007331851edc)
![Näyttökuva 2025-01-20 164144](https://github.com/user-attachments/assets/b041a355-be29-4636-829e-b70875e8e953)
Päivitetään seuraavaksi kaikki ohjelmistot alla olevan komennon avulla.
![Näyttökuva 2025-01-20 164323](https://github.com/user-attachments/assets/1550d2c6-8bd0-4016-b3fa-54d2c3218434)
Asennetaan alla olevalla komennolla palomuuri.
![Näyttökuva 2025-01-20 164852](https://github.com/user-attachments/assets/ab03049d-506e-4a42-871e-ac902dd8333e)
Laitetaan alla olevalla komennolla palomuuri päälle.
![Näyttökuva 2025-01-20 164938](https://github.com/user-attachments/assets/df10d6c8-5727-417b-a738-d8ade36c93e4)
Käynnistetään sitten vielä kone uudelleen, jotta määritykset tulevat voimaan.
![Näyttökuva 2025-01-20 165126](https://github.com/user-attachments/assets/de8a132a-cc70-45ee-841b-01bd7cf8e63d)

## Lähteet
GNU: 1.1.2024  What is Free Software? https://www.gnu.org/philosophy/free-sw.html
Karvinen Tero: 4.6.2006 Raportin kirjoittaminen https://terokarvinen.com/2006/raportin-kirjoittaminen-4/
Karvinen Tero: 26.9.2024 Install Debian on Virtualbox - Updated 2024 https://terokarvinen.com/2021/install-debian-on-virtualbox/
Debian:  https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/
VirtualBox: https://www.virtualbox.org/wiki/Downloads
