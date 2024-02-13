# Tiivistelmä
- Ensin vuokrattava palvelu, esimerkiksi DigitalOcean, Linode ja Gandi
- Domainnimi (DNS-name) esimerkiksi Namecheapilta
- Palvelin oltava joko lähellä asiakkaita tai itseä pienen latencyn ja GRPD vuoksi
- Ensin terminaalen juureen kiinni, löytyy palveluntarjoajan sivulta (tiedoista) ssh root@ ... ip
- HYVÄT SALASANAT!
- Palomuuriin reikä, palomuuri aktiiviseksi
- ufw allow 22/tcp, sudo ufw enable
- TESTAA ennen rootin lukitsemista Sudolla!
- Muista PÄIVITYKSET! sudo apt-get update ja upgrade
- sudo adduser ... käytännössä kaikki komennot nimen perään voi muokata
- adduser nico (sudo, admin, adm)
- Public-servereiden asennus - vaatii palomuuriin rei'än sudo ufw allow 80/tcp


# Tehtävät - Pilvipalvelun vuokraus ja webbipalvelin

### Ympäristö

Tehtävät on suoritettu Oracle VM VirtualBoxilla Debian 12, taustalla Windows 11 - Home - käyttöjärjestelmä, päivitykset ajettu 13.02.2024 asti. AMD Ryzen 5 4500U, RAM 8 Gt.

## Suoritus
Valitsin DigitalOcean - palvelun GitHubin kautta. Palvelu kysyi aluksi jongenjoutavia kysymyksiä, joihin vastasin opiskelijan näkökulmasta. 
Lopputulokseen ei näyttänyt olevan vaikutusta, sillä sain linkitettyä käyttäjän Githubin kanssa ja palvelu toimii.
Miten liikkeelle?
Käytän Tero Karvisen oppitunnilla opettamia ohjeita ja lisämateriaaleina https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/ sekä https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/.
1. Ensiksi valitaan se, mitä ollaan tekemässä - DigitalOceanin tapauksessa "Droplet" vastaa virtuaalipalvelinta ja sen vuokraamista.
2. Palvelu pyytää ensiksi serverin valitsemista, jolloin valitaan tässä tapauksessa lähin palvelin, jotta yhteys on paras (latenssi pienin). EU:n sisältä löytyy myös mukavat GDPR-asetukset.
3. Image - Debian, 12x64 (12 viimeisin versio)
4. Tilauksesta Basic (SharedCPU) - älä maksa siitä, mistä et mitään tiedä. 1GB/25GB Disk, sillä se riittää mainiosti.
5. Tähän hetkeen ei tarvita mitään ylimääräistä lisäpalveluita - Host name on hyvä olla joku julkisuuteen kelpaava, joka ei paljasta mitään ylimääräistä.
6. Create, kaikki valmista hankintojen puolesta, "Droplet" on aktiivinen - siirrytään VM Terminaalin pariin.

## Yhteydenotto ja alkutoimet
Tässä kohdassa tuli pieniä ongelmia matkaan. En saanut yhteyttä komennolla ssh root@dropletip, terminal näytti vain "command not found" ja "Connection timed out". Noin 45 minuuttia käynnistelin Droplettiä uudestaan, selvitin mahdollisia asetuksia, seuloin internetiä ja DigitalOceanin asiakaspalvelun "Usein kysyttyjä kysymyksiä" - osiota. Lopulta törmäsin artikkeliin https://phoenixnap.com/kb/ssh-connection-refused sekä vihdoin ajatukseen siitä, ettei SSH Client ole asennettu.
Käytin siis komentoja:
- sudo apt-get update
- sudo apt-get upgrade
Jotta päivitykset on ajettu ja ohjelmia pystyy asentamaan.
Tämän jälkeen artikkelin mukaan suoritin komennon
- sudo apt install openssh-client.
- Kokeilin systemctl status ssh
![systemctlssh](https://github.com/NicoSaario/Tunti1/assets/156778628/51de0969-3539-4073-9e0a-5854d5242780).
- Vihreetä valoa näyttää, service enabled, active and running. Se kuulostaa aina hyvältä.
- Uusi yritys ssh root@"dropletip"
- ![systemctlssh](https://github.com/NicoSaario/Tunti1/assets/156778628/1f8504e8-d00c-4b70-aae9-d9875ee35d78)
- Sisällä ollaan!
Jatketaan edellämainituilla Teron ja Sannan ohjeilla.
- Palomuuriin reikä.... Palomuuri on kateissa.
 Asennetaan siis. Nopeasti hain ohjeet, kun ei muistista vielä löytynyt. Mukavasti käyttämäni palvelun ohjeet ensimmäisenä.. Kiva "sattuma". https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-debian-11-243261243130246d443771547031794d72784e6b36656d4a326e49732e
 Nykyään ei tarvitse aktivoida Ipv6, koska ufw tekee sen automaattisesti
- sudo apt install ufw
- systemctl status ufw - vihreää valoa
- Takaisin hommiin.
- sudo ufw allow 22/tcp
- sudo ufw enable
![systemctlssh](https://github.com/NicoSaario/Tunti1/assets/156778628/b7d0bbc7-7451-424b-a6a5-d32a83c3fa0c)
- Lisätään käyttäjä
- sudo adduser nico
- Lisätään käyttäjä sudoryhmään
- sudo adduser nico sudo
- Testataan sudon toimivuus
- ssh nico@"dropletip"
- Lukitsee salasanan, kannattaa tehdä normaalista sudo-käyttäjästä
- sudo usermod --lock root
- ![roottilukko](https://github.com/NicoSaario/Tunti1/assets/156778628/b05c5b8e-b0e2-42d9-8f93-cb01febf4c94)
- Näytti toimivan!
- sudp apt-get update
- sudo apt-get dist upgrade

### Webbipalvelin
Asennetaan Apache2 aikaisempien tehtävien perusteella
- sudo aptp-get install apache2
- sudo systemctl enable -now apache2
 Avataan Apachelle portti
- sudo ufw allow 80/tcp
- avasin selaimella palvelimen ip-osoitteen 188.166.27.117, josta tuli Apache2 default-sivu. Hyvin menee siis!
- Sain näkyviin pelkän "Default"-tekstin sivustolle, mutta joudun palaamaan tehtävään hieman myöhemmin ja suorittamaan loput tehtävät myöhemmin.

  
### Lähteet
- Teoriasta käytäntöön pilvipalvelimen avulla (h4)
Kirjoittaja Susanna / 14.2.2022
https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/ (luettu 13.02.2024)

- First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS
Posted on September 19, 2017 by Tero Karvinen 
https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/ (luettu 13.02.2024)

- https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-debian-11-243261243130246d443771547031794d72784e6b36656d4a326e49732e
