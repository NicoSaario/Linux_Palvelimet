# Koko juttu

Asennetaan uusi, tyhjä virtuaalikone ja tehdään siihen Apache-webbipalvelin ja SSH-etähallintapalvelin. 
Etusivu weppialvelimelle, jolle normaalikäyttäjän oikeudet.

### Tehtävien suoritus
Tehtävät on suoritettu Oracle VM VirtualBoxilla, taustalla Windows 11 - Home - käyttöjärjestelmä, päivitykset ajettu 26.02.2024 asti. AMD Ryzen 5 4500U, RAM 8 Gt. Aika:
Itä-Euroopan normaaliaika
Aikavyöhyke: Suomi (UTC+2)
maanantaina, 26. helmikuuta 2024
- Tehtävästä löytyy 2 erilaista markdownia, sillä jouduin tekemään puhtaan suorituksen 3 kertaa uudelleen samalla raportoiden. Ensimmäisellä kerralla kastui läppäri, toisella kerralla varatietokone sanoi sopimuksen irti. Tämä on siis kolmas raportointiyritys

## Uuden virtuaalikoneen asennus
Tein asennuksen vanhan ohjeeni mukaan sekä varmistin asetusten oikeellisuuden sivulta https://terokarvinen.com/2021/install-debian-on-virtualbox/.
Itse asennus meni kokonaisuudessaan näin:
![k1](https://github.com/NicoSaario/Tunti1/assets/156778628/213ae983-66dd-4a19-ab90-b46e8725bc84)
![k2](https://github.com/NicoSaario/Tunti1/assets/156778628/ad933363-4cf0-47a0-b588-1ac2dd5cac34)
![k3](https://github.com/NicoSaario/Tunti1/assets/156778628/70381f15-368d-4714-b766-295973a7e53a)

Käytännössä ainoat muutokset:
- Nimen asettaminen
- ISO image
- Type = Linux ja Debian (64-bit)
- Skip unattended installation täppä
- RAM 4096MB
- 4 Prosessoria
- File-Size Hard Disk 60GB
- Muut default
  Lopputulos:
  ![k4](https://github.com/NicoSaario/Tunti1/assets/156778628/6ab6dd15-6b66-49e0-b45f-5a6fd1f1af5f)
  Muutoksissa meni karkeasti noin 5 min. 

Käynnistyksessä ei näkynyt virhelogeja. Seuraavaksi testataan, että kaikki toimii. Testi osoittaa näppäimistön, hiiren, netin sekä näytön toimivuuden.

![k5](https://github.com/NicoSaario/Tunti1/assets/156778628/73f976eb-ad24-4e39-bd57-53c383e6ef23)

Seuraavaksi klo 20:38 alkaa Debianin asentelu työpöydältä Install Debian:
- Valitaan American English (automaattisesti)
![k6](https://github.com/NicoSaario/Tunti1/assets/156778628/e31ec90f-d1f2-4cfc-ae50-e2c6731c8b3d)
- Pistetään Suomi maailmankartalle
  ![k7](https://github.com/NicoSaario/Tunti1/assets/156778628/817c5a31-cf55-4ce0-b8df-9415a8466083)
- Koska ollaan Suomessa, Näppäimistö Generic 105-key PC, Finnish ja Default. Testataan myös ääkkösten ja merkkien toimivuus.
![k8](https://github.com/NicoSaario/Tunti1/assets/156778628/98665290-141f-42db-b87f-445027f5e1d1)
- Poistellaan ylimääräiset roskat ja käytännössä kaikki virtuaalilevyltä
  ![k9](https://github.com/NicoSaario/Tunti1/assets/156778628/2ec5dcd9-e506-4789-a5df-8ed7544b5685)
Muita kohtia ei tarvitse, koska Encryptaus on fyysisille tietokoneille, ei niinkään virutaalikoneille. Master Boot Record hämää ja sen defaulttina vaihtaminen vain rikkoo asioita
- Oma nimi, kirjautumisnimi (lowercase, lyhyt!!) käyttäjä jota ei voi sitoa mihinkään, koska siitä tulee Public Domain Name, VAHVA SALASANA, Log in autom.. (EDIT=VIRHE!! EI NÄIN. TÄPPÄ POIS)
  ![k10](https://github.com/NicoSaario/Tunti1/assets/156778628/25506aa4-5985-4a6c-8110-66f858c7955d)
- Summary ja Install
![k11](https://github.com/NicoSaario/Tunti1/assets/156778628/66aca1d7-4724-4965-93fd-2581fe420973)

Tein raporttia ja ruokaa (pitäähän sitä syödä välillä), joten ajasta voisi ottaa noin 10 minuuttia pois, asennuksen aloitin 20:57. Todellisuudessa asetuksiin menisi noin 5 - minuuttia.
Asennus kesti muistaakseni noin 13 minuuttia.


## Apache2
Aloitetaan asentamalla apache2
- ensin aina sudo apt-get update, jotta voidaan asennella tavaraa
- sudo apt-get install apache2
- Saadaan apachen Default-sivu näkyviin
![apache2](https://github.com/NicoSaario/Tunti1/assets/156778628/acca735f-112b-4b8a-9bce-e23f8f5e2123)
Aikaisemman ohjeeni mukaan otetaan ensin default-sivu pois päältä
- cd /etc/apache2/sites-enabled
- sudo a2dissite 000-default 
Laitellaan esimerkkisivu
- EDITOR=micro sudoedit /etc/apache2/sites-available/kukko.example.com.conf
  ![tiedosto](https://github.com/NicoSaario/Tunti1/assets/156778628/98bcdcec-4037-45a5-91aa-d52d26ecb492)
  - sudo a2ensite kukko.example.com.conf eli laitetaan se päälle
  - Restarttia apachelle sudo systemctl restart apache2
  ![hyvähyvä](https://github.com/NicoSaario/Tunti1/assets/156778628/ade419dc-f8fc-41a3-bc32-2d6157669918)
Huomasin, että laitoin vahingossa väärän polun kansioille, joten korjasin sekä kukko.example.com.conf, että publicsites - kansion osoittamaan /home/nico sen sijaan, että olisi polku /home/kana
- mkdir -p /home/nico/publicsites/kukko.example.com/
- Navigoidaan kansioon kukko.example.com/
Luodaan html - tiedosto
- micro index.html
- Teksti mahd. simppeli
- Lopputulos:
![toimiiii](https://github.com/NicoSaario/Tunti1/assets/156778628/1aef4d43-e641-4a38-9cd2-4ac274b028cb)
![ennenSSH](https://github.com/NicoSaario/Tunti1/assets/156778628/db669d7d-e264-4edc-8305-c7583e915eba)
- Asensin siis puuttuvan SSH-serverin aikaisemman ohjeeni mukaan
- https://github.com/NicoSaario/Tunti1/blob/main/h4%20Maailma%20kuulee.md
- Testasin sen toimivuuden komennolla systemctl status ssh
- ![statusssh](https://github.com/NicoSaario/Tunti1/assets/156778628/2daeca5e-9932-4bde-981b-b85b704411e2)
Kaikki näyttää olevan kunnossa. Olisi pitänyt tehdä jo aikaisemmin, mutta nyt palomuurin kimppuun:
Asennetaan se
- sudo apt install ufw
- systemctl status ufw - tällä hetkellä inactive (dead)
Korjataan muutama juttu, eli tehdään muutama reikä https://terokarvinen.com/2016/instant-firewall-sudo-ufw-enable/?fromSearch=firewall ohjeen mukaan
- sudo ufw allow 22/tcp - SSH
- sudo ufw allow 80/tcp - normaali http
- sudo ufw allow 443/tcp - encryptattu https
- sudo ufw enable
- systemctl status ufw
![status_ssh](https://github.com/NicoSaario/Tunti1/assets/156778628/8a356861-fcc9-4aef-9fd8-01132d466a29)
- otetaan yhteys DigitalOceaniin
- ssh root@dropletip
- ![avain](https://github.com/NicoSaario/Tunti1/assets/156778628/b0d1a584-c682-4dd2-b6cb-e7d3fcb076b3)
- Kaikki meni läpi ja sain avaimen tehtyä, mutta nyt ongelmaksi muodostui se, etten pääse kirjautumaan nico@localhostina
- Selvitellyt noin 2h vikaa ja ongelmaan ei ole vielä löytynyt vastausta.












