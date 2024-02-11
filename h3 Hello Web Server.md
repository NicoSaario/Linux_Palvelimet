# Webbipalvelin

## Name-based vs. IP-based Virtual Hosts
Tiivistelmä tehty https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/ h3 Hello WeB server x) - kohdan linkeistä

- IP-pohjaiset virtuaali-isännät käyttävät yhteyden IP-osoitetta määrittämään oikean virtuaalisen isännän palvelimiseen
- Jokaiselle isännälle tarvitsee oman osoitteen
- Name-based virtuaalihostit on paljon käytännöllisempi metodi, koska monet virtuaaliset isännät voivat jakaa yhden osoitteen/portin
- Voidaan saavuttaa useilla fyysisillä verkkoyhteyksillä

Name-based virtual hosts
- Monet eri isännät voivat jakaa saman IP-osoitteen
- Isäntänimi tulee osana HTTP-otsikkoa
- Yksinkertaisempi, koska DNS-palvelimen voi määrittää yhdistämään kukin IP-osoite ja sen jälkeen Apachen HTTP server tunnistamaan eri isäntänimet
- Pyynnön käsittelyn saapuessa, palvelin löytää parhaan vastaavuuden, IP-osoitteeseen ja porttiin perustuen. Jos isäntiä on useampia, se valitsee parhaiten vastaavan portin ja osoitteen yhdistelmän

### Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address
- Apache mahdollistaa usean verkkotunnuksen yhdelle IP-osoitteelle
Komennot
- Web Serverin asennus sekä configuraatio
- $ sudo apt-get -y install apache2
- $ echo "Default"|sudo tee /var/www/html/index.html
- Uuden nimen asettaminen
- $ sudoedit /etc/apache2/sites-available/pyora.example.com.conf
- $ cat /etc/apache2/sites-available/pyora.example.com.conf
<VirtualHost *:80>
 ServerName pyora.example.com
 ServerAlias www.pyora.example.com
 DocumentRoot /home/xubuntu/publicsites/pyora.example.com
 <Directory /home/xubuntu/publicsites/pyora.example.com>
   Require all granted
 </Directory>
</VirtualHost>
- $ sudo a2ensite pyora.example.com
- $ sudo systemctl restart apache2
- Normaalina käyttäjänä sivun luominen
- $ mkdir -p /home/xubuntu/publicsites/pyora.example.com/
- $ echo pyora > /home/xubuntu/publicsites/pyora.example.com/index.html
- Testaaminen curl-komennoilla
  Helpointa käyttää curl localhost

## Tehtävät Oracle VM Debian
Tehtävät on suoritettu Oracle VM VirtualBoxilla, taustalla Windows 11 - Home - käyttöjärjestelmä, päivitykset ajettu 12.02.2024 asti. AMD Ryzen 5 4500U, RAM 8 Gt. Linux ei myöskään ole entuudestaan kovinkaan tuttu, joten kaikki on tehty ensimmäisiä kertoja ja amatöörin näkövinkkelistä.

![curllocal](https://github.com/NicoSaario/Tunti1/assets/156778628/87de5cb7-9e08-4244-9935-baa41084c1cb)
Apache-webbipalvelin asennettiin tunnilla. Testin mukaan curl-komennolla, sivu on aktiivinen ja näyttää toimivan.

### Error-log
![logimerkinnät](https://github.com/NicoSaario/Tunti1/assets/156778628/9f030a2b-faea-45bd-8fd4-19c57763a4d9)

Tulkintojeni mukaan ensimmäinen rivi tarkoittaa sitä, milloin rivi luotiin eli tehtävän teon yhteydessä. Kellonaika ja päivämäärä täsmää.
Jouduin hieman käyttämään Bardia (nykyinen Gemini) apuna loppujen logien tulkinnoissa ja vastauksena sain, että loput rivit on Apachen tunnistemerkintöjä ja configured resuming normal operations tarkoittaisi Apache-palvelimen konfiguroitua ja palaamista normaaliin toimintaan.

### Etusivu uusiksi
Aloitin laittamalla tunnilla tehdyn sivuston pois käytöstä komennolla avaamalla kansion /etc/apache2/sites-enabled. Siitä sudo a2dissite nico.example.com.conf
Tämän jälkeen Apache2 näkyi jälleen Default Page

![defaultsite](https://github.com/NicoSaario/Tunti1/assets/156778628/850f4571-a580-4200-810d-0dd8c8d684de)

Tein ensin komennolla sudoedit=MICRO /etc/apache2/sites-available/hattu.example.coml.conf, jotta saan tuon esimerkkisivun rakennettua. MICRO sen takia, että käytän microeditoria. Käytin https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/ Add New Name Based Virtual Host - kohtaa apuna ja asetin samoin, mutta nimeksi vain hattu.example.com

![hattuexample](https://github.com/NicoSaario/Tunti1/assets/156778628/229d4fc2-7bf0-4acc-af40-bc1d36432a22)

Tein uuden kansion hattu.example.com, restart apache2 komennon ja configtestin, jossa Syntax OK.
![hattumkdir](https://github.com/NicoSaario/Tunti1/assets/156778628/48ef9554-1e2f-4175-9ca0-dc01251c0528)

Nyt tuli myös virheilmoitus kotisivusta, joten hyvään suuntaan ollaan menossa!
![hattuvirheilmoitus](https://github.com/NicoSaario/Tunti1/assets/156778628/aa8f3c84-0aa5-4670-a43d-6dcca91fc0af)

Kaikki näyttäisi olevan kunnossa, mutten jostain syystä saa sivun HTML-koodia näkyviin. 
Muutaman ärräpään ja vaiheiden läpikäymistä yksi kerrallaan, tajusin virheen. Publicwebissä oli nyt kaksi sivua ja ilmeisesti tästä syystä se ei toiminut.
Tein uuden hakemiston publicwebbi ja lisäsin sinne hattu.example.com ja index.html - tiedoston. Tämän jälkeen sivu alkoi toimia.

![history2](https://github.com/NicoSaario/Tunti1/assets/156778628/9e5eb527-d818-4bb6-bff7-9b8cfef38b99)

![toimii](https://github.com/NicoSaario/Tunti1/assets/156778628/20b695b7-3f27-4656-8e48-15c676ac1206)

### ValidiHTML
![koodi](https://github.com/NicoSaario/Tunti1/assets/156778628/6c771755-79c0-40ae-aaaa-a04a56558944)

Kirjoitettu koodi tuli yhden virheilmoituksen kanssa takaisin.
![validi](https://github.com/NicoSaario/Tunti1/assets/156778628/5e2819bb-2377-4d39-bc32-5d527cf4f4ae)

Korjasin koodissa html-tagin sisään lang="en" ja virheilmoitus lähti.
![eivirhe](https://github.com/NicoSaario/Tunti1/assets/156778628/58058b0a-9e5d-4de0-918a-dbf9f77bf9a7)

# Curl
curl -
![curl -i](https://github.com/NicoSaario/Tunti1/assets/156778628/4497aa78-8887-4b5d-b0fe-e10eeb79ffad)
- curl ottaa yhteyden palvelimen ja laitteen välillä CLI:n kautta
- curl -i on yksityiskohtaisempi ja näyttää ajan, Server-kohdassa Debianin ja sen version, viimeiseksi muokattu ja tiedostomuodon (text/html)






