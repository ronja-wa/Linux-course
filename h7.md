# h7

## a) Hei maailma!

Tehdään skriptejä Tero Karvisen ohjeen avulla (https://terokarvinen.com/2007/12/04/shell-scripting-4/).

Asennetaan python ja java komennoilla:

sudo apt-get install openjdk-17-jdk

sudo apt-get install python3

Tehdään “Hei maailma” -ohjelmat bashilla, pythonilla ja javalla. Luodaan microlla bash-skripti ja tallennetaan nimellä heimaailma.sh. Tiedoston ensimmäinen rivi kertoo, millä kielellä koodi tulkitaan.

![image](https://github.com/user-attachments/assets/c0449449-220f-4475-8629-45ee155cbeb3)

Luodaan microlla python -ohjelma.

![image](https://github.com/user-attachments/assets/663eb1fd-434e-4e30-8ba2-518a18900702)

Luodaan microlla java -ohjelma.

![image](https://github.com/user-attachments/assets/0fff9fb4-58e9-4de9-bb85-4ccbd47f0ea4)

Java pitää myös kääntää, jotta se on ajettavissa. Tehdään se alla olevalla komennolla.

![image](https://github.com/user-attachments/assets/263502a0-2321-4279-ac2f-6d1584da9282)

Muokataan käyttöoikeuksia siten, että äsken luotuja ohjelmia saa ajaa kaikki.

![image](https://github.com/user-attachments/assets/5e6b3fe8-777a-44f3-9306-e9739f1738ac)

Testataan toimiiko uudet ohjelmat.

![image](https://github.com/user-attachments/assets/f8d53a52-c411-4976-b09d-75ac579385d4)

![image](https://github.com/user-attachments/assets/6d51a62d-804f-44bc-b7c6-86c7b1e86087)

![image](https://github.com/user-attachments/assets/add6fc12-069d-46d6-ac81-861b1f4ad4cb)


## c) Oma ohjelma

Luodaan tervehdys.sh -skripti käyttäjällä ronja.

![image](https://github.com/user-attachments/assets/dfa7ad93-a2f0-41cc-819d-3190ddc4f083)

Lisätään tähänkin skriptiin ajo-oikeus kaikille komennolla

chmod a+x tervehdys.sh

Siirretään se alla näkyvään hakemistoon, jolloin komennon tervehdys.sh  pitäisi toimi kaikilla käyttäjillä.

![image](https://github.com/user-attachments/assets/b6263b29-5537-4bee-9ff1-9e29e50fbe60)

Testataan komento käyttäjällä ronja ensin.

![image](https://github.com/user-attachments/assets/5576805d-be10-4bf2-b90f-a0fd4b61f0f5)

Kirjaudutaan testeri -käyttäjälle, ja kokeillaan toimiiko komento myös sillä.

![image](https://github.com/user-attachments/assets/9ed654bc-0a4c-4298-8a6b-70f07271b7b2)


## d) Laboratorio tehtävä
https://terokarvinen.com/2018/arvioitava-laboratorioharjoitus-linux-palvelimet-ict4tn021-8-maanantai-alkukevat-2018-5-op/?fromSearch=laboratorio%202018

Lisätään uudet käyttäjät työntekijöille Jorma Mähkylä, Pekka Hurma, Ronaldo Smith.

![image](https://github.com/user-attachments/assets/dbb1d115-d600-4be1-8f72-5f2926040548)

Lisätään kaikille salasanat ja koko nimi. Muut tiedot voi jättää tyhjäksi.

![image](https://github.com/user-attachments/assets/c5fca2af-e1cb-4902-b9ab-c92dd723f5fe)

Uudet käyttäjät näkyvä kotihakemistossa.

![image](https://github.com/user-attachments/assets/bc777315-20be-4979-a85e-20d74fd4570d)

Tehdään jokaiselle käyttäjälle oma kotisivu. Siirrytään kansioon /etc/apache2/sites-available. Lisätään sinne jokaiselle käyttäjälle oman kotisivun konfiguraatiotiedosto.

![image](https://github.com/user-attachments/assets/b0bc09dc-0fe1-45f7-8395-85b807eec16b)

![image](https://github.com/user-attachments/assets/909289e6-7add-4994-9cd2-6011218b3130)

![image](https://github.com/user-attachments/assets/ce08fcf5-d99f-4395-b036-2f43ef3be9de)

Laitetaan kaikki äsken luodut nettisivut päälle.

![image](https://github.com/user-attachments/assets/d42f753c-9233-4514-9d60-4e8c09241443)

Käynnistetään vielä apache uudestaan.

![image](https://github.com/user-attachments/assets/ff8c1393-6fa1-4f22-96bf-7daa08bab835)

Luodaan kotisivuille omat hakemistot

![image](https://github.com/user-attachments/assets/d7bab92d-9563-4c1f-b146-6d0ca3c3c319)

Jotta jokainen käyttäjä pystyy itse muokkaamaan kotisivujaan, pitää jokaisen käyttäjän hakemiston omistajuus siirtää rootilta käyttäjälle. Se onnistuu käyttäjällä ronja, koska se on lisätty myös sudo-ryhmään, jolloin on pääkäyttäjän oikeudet. Vaihdetaan hakemiston omistajuus komennolla

sudo chown -R jorma:jorma  /home/jorma

![image](https://github.com/user-attachments/assets/78a357eb-5ef1-4bf4-a02b-8b215056e576)

Tehdään sama myös muille käyttäjille.

Käydään tekemässä jokaiselle oma kotisivu Tero Karvisen html-ohjeen avulla. (https://terokarvinen.com/2012/short-html5-page/?fromSearch=html5)

![image](https://github.com/user-attachments/assets/b3a662c6-8328-421e-92b7-adb69efc0488)

## Lähteet

Karvinen 2007: Shell Scripting: https://terokarvinen.com/2007/12/04/shell-scripting-4/

Karvinen 2025: Linux kevät 2025: https://terokarvinen.com/linux-palvelimet/

Karvinen 2012: Short HTML5 page: https://terokarvinen.com/2012/short-html5-page/?fromSearch=html5

