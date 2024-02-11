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
$ sudo apt-get -y install apache2
$ echo "Default"|sudo tee /var/www/html/index.html
- Uuden nimen asettaminen
$ sudoedit /etc/apache2/sites-available/pyora.example.com.conf
$ cat /etc/apache2/sites-available/pyora.example.com.conf
<VirtualHost *:80>
 ServerName pyora.example.com
 ServerAlias www.pyora.example.com
 DocumentRoot /home/xubuntu/publicsites/pyora.example.com
 <Directory /home/xubuntu/publicsites/pyora.example.com>
   Require all granted
 </Directory>
</VirtualHost>
$ sudo a2ensite pyora.example.com
$ sudo systemctl restart apache2
- Normaalina käyttäjänä sivun luominen
$ mkdir -p /home/xubuntu/publicsites/pyora.example.com/
$ echo pyora > /home/xubuntu/publicsites/pyora.example.com/index.html
- Testaaminen curl-komennoilla
  Helpointa käyttää curl localhost

## Tehtävät Oracle VM Debian


