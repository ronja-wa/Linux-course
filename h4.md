# h4 Maailma kuulee
## x)
Lehto Susanna: Teoriasta käytäntöön pilvipalvelimen avulla (h4) 14.2.2022: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/
a) Pilvipalvelimen vuokraus ja asennus

o	Ensin täytyy vuokrata julkinen palvelin, jolle voi rakentaa oman websivun. Sivulla pääsee vierailemaan kuka tahansa internetissä, kunhan vain tietää IP-osoitteen. Sen jälkeen vuokrataan nimi, jolloin websivu saa domain-nimen.

d) Palvelin suojaan palomuurilla

o	Palvelimelle pitää asentaa palomuuri, joka estää kaikki sisään tulevan ja ulos lähtevän liikenteen. Sen jälkeen avataan vain tarvittavat portit, jotta palvelimella oleva websivu on saatavilla internetissä.

e) Kotisivut palvelimelle

o	Kotisivut luodaan samalla tavalla kuin edellisessä tehtävässä h3. Palvelimelle pitää ensin asentaa Apache webpalvelin. Sen jälkeen testisivu tulee korvata ja luoda palvelimelle uusi kotisivu.

f) Palvelimen ohjelmien päivitys

o	Päivitetyt ohjelmat mahdollistavat paremman tietoturvan. Ohjelmat päivitetään seuraavilla komennoilla:

$ sudo apt-get update

$ sudo apt-get upgrade

$ sudo apt-get dist-upgrade


Karvinen Tero 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
-	Ensin tulee vuokrata virtuaalipalvelin (esim. DigitalOcean tai UpCloud, tai ilmaiseksi GitHub Education student pack).
-	Valitse palvelimen fyysiseksi sijainniksi jokin valtio EU:n sisältä, jotta lainsäädäntö sama kuin Suomessa.
-	Käytä vain hyviä salasanoja tai luo SSH Key.
-	Kun virtuaalipalvelin on pystyssä, pistä ensin palomuuri päälle ja avaa vain tarvittavat portit.
-	Tee uusi pääkäyttäjä virtuaalipalvelimelle ja sen jälkeen ota Root -käyttäjä pois käytöstä.
-	Lopuksi päivitä kaikki ohjelmistot.
-	Nyt virtuaalipalvelin on valmis käytettäväksi.


## a) Virtuaalipalvelimen vuokraus
Vuokraan virtuaalipalvelimen UpCloudista eli osoitteesta upcloud.com. Luodaan ensin käyttäjä ja lisätään omat tiedot.
Kun omat henkilötiedot ja maksukortti on lisätty, voidaan ottaa käyttöön uusi palvelin. Painetaan ”Deploy your services” kohdasta nappia ”+ Deploy now” ja valitaan valikosta ”Server”.

