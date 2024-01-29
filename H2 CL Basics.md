# Command Line Basics

## Peruskomennot ja niiden funktio
- $ pwd tulostaa työhakemiston
- $ ls listaa tiedostot työhakemistossa, jos ei näy haettavaa tiedostoa tai hakemistoa, kannattaa käyttää nähdäkseen ne tiedostot, mitä se sisältää
-  $ cd ...dir/ vaihtaa hakemiston ...dir työhakemistossa
-  $ cd vaihtaa hakemistoa, jolloin Pwd.n tulostama polku lyhenee "hyppää ylöspäin"
-  $ mkdir uusikansio - uusi hakemisto, esim. kansio
-  $ mv uusikansio vanhakansio - vaihtaa nimen
-  $ history Näkee vanhat, tehdyt komennot
-  $ sudo apt-get update aina ennen muita apt-komentoja, päivittää listan vapaista paketeista
-  /var/log/ Lokit
-  $ nano lll.txt tekstieditori, jolla voi tehdä tekstitiedostoja

# Tehtävien suoritus
Tehtävät on suoritettu Oracle VM VirtualBoxilla, taustalla Windows 11 - Home - käyttöjärjestelmä, päivitykset ajettu 28.01.2024 asti. AMD Ryzen 5 4500U, RAM 8 Gt.
Linux ei myöskään ole entuudestaan kovinkaan tuttu, joten kaikki on tehty ensimmäisiä kertoja ja amatöörin näkövinkkelistä.

