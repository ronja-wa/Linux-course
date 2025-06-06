# h5 Nimekäs
## a) Domain-nimen vuokraus
Valitaan domain-nimen vuokraajaksi namecheap. Luodaan ensin käyttäjä, jonka jälkeen päästään etsimään sopiva nimi. Oma nimeni oli vapaana, joten valitsin domainiksi ronjawahlsten.com.

![image](https://github.com/user-attachments/assets/4518c96f-202d-49ae-acc9-3e110e0459d7)


Kun domain-nimi on ostettu, siirrytään Domain List -välilehdelle.

![image](https://github.com/user-attachments/assets/a0811968-da4f-4f89-aad8-117435ba513f)

Painetaan sivun oikeassa reunassa näkyvää Manage -nappia.

![image](https://github.com/user-attachments/assets/3f63b758-5c93-41d4-a7c0-80ad65229e5f)

Valitaan aukeavalta sivulta välilehti Advanced DNS.

![image](https://github.com/user-attachments/assets/62e3a9d4-bde9-4f2a-9cbc-8c16b83809e5)

Luodaan uusi tietue painamalla ”ADD NEW RECORD” -napista.

![image](https://github.com/user-attachments/assets/42666258-8240-41db-9fb3-72cced7d4f79)

Tehdään kaksi A-tietuetta, joiden avulla yhdistetään domain-nimi ja palvelimen IP-osoite toisiinsa. TTL on lyhenne sanoista Time To Live. Se kertoo, kuinka kauan A-tietue säilyy välimuistissa. Kun uudet tietueet on luotu, vanhat tietueet poistuvat samalla itsestään, jolloin niitä ei tarvitse manuaalisesti poistaa.

![image](https://github.com/user-attachments/assets/0c1c8221-9f7d-4590-ab97-a4c9f016b620)

Nyt oman palvelimen testisivun tulisi näkyä, kun verkko-osoitteeksi kirjoittaa ronjawahlsten.com.

![image](https://github.com/user-attachments/assets/924a5442-7cda-4aa1-a37f-2d7422b2ba84)


## b) Name Based Hosting
Siirrytään omalle virtuaalikoneelle ja otetaan ensin SSH-yhteys palvelinkoneelle. Siirrytään alla näkyvään hakemistoon. Lisätään uusi domain ronjawahlsten.com.

![image](https://github.com/user-attachments/assets/f3e4677a-11f6-4f7b-b10c-60a7f41b77d1)

Alla näkyy nettisivun konfiguraatiotiedosto. Olin aikaisemmin laittanut väärän hakemiston DocumentRootin kohdalle, joten vaihdoin sen oikeaksi. Tähden tilalla oli myös IP-osoite aiemmin, joten muokkasin senkin.

![image](https://github.com/user-attachments/assets/eed07716-5b93-47f2-a323-3726cf84ec5e)

Aktivoidaan name based virtualhost.

![image](https://github.com/user-attachments/assets/26512c56-8c7f-4d18-8cd3-bcbb03887646)

Käynnistetään apache uudestaan.

![image](https://github.com/user-attachments/assets/79f321a7-7816-423c-be9f-ead8e120e956)

Siirrytään kotihakemistoon ja huomataan, että nettisivun sijainniksi merkattua hakemistopolkua ei ole olemassa, joten luodaan se komennolla
sudo mkdir -p /home/ronja/publicsites/ronjawahlsten.com

Luodaan index.html etusivu -tiedosto. Tiedosto pitää vielä tallentaa pääkäyttäjän oikeuksilla, koska tiedoston omistajuutta ei ole vielä siirretty käyttäjälle.

![image](https://github.com/user-attachments/assets/52214820-5fcf-46d8-b96a-baf4e89c2208)

![image](https://github.com/user-attachments/assets/1298c74b-1367-4ea1-ad2f-49a573d8c054)

Testataan etusivun toimivuus tarkistamalla se selaimesta.

![image](https://github.com/user-attachments/assets/186ed337-3587-47a0-8313-ab259c3d608c)

Nettisivu ei toimikaan. Käydään tarkistamas error loki. Se kertoo, että Apachella ei ole käyttöoikeuksia hakemistoon /home/ronja/publicsites

![image](https://github.com/user-attachments/assets/1f905bc3-3d47-4a72-94de-3e808b5c849d)

Tarkistetaan kaikki käyttöoikeudet. Home -hakemiston käyttöoikeudet ovat oikein.

![image](https://github.com/user-attachments/assets/4520d3df-d36c-4fa8-98d3-13a5a0e62de9)

ronja -hakemistosta puuttuu käyttöoikeuksia. Lisätään rekursiivisesti eli kaikkiin ronja -hakemiston sisällä oleviin kansioihin ja tiedostoihin samanaikaisesti samat käyttöoikeudet. Lisätään siis kaikille luku ja suoritusoikeus.

![image](https://github.com/user-attachments/assets/277015c0-cdca-4e91-b908-cc3fe9de6abf)

![image](https://github.com/user-attachments/assets/bcf2a1ff-68f7-4681-af0b-5a4ee6428949)

Nyt käyttöoikeudet ovat oikein ja myös nettisivu toimii.

![image](https://github.com/user-attachments/assets/8dc170e0-5367-4920-963d-df1d52fa6019)

![image](https://github.com/user-attachments/assets/811bb0f3-b10c-4ffb-a53d-19e6bf98e87c)


## c) Kotisivu

Luodaan alasivut blog.html ja projects.html samaan hakemistoon, jossa index.html on.

![image](https://github.com/user-attachments/assets/c19c590f-eeea-402a-98af-e226ef710c9d)

Annetaan peruskäyttäjälle kirjoitusoikeus siirtämällä tiedostojen omistajuus käyttäjälle ronja.

Alla olevasta kuvasta nähdään, että tiedostojen omistaja on root.

![image](https://github.com/user-attachments/assets/ab5e09a3-cf39-4f7e-ab5b-1136f2d60b17)

Siirretään tiedostot käyttäjän ronja omistukseen.

![image](https://github.com/user-attachments/assets/a701c507-9bc5-4808-be04-2344bb57f35f)

Muokataan ensin etusivua. Lisätään siihen nav -osio eli navigointivalikko, jonka avulla päästään äsken luotuihin alasivuihin. Ohje navigoinnin tekoon löytyy täältä: https://www.w3schools.com/TAGs/tag_nav.asp

![image](https://github.com/user-attachments/assets/aab3c4d0-b99f-4c1c-b94b-de5470a2c6dc)

Muokataan seuraavaksi alasivuihinkin navigointivalikko, jotta jokaiselta alasivulta voidaan siirtyä toiselle alasivulle.

![image](https://github.com/user-attachments/assets/5dad3cb6-6541-456d-bcd4-84d3d17fa718)

![image](https://github.com/user-attachments/assets/24f85447-b3e5-47e0-a09f-594e23ef4ebe)

Lopputulos näyttää selaimessa tältä.

![image](https://github.com/user-attachments/assets/d4496a38-78d8-4575-8ba9-953f5fe36a96)

![image](https://github.com/user-attachments/assets/a0a00795-c8ff-4560-ae03-0939937e677c)

![image](https://github.com/user-attachments/assets/5d3e57bf-b822-4405-ab50-623602da129c)

## d) Subdomain

Siirrytään NameCheapissä samaan sijaintiin, jossa a-kohdassa lisättiin A-tietueet. Lisätään kaksi uutta A-tietuetta, joiden host-nimeksi laitetaan testi ja linux. Ohjeet alidomainin luomiseen löytyy tästä videosta: https://www.youtube.com/watch?v=lhsm_1jx2Uk

![image](https://github.com/user-attachments/assets/e583adf9-1ee5-4181-8a23-58274d23532d)


Testataan onnistuuko uusilla alidomaineilla nettisivuille pääsy.

![image](https://github.com/user-attachments/assets/b553cfc1-766e-4b53-93a9-257048017bf1)

![image](https://github.com/user-attachments/assets/bb0539ac-d7eb-425b-8ff3-e2b590a532ab)


Onnistui!

## e) DNS-tiedot

Asennetaan ensin host- ja dig-työkalut

![image](https://github.com/user-attachments/assets/bed72478-9766-42cb-884b-14c0bff51d74)

![image](https://github.com/user-attachments/assets/e3a1db6a-36b9-4e7c-8680-fe8c6b4b42e7)

host-komennolla nähdään domainin IP-osoite.

![image](https://github.com/user-attachments/assets/fee54e82-630f-4da3-bd26-b4c5f4f41482)


Alla näkyy dig -komennon suoritus domainille ronjawahlsten.com ja alidomainille linux.ronjawahlsten.com. Molemmista saadaan IP-osoitteeksi palvelimen IP-osoite 80.69.172.186. Ainoat erot näiden tulosten välillä on viestin koko, joka on päädomainilla 62 ja alidomainilla 68, sekä kyselyn vastausaika, joka on päädomainilla 44ms ja alidomainilla 0ms.

![image](https://github.com/user-attachments/assets/637daac3-6f71-4058-a4ca-2d2726f9ec51)

![image](https://github.com/user-attachments/assets/c54e4cce-d52a-4bbd-b37d-4b0864bbd277)



google.com

![image](https://github.com/user-attachments/assets/433b20a0-e45e-4168-822f-8661b0889584)


terokarvinen.com

![image](https://github.com/user-attachments/assets/0061a22f-0be8-44ec-bbe3-810fbf8775c3)


## Lähteet

Karvinen Tero 2024: h5 Nimekäs: https://terokarvinen.com/linux-palvelimet/#h5-nimekas

Karvinen Tero 12.2.2012: Short HTML5 page: https://terokarvinen.com/2012/short-html5-page/

w3schools: HTML <nav Tag: https://www.w3schools.com/TAGs/tag_nav.asp

Namecheap 24.10.2024: How to create subdomain for my domain via Namecheap account: https://www.youtube.com/watch?v=lhsm_1jx2Uk

GeeksForGeeks 6.11.2024: dig Command in Linux with Examples: https://www.geeksforgeeks.org/dig-command-in-linux-with-examples/


Muokattu 11.3.2025 konfiguraatiotiedosto ja käyttöoikeuksia