![image](https://github.com/user-attachments/assets/1392e14f-10f5-4570-96d6-5853d5e42d95)

![image](https://github.com/user-attachments/assets/f2a60a15-895c-456b-8a18-5d8b2c90b31a)


Seuraavaksi valitaan palvelimen tekniset yksityiskohdat. Muistia tulisi olla vähintään 1GB, joten halvin vaihtoehto riittää.

![image](https://github.com/user-attachments/assets/879d06ae-53c6-4b9b-ae95-dbeeb3da25c2)


Vaihdetaan tallennustila salatuksi, jolloin tietoturva on parempi.

![image](https://github.com/user-attachments/assets/29de0a63-b00d-488d-9bfc-de6e78137c2a)


Käyttöliittymäksi valitaan Debian GNU/Linux 12 (Bookworm).

![image](https://github.com/user-attachments/assets/54e2ebd2-4d2e-4baf-9c62-1e124d31faf4)


Kirjautumistavaksi valitaan SSH-avain.

![image](https://github.com/user-attachments/assets/03cacf9e-24e3-4c8a-95e6-2915d34c2894)


Siirrytään omalle virtuaalikoneelle ja luodaan siellä SSH-avain. Asennetaan aluksi alla näkyvä ohjelma.

![image](https://github.com/user-attachments/assets/42a65f01-3f15-4d7d-934b-d9bd40eaec25)


Luodaan avain komennolla ssh-keygen. Painetaan enteriä, jolloin avain luodaan kansioon /home/ronja/.ssh/id_rsa. Painetaan kahdesta seuraavastakin kohdasta suoraa enteriä, jolloin avainta ei suojata.

![image](https://github.com/user-attachments/assets/ed69b924-1732-48a8-b1c2-effcc90b2745)


Avain on nyt luotu. Käydään kopioimassa avainparin julkinen avain. Siirrytään alla näkyvään hakemistoon. Nähdään, että siellä on kaksi tiedostoa. id_rsa on salainen avain ja id_rsa.pub on julkinen avain.

![image](https://github.com/user-attachments/assets/e23411fd-e1cb-4ce5-b193-85250208aaca)


Avataan tiedosto microlla.

![image](https://github.com/user-attachments/assets/59318687-e580-4cd0-8fab-b521f60abd40)

![image](https://github.com/user-attachments/assets/06f5d8ae-d093-4818-994e-91e0bde9a833)


Lisätään julkinen avain UpCloudiin.

![image](https://github.com/user-attachments/assets/229b91ca-7560-4c32-8a74-f8a0c8425ffc)


Nyt virtuaalipalvelin on valmis käyttöönottoa varten. Rullataan sivulla alas ja painetaan ”Deploy” -nappia.



## Virtuaalipalvelimen valmistelu käyttöönottoa varten
Siirrytään takaisin VirtualBoxin virtuaalikoneelle ja avataan terminaali. Otetaan juuri luotuun virtuaalipalvelimeen SSH-yhteys komennolla

ssh root@80.69.173.92

Root on palvelimen käyttäjä, jolla on täydet oikeudet palvelimen hallintaan. 80.69.173.92 on palvelimen IPv4 -osoite.

![image](https://github.com/user-attachments/assets/2b41f7bb-761c-43a0-9d16-b28d08895efa)


SSH-yhteyden luominen onnistui.

![image](https://github.com/user-attachments/assets/edd50f57-0591-4ec3-b44f-7b2c44667365)


Ensimmäisenä haetaan lista päivityksistä ja päivitetään kaikki tarvittava komennoilla

sudo apt-get update

sudo apt-get upgrade

Seuraavaksi asennetaan palvelimelle palomuuri komennolla 

sudo apt-get install ufw

![image](https://github.com/user-attachments/assets/fc29e0fa-7f45-4ad9-9121-911db94a7109)


Palomuurissa on tällä hetkellä kaikki portit kiinni eli tietoliikennettä ei kulje palvelimelta ulos eikä sisään. Avataan ensin portti 22 SSH-yhteyttä varten komennolla 

sudo ufw allow 22/tcp

Sen jälkeen otetaan palomuuri käyttöön komennolla

sudo ufw enable

Avaamalla ensin SSH-portin yhteys palvelimeen ei katkea, kun palomuuri laitetaan päälle.

sudo ufw allow 22/tcp

![image](https://github.com/user-attachments/assets/4c2f11d9-4b73-4552-9f10-4d76763bf4ba)


Lisätään palvelimelle uusi käyttäjä komennolla
	
 sudo adduser ronja

![image](https://github.com/user-attachments/assets/d5a2e85e-a577-40e7-a1b9-b605c20304c9)


Valitaan hyvä salasana ja syötetään se kaksi kertaa. Annetaan oma nimi. Muihin kysymyksiin voi olla vastaamatta.

![image](https://github.com/user-attachments/assets/031ec3b4-a029-4e2b-a590-d22d16b36b1c)


Uusi käyttäjä on nyt luotu.

Tehdään käyttäjästä ronja pääkäyttäjä alla näkyvällä komennolla.

![image](https://github.com/user-attachments/assets/6063eee1-8e2f-48fe-9881-2732001219c6)


Jotta ronja -käyttäjällä voidaan kirjautua palvelimelle sisään, täytyy julkinen ja salainen avain kopioida tälle käyttäjälle. Se tehdä alla näkyvien komentojen avulla.

![image](https://github.com/user-attachments/assets/690c28ee-93fe-4c38-8246-8bbadc20a9df)


Testataan seuraavaksi onnistuuko kirjautuminen ronja -käyttäjälle. Poistutaan ensin palvelimelta takaisin omalle virtuaalikoneelle exit -komennolla. Sen jälkeen koitetaan kirjautua komennolla ssh ronja@80.69.173.92.

![image](https://github.com/user-attachments/assets/090fd6f7-886a-4e0c-8722-1635de116ebe)

![image](https://github.com/user-attachments/assets/a34f491d-8cf4-4339-88af-658ce24e3cac)


Kirjautuminen onnistui. Nyt voidaan sulkea root -käyttäjä alla näkyvällä komennolla.

![image](https://github.com/user-attachments/assets/081f56ec-56d6-4835-b551-d03f08d5fe65)


Estetään myös root -käyttäjällä SSH-yhteyden avaaminen palvelimelle alla näkyvällä komennolla. Tämä komento siirtää komennossa näkyvän ensimmäisen hakemiston sisällön toiseen hakemistoon, jolloin estetään root -käyttäjältä mahdollisuus ottaa SSH-yhteys palvelimeen.

![image](https://github.com/user-attachments/assets/ca59ba26-ab82-4927-923e-0bbe4f0a6670)



## Webpalvelin
Asennetaan palvelimelle Apache webpalvelin.

![image](https://github.com/user-attachments/assets/0a367283-28c3-48da-98ee-4fb6049962fb)


Avataan palomuurista portti 80 http:tä varten, jotta palvelimen testisivu näkyy selaimessa.

![image](https://github.com/user-attachments/assets/fd000ebf-f407-4556-9459-8cd55ca176e1)


Testataan näkyykö testisivu. Kirjoitetaan hakukenttään käytettävä protokolla ja palvelimen IP-osoite:

![image](https://github.com/user-attachments/assets/43b7c63f-a028-46cb-b654-1c06dfb9bef1)


Testisivut aukesivat.

![image](https://github.com/user-attachments/assets/a340b10e-6b27-4549-8da2-2bc1c8b7785b)


Mennään alla näkyvään hakemistoon ja luodaan konfiguraatiotiedosto ronja.testi.com.conf

![image](https://github.com/user-attachments/assets/8bbfe99e-6f44-491e-8c47-a2fab47ec3d3)

![image](https://github.com/user-attachments/assets/ed5e28a6-da21-4fa4-8460-43702d95438f)


Vaihdetaan juuri luotu uusi sivu testisivun tilalle.

![image](https://github.com/user-attachments/assets/dbe94160-8178-4db0-9e84-5142125c072a)


Luodaan hakemisto /home/xubuntu/publicsites/ronja.testi.com/index.html

![image](https://github.com/user-attachments/assets/eb71ca08-ff1d-4e0a-afa5-97f931f8dd52)

![image](https://github.com/user-attachments/assets/e2805f09-8f3c-426f-8757-3f2010ef3f48)


Kirjoitetaan nettisivuille jokin teksti.

![image](https://github.com/user-attachments/assets/d189502e-a524-47f7-bd7a-6344c47e4bf5)


![image](https://github.com/user-attachments/assets/c325dcdd-8e23-4d20-9e76-e2f5eec7799f)



Kävin testaamassa oliko nettisivu vaihtunut, mutta se ei ollutkaan. Kävin sen jälkeen testaamassa vaihtuisiko se, jos lisäisin tähden (*) tilalle palvelimen IP-osoitteen konfiguraatiotiedostoon. Tämä toimi.


![image](https://github.com/user-attachments/assets/14831702-01fa-4cb1-b105-5e2ff2e56082)

![image](https://github.com/user-attachments/assets/2982ee70-64a5-401e-9acd-392a0f682584)

 
## Lähteet

Lehto Susanna: Teoriasta käytäntöön pilvipalvelimen avulla (h4) 14.2.2022: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

Karvinen Tero 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/

Karvinen Tero 2025: Linux Palvelimet 2025 alkukevät: https://terokarvinen.com/linux-palvelimet/#h4-maailma-kuulee





