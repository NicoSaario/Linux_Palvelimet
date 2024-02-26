# Koko juttu

Asennetaan uusi, tyhjä virtuaalikone ja tehdään siihen Apache-webbipalvelin ja SSH-etähallintapalvelin. 
Etusivu weppialvelimelle, jolle normaalikäyttäjän oikeudet.

### Tehtävien suoritus
Tehtävät on suoritettu Oracle VM VirtualBoxilla, taustalla Windows 11 - Home - käyttöjärjestelmä, päivitykset ajettu 26.02.2024 asti. AMD Ryzen 5 4500U, RAM 8 Gt. Aika:
Itä-Euroopan normaaliaika
Aikavyöhyke: Suomi (UTC+2)
maanantaina, 26. helmikuuta 2024

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
- Oma nimi, kirjautumisnimi (lowercase, lyhyt!!) käyttäjä jota ei voi sitoa mihinkään, koska siitä tulee Public Domain Name, VAHVA SALASANA, Log in autom..
  ![k10](https://github.com/NicoSaario/Tunti1/assets/156778628/25506aa4-5985-4a6c-8110-66f858c7955d)
- Summary ja Install
![k11](https://github.com/NicoSaario/Tunti1/assets/156778628/66aca1d7-4724-4965-93fd-2581fe420973)

Tein raporttia ja ruokaa (pitäähän sitä syödä välillä), joten ajasta voisi ottaa noin 10 minuuttia pois, asennuksen aloitin 20:57. Todellisuudessa asetuksiin menisi noin 5 - minuuttia.
Asennus kesti muistaakseni noin 13 minuuttia.

# Virhe, jota kukaan ei toivo tai odota, lähes kaikki sen jossain kohtaa elämää onnistuvat tekemään
Kaikki oli OK.. kunnes tein ehkä yleisimmän ja onnettomimman virheen, jonka voi tietokoneen parissa tehdä - kaadoin läppärin päälle lasillisen vettä.
Noh.. kone on nyt kuivatuksessa, joten jouduin kaivamaan kaapista pölyjen keskeltä vanhan Lenovon läppärin.
Lopputehtävä on siis suoritettu seuraavilla specseillä sähköpostien lukemiseen tarkoitetulla koneella:
- Lenovo Yoga 330 kosketusnäyttö
- Suoritin Intel(R) Celeron(R) N4000 CPU @ 1.10GHz   1.10 GHz
- RAM 4GB
- Windows 11 Home - päivityksiä ajan raporttia kirjoittaessa, joten 26.02 asti

## Uusi alku
Latasin VirtualBoxin kyseisestä linkistä: https://www.virtualbox.org/wiki/Downloads, VirtualBox 7.0.14 platform packages Windwsille.
  


  
  



  
