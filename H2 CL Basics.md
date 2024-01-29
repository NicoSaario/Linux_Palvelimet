# Command Line Basics

## Peruskomennot ja niiden funktio
- $ pwd tulostaa työhakemiston
- $ ls listaa tiedostot työhakemistossa, jos ei näy haettavaa tiedostoa tai hakemistoa, kannattaa käyttää nähdäkseen ne tiedostot, mitä se sisältää
-  $ cd ...dir/ vaihtaa hakemiston ...dir työhakemistossa
-  $ cd vaihtaa hakemistoa, jolloin Pwd.n tulostama polku lyhenee

#Tehtävien suoritus
Tehtävät on suoritettu Oracle VM VirtualBoxilla, taustalla Windows 11 - Home - käyttöjärjestelmä, päivitykset ajettu 28.01.2024 asti. AMD Ryzen 5 4500U, RAM 8 Gt.
Linux ei myöskään ole entuudestaan kovinkaan tuttu, joten kaikki on tehty ensimmäisiä kertoja ja amatöörin näkövinkkelistä.

### Micron asennus
Asennus on toteutettu https://terokarvinen.com/2022/micro-editor-plugin-hello-world/ ohjeen mukaan. Vaihe vaiheelta, testailin ensin erilaisia komentoja, jonka jälkeen  komennot:
- $ sudo apt-get update (päivittää käytettävissä olevien pakettien luettelon, suoritettava ennen muita apt-komentoja)
- $ sudo apt-get -y install micro
![Micro](https://github.com/NicoSaario/Tunti1/assets/156778628/22bbdbfa-9afd-497c-bf9d-9721ed144c9b)

** $ sudo apt-get update ei näy kuvassa, sillä suoritin sen hetkeä aikaisemmin testatessani muita komentoja. Meni kuitenkin läpi ja toimii.

![Micro_Toiminnassa](https://github.com/NicoSaario/Tunti1/assets/156778628/3be67458-3223-49a7-a1d7-8ce9b315c502)

### Koneen rauta ja lshw
Ohjeessa oleva lshw-komento ei mennyt läpi, joten asensin lshw kyseisen linkin kautta https://www.howtogeek.com/devops/how-to-use-lshw-in-linux-with-a-practical-example/
Totesin kuitenkin nopeasti, ettei $ sudo lshw -short -sanitize - komento toiminut, sillä asensin graafisen lshw-gtk työkalun normaalin lshw-paketin sijaan. No eipä siitä haittaakaan ole, vaikkakin graafinen vaikuttaisi näyttävän vähemmän tietoja.
![lshw-gtk](https://github.com/NicoSaario/Tunti1/assets/156778628/e0cff8c4-19a7-4bfe-a8c6-82e9f88badd9)

Komennolla $ sudo apt-get install lshw sen sai toimimaan komentokehotteessa.
![lshw](https://github.com/NicoSaario/Tunti1/assets/156778628/54e9c225-9b0d-4359-b486-8d2df7f4945a)

Listassa näyttäisi olevan yhteenveto laitteiston kokoonpanosta ja esimerkiksi näyttää tuon aiemmin kertomani AMD Ryzen 5 4500U ja raportti kattaa järjestelmän havaitut laitteistot sekä näyttää esimerkiksi tietokoneen oman suorittimen. Siihenpä se analystointi tältä erää jäi. Pitää palata tuohon vielä myöhemmin ja perehtyä lisää.

### Asenna itsellesi kolme uutta komentoriviohjelmaa

Ohjelma 1
-----------------------------------------------------------------------------------------------------------------
Hetken aikaa pohdiskeltuani siitä, mitä tässä tehtävässä haetaan, päädyin asentamaan tekstilehmän, joka piristää mukavasti muuten suht tylsää ympäristöä. Käytin tehtävässä tämän sivuston ohjeita https://medium.com/@gurpreet.singh_89/15-fun-linux-command-line-programs-to-spice-up-your-terminal-abf30af73de1
ja asensin käyttämällä $sudo apt-get install cowsay.
![cowsay](https://github.com/NicoSaario/Tunti1/assets/156778628/e9e4bdc0-9136-4914-a0dd-e32bdd24197a)
-----------------------------------------------------------------------------------------------------------------
Ohjelma 2
-----------------------------------------------------------------------------------------------------------------
Seuraavaksi asensin Wikit - Command Line Toolin linkin ohjeiden mukaan
https://www.tecmint.com/wikipedia-commandline-tool/
Ensin piti asentaa nodejs ja npm, jotta sen sai asennettua. Kyseessä siis open-source command-line ohhjelma, joka tuottaa Wikipedian yhteenvetoja. 
![wikit](https://github.com/NicoSaario/Tunti1/assets/156778628/d47b3a8c-c318-42d8-82d9-b759b730257e)
-----------------------------------------------------------------------------------------------------------------
Ohjelma 3
-----------------------------------------------------------------------------------------------------------------
En keksinyt oikeen mitään muuta hyödyllistä, vaikka selasin useita eri artikkeleita aiheeseen liittyen. Päädyin lopulta fortuneen, joka lähettää satunnaisia viestejä ja sitaatteja. Ongelmana tällä hetkellä on se, ettei viestit palaudu englannin kielellä, vaan Lettura Rapida.. Italiaksi kenties? Ilmeisesti pitäisi poistaa ylimääräiset kielipaketit.

![fortune](https://github.com/NicoSaario/Tunti1/assets/156778628/aab26937-62a9-44a0-b377-3b8597555276)

----------------------------------------------------------------------------------------------------------------


## Important Directories
/ Rootti, jonka alla kaikki muut ovat
![Rootti](https://github.com/NicoSaario/Tunti1/assets/156778628/c93de453-7870-42b2-be91-ebeb21b4717f)

Esimerkkinä /lib, joka sisältää kaikki järjestelmän käyttämät hyödylliset kirjastotiedostot:
![rootlib](https://github.com/NicoSaario/Tunti1/assets/156778628/2a8173b3-4820-4858-b9f8-c8eab5b2bfb8)

/home/käyttäjä/, johon käyttäjä pystyy vakituisesti tallettamaan tiedostoja. Downloads tällä hetkellä varmaan tärkein näistä kaikista, vaikkei sielläkään ole vielä sisältöä.
![home](https://github.com/NicoSaario/Tunti1/assets/156778628/83cdd541-8b97-421e-9efb-3733ac596ed7)

/etc/security varmasti yksi tärkeimmistä tämän kansion sisällyksistä, sillä se sisältää tiedostoja, jotka liittyvät järjestelmän turvallisuuteen, kuten salasanoja.
![cdsecurity](https://github.com/NicoSaario/Tunti1/assets/156778628/822de49b-412a-4b1f-9591-40b7571a0279)