### Micron asennus
Asennus on toteutettu https://terokarvinen.com/2022/micro-editor-plugin-hello-world/ ohjeen mukaan. Vaihe vaiheelta, testailin ensin erilaisia komentoja, jonka jälkeen  komennot:
- $ sudo apt-get update (päivittää käytettävissä olevien pakettien luettelon, suoritettava ennen muita apt-komentoja)
- $ sudo apt-get -y install micro
![oikealshw](https://github.com/NicoSaario/Tunti1/assets/156778628/e8cc6938-668c-43be-9467-c9012a2cfe3e)

** $ sudo apt-get update ei näy kuvassa, sillä suoritin sen hetkeä aikaisemmin testatessani muita komentoja. Meni kuitenkin läpi ja toimii.
![Micro_Toiminnassa](https://github.com/NicoSaario/Tunti1/assets/156778628/e07064c5-4670-4720-bb52-5a0822a694a3)


### Koneen rauta ja lshw
Ohjeessa oleva lshw-komento ei mennyt läpi, joten asensin lshw kyseisen linkin kautta https://www.howtogeek.com/devops/how-to-use-lshw-in-linux-with-a-practical-example/
Totesin kuitenkin nopeasti, ettei $ sudo lshw -short -sanitize - komento toiminut, sillä asensin graafisen lshw-gtk työkalun normaalin lshw-paketin sijaan. No eipä siitä haittaakaan ole, vaikkakin graafinen vaikuttaisi näyttävän vähemmän tietoja.
![lshw-gtk](https://github.com/NicoSaario/Tunti1/assets/156778628/e0cff8c4-19a7-4bfe-a8c6-82e9f88badd9)

Komennolla $ sudo apt-get install lshw sen sai toimimaan komentokehotteessa.
![lshw](https://github.com/NicoSaario/Tunti1/assets/156778628/54e9c225-9b0d-4359-b486-8d2df7f4945a)

Listassa näyttäisi olevan yhteenveto laitteiston kokoonpanosta ja esimerkiksi näyttää tuon aiemmin kertomani AMD Ryzen 5 4500U ja raportti kattaa järjestelmän havaitut laitteistot sekä näyttää esimerkiksi tietokoneen oman suorittimen. Siihenpä se analystointi tältä erää jäi. Pitää palata tuohon vielä myöhemmin ja perehtyä lisää.

## Asenna itsellesi kolme uutta komentoriviohjelmaa

Ohjelma 1

Hetken aikaa pohdiskeltuani siitä, mitä tässä tehtävässä haetaan, päädyin asentamaan tekstilehmän, joka piristää mukavasti muuten suht tylsää ympäristöä. Käytin tehtävässä tämän sivuston ohjeita https://medium.com/@gurpreet.singh_89/15-fun-linux-command-line-programs-to-spice-up-your-terminal-abf30af73de1
ja asensin käyttämällä $sudo apt-get install cowsay.
![cowsay](https://github.com/NicoSaario/Tunti1/assets/156778628/e9e4bdc0-9136-4914-a0dd-e32bdd24197a)

Ohjelma 2

Seuraavaksi asensin Wikit - Command Line Toolin linkin ohjeiden mukaan
https://www.tecmint.com/wikipedia-commandline-tool/
Ensin piti asentaa nodejs ja npm, jotta sen sai asennettua. Kyseessä siis open-source command-line ohhjelma, joka tuottaa Wikipedian yhteenvetoja. 
![wikit](https://github.com/NicoSaario/Tunti1/assets/156778628/d47b3a8c-c318-42d8-82d9-b759b730257e)

Ohjelma 3
En keksinyt oikeen mitään muuta hyödyllistä, vaikka selasin useita eri artikkeleita aiheeseen liittyen. Päädyin lopulta fortuneen, joka lähettää satunnaisia viestejä ja sitaatteja. Ongelmana tällä hetkellä on se, ettei viestit palaudu englannin kielellä, vaan Lettura Rapida.. Italiaksi kenties? Ilmeisesti pitäisi poistaa ylimääräiset kielipaketit.

![fortune](https://github.com/NicoSaario/Tunti1/assets/156778628/aab26937-62a9-44a0-b377-3b8597555276)


## Important Directories
/ Rootti, jonka alla kaikki muut ovat
![Rootti](https://github.com/NicoSaario/Tunti1/assets/156778628/c93de453-7870-42b2-be91-ebeb21b4717f)

Esimerkkinä /lib, joka sisältää kaikki järjestelmän käyttämät hyödylliset kirjastotiedostot:
![rootlib](https://github.com/NicoSaario/Tunti1/assets/156778628/2a8173b3-4820-4858-b9f8-c8eab5b2bfb8)

/home/käyttäjä/, johon käyttäjä pystyy vakituisesti tallettamaan tiedostoja. Downloads tällä hetkellä varmaan tärkein näistä kaikista, vaikkei sielläkään ole vielä sisältöä.
![home](https://github.com/NicoSaario/Tunti1/assets/156778628/83cdd541-8b97-421e-9efb-3733ac596ed7)

/etc/security varmasti yksi tärkeimmistä tämän kansion sisällyksistä, sillä se sisältää tiedostoja, jotka liittyvät järjestelmän turvallisuuteen, kuten salasanoja.
![cdsecurity](https://github.com/NicoSaario/Tunti1/assets/156778628/822de49b-412a-4b1f-9591-40b7571a0279)

/media - kansiossa ei ole vielä sisällä mitään, joten jätän esimerkin tästä pois.

/var/log/ sisältää järjestelmän laajuiset logit ja tiedostot niistä.

##Grep
Tässä esimerkissä käytin Greppiä hakemaan tiedostosta foo.txt hakusanalla "Aku", jolloin se printtasi takaisin "Aku Ankka".

![AkuAnkka](https://github.com/NicoSaario/Tunti1/assets/156778628/7e5d067e-8436-472e-b2c3-a6787c34b9eb)
Toisessa esimerkissä käytin sitä etsimään kuviota vastaavat tiedostot, jotka sisältävät merkit "Aku"

![AkuTiedostot](https://github.com/NicoSaario/Tunti1/assets/156778628/0f7dcfdd-08d9-42d5-b4b0-f3a7e4ac4c0d)


## Pipes
Esimerkissä käytin Teron materiaalista löytyvää ls /etc|less - komentoa,
![Pipes](https://github.com/NicoSaario/Tunti1/assets/156778628/bd3aa898-09ff-47ec-bb2f-6e2f285174f9)

Rehellisesti ottaen tehtäviin meni aikaa enemmän, mitä olisin voinut edes kuvitella. Joudun palaamaan näihin vielä myöhemmin ja jatkamaan niitä lisää, mutta tehtävä on näiden puitteissa palautettava tässä tilassa.


Lähteet: 
Basic Linux Commands for Beginners, March 21, 2018 by Alok Naushad:
https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners (Luettu 29.01.2024)

10 Best Linux Command-Line Tools, Aaron KiliLast Updated: November 9, 2023 (Luettu 29.01.2024):
https://www.tecmint.com/command-line-tools/#2_Googler_%E2%80%93_Google_from_the_Linux_Terminal

Micro Editor Plugin - a Hello World Tutorial, Tero Karvinen Sun 31.10.2022 (Luettu 29.01.2024):
https://terokarvinen.com/2022/micro-editor-plugin-hello-world/

How to Use lshw in Linux (With a Practical Example), BYHTG STAFF PUBLISHED NOV 24, 2021 (Luettu 29.01.2024)
https://www.howtogeek.com/devops/how-to-use-lshw-in-linux-with-a-practical-example/

Linux directory structure: /lib explained, SEPTEMBER 28, 2017 (Luettu 29.01.2024)
https://www.linuxtoday.com/infrastructure/linux-directory-structure-lib-explained/

grep command in Unix/Linux geeksforgeegs.org, Last Updated 13 Dec, 2023 (Luettu 29.01.2024)
https://www.geeksforgeeks.org/grep-command-in-unixlinux/

Command Line Basics Revisited, Tero Karvinen, Mon 03.02.2020 (Luettu 29.01.2024)
https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited



