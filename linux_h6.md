# h6

## x) Lue ja tiivistä

### Let's Encrypt 2024: How It Works

-	Let’s Encryptin ja ACME-protokollan avulla voidaan hankkia varmenne, jonka avulla nettisivu on todistetusti turvallinen.
-	Prosessi tehdään kahdessa vaiheessa:
o	Ensin pitää todistaa, että agentti eli verkkopalvelimella oleva ohjelmisto, joka vastaa varmenteiden hallinnasta, hallitsee verkkotunnusta.
o	Tunnistautumisen jälkeen varmenne voidaan allekirjoittaa ja myöntää.

### Lange 2024: Lego: Obtain a Certificate: Using an existing, running web server

-	Haasteen avulla varmistetaan, että palvelin hallitsee domainia.
-	Jos palvelin käyttää porttia 80, pitää suorittaa --http.webroot. Tämä kertoo, mihin hakemistoon haaste tallennetaan.
-	Hakemisto pitää olla löydettävissä julkisesti, jotta se on luettavissa.
	
### The Apache Software Foundation 2025: Apache HTTP Server Version 2.4 [Official] Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example

-	Verkkosivun konfiguraatiotiedostossa täytyy olla ainakin seuraavat tiedot:
  - Listen 443
  - <VirtualHost *: 443>
  - ServerName www.example.com
  - SSLEngine on
  - SSLCertificateFile “/path/to/www.example.com.cert”
  - SSLCertificateKeyFile “/path/to/www.example.com.key”
  - < /VirtualHost>



## a) Sertifikaatti

Käynnistetään Apache uudelleen.

![image](https://github.com/user-attachments/assets/3a4cc132-0fa0-417d-bd2a-3f2f5fec7266)

Varmistetaan, että nettisivu toimii.

![image](https://github.com/user-attachments/assets/c9f5ec15-eb98-4c32-a13e-a23a3d2551d5)

Asennetaan lego eli ohjelma, jonka avulla on mahdollista hankkia Let’s Encrypt -varmenne.

![image](https://github.com/user-attachments/assets/a1a6ee3c-f64c-4068-a779-5614c08ff823)

Suoritetaan alla näkyvä testikomento.

![image](https://github.com/user-attachments/assets/01096a31-b4cc-47e2-a7f7-5d7e500c150e)

Komennon suoritus onnistui.

![image](https://github.com/user-attachments/assets/f4b78f24-d00c-4ac9-80e8-1df1c1581552)

Äsken tallennettiin testitietoa hakemistoon /home/ronja/lego/certificates/. Poistetaan ne, jotta voidaan suorittaa virallinen komento. rm -r lego poistaa lego -kansion sekä sen sisällä olevat kansiot ja tiedostot.

![image](https://github.com/user-attachments/assets/520e031f-7ef9-4285-b358-018ca5e6d511)

Suoritetaan sama komento kuin aikaisemmin, mutta poistetaan --server=… Tämä on siis virallinen pyyntö palvelimelle, ei enää testi.

![image](https://github.com/user-attachments/assets/84d26b57-0bf8-4fc1-9303-cfcfffe8de80)

Komennon suoritus onnistui.

![image](https://github.com/user-attachments/assets/42d605d2-35a7-4a5a-b96c-fbdbd6fb806b)

Avataan seuraavaksi nettisivun konfiguraatiotiedosto ronjawahlsten.com.conf.

![image](https://github.com/user-attachments/assets/f3698cb4-c5af-40be-bc65-ba712822ded3)

Muokataan konfiguraatiotiedostoa alla olevan mukaiseksi. Lisätään siis portille 443 eli HTTPS-portille oma konfiguraatio, jossa edelliseen verrattuna lisätään myös varmenteen hakemistot.

![image](https://github.com/user-attachments/assets/47c45dd6-e1a6-48f4-bf09-f73e34bc198b)

Otetaan varmenne käyttöön.

![image](https://github.com/user-attachments/assets/76eb347c-193a-4c8d-a77a-f6ebbd011d50)

Yritin käynnistää Apachen uudestaan, mutta tuli virheilmoitus.

![image](https://github.com/user-attachments/assets/7a23afba-7457-42fb-8515-5f17ecd2f191)

Katsoin toimiiko nettisivu. Ei toiminut.

![image](https://github.com/user-attachments/assets/6693ebfc-0fc0-4457-9b0d-6e13c21e0333)

Ajattelin ensin, että Apachen uudelleenkäynnistys ei onnistus, koska palomuuri ei ole sallinut porttia 443, joten avasin sen. Se ei kuitenkaan auttanut, sama virheilmoitus tuli edelleen.

![image](https://github.com/user-attachments/assets/bbf50b67-2c84-49f3-b05b-e023b11a6938)

Päätin seuraavaksi tarkistaa, onhan konfiguraatiotiedoston hakemistopolut oikein. Huomasin, että hakemistopolku varmenteelle on väärin. Siitä puuttuu yksi kansio. Certificates -kansion sisällä on vielä toinen certificates -kansio, joten lisäsin sen konfiguraatiotiedostoon.

![image](https://github.com/user-attachments/assets/edbc181a-bbae-457b-a9bd-8c70034354ec)

![image](https://github.com/user-attachments/assets/6f291170-afa7-4d28-be46-cff0d570e4c6)

Testataan toimiiko Apachen uudelleenkäynnistys nyt.

![image](https://github.com/user-attachments/assets/0e33c88f-7fa1-4a41-bc95-732327a6f7d2)

Onnistui!!

Suoritetaan komento sudo apache2ctl configtest.

![image](https://github.com/user-attachments/assets/20b39105-762f-45c8-8f2c-ec35f8fa08ce)

Testataan, toimiiko sertifikaatti. Kirjoitetaan selaimen hakukenttään osoite https://ronjawahlsten.com

![image](https://github.com/user-attachments/assets/ded63c78-bea1-4e68-becd-06399aef6028)

Lukon kuva ilmestyi!!



## b) SSLLabs Rating

Testataan nettisivu laadunvarmistustyökalulla. Käytetään siihen sivustoa 

https://www.ssllabs.com/ssltest/

Saadaan SSL raportti. ronjawahlsten.com sivustolla on A-rating.

![image](https://github.com/user-attachments/assets/5b6ddd38-e4f7-409d-974f-eeb70a49f0ac)



## Lähteet

Karvinen Tero 2025: Linux Palvelimen 2025 alkukevät: https://terokarvinen.com/linux-palvelimet/

Let's Encrypt 2024: How It Works: https://letsencrypt.org/how-it-works/

Lange 2024: Lego: Obtain a Certificate: Using an existing, running web server: https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/index.html#using-an-existing-running-web-server

The Apache Software Foundation 2025: Apache HTTP Server Version 2.4 [Official] Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample
