# KotitehtäväOmaLinux

## FSF Free Software Definition
- Käyttäjillä on vapaus ajaa, käyttää, kopioida, jakaa, opiskella, muuttaa sekä kehittää ohjelmaa
- Voi olla kaupallisia
- Ei pidä sekoittaa "Open Sourcen" kanssa.  
### Four essential freedoms
- Voi ajaa ohjelmaa ihan, mihin tarkoitukseen tahansa (ei  voida kieltää tai estää sen suorittamista)
- Opiskella, miten se toimii ja muuttaa se toimimaan omien mieltymysten mukaan. Siihen tarvitaan pääsy lähdekoodiin.
- Vapaus levittää kopioita eteenpäin muille (Kenenkään ei tarvitse tietää, jos teet muutoksia tai jaat eteenpäin tekemiäsi muutoksia ohjelmaan, voit jakaa vapaasti ja vaikka veloittaa tehdyistä muutoksista)
- Vapaus jakaa omia modifioituja versioita muille. Tähänkin vaatimuksena on koodiin pääsy.
* Jos ohjelma antaa käyttäjille kaikki nämä edellämainitut neljä kohtaa, voidaan se luokitella "free softwareksi"
## Raportin aakkoset
- Tarkoituksena tehdä raportti, jonka mukaan joku toinen ihminen pystyisi tekemään samat asiat sen perusteella
- Mitä teet, mitä ja miten tapahtui
- Muistiinpanoja raportin yhteydessä ja samalla, kun tekee
- Ympäristö, käyttöjärjestelmä, verkko, aika
- Kellotus (kuinka kauan aikaa, koska alkoi - koska loppui)
- Epäonnistumiset ja onnistumiset, vikalista
- Helppolukuisuus
- Lähdeviittaukset
- Pyrkimys tehdä raportti niin, että sitä on mahdollista hyödyntää myös itse tulevaisuudessa

# Linuxin asennus virtuaalikoneeseen

### Alkutiedot
Olin jo aiemmalla kurssilla ICT-infra/pilvi asentanut Oracle VM VirtualBox Managerin, mutta päivitin sen versioon 7.0.14 ja raportti on luotu sen pohjalta. Debian tuli ladattua valmiiksi tunnilla oheisesta linkistä:
https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/ ja kyseessä debian-live-12.1.0-amd64-xfce.iso - tiedosto.
Asennukset alkoivat VirtualBoxin päivityksellä noin kello 23:40. Boxin päivitys loppui 23.45 ja kaikki kyseisen raportin pohjalta on tehty kotioloissa Windows 11, HP läppärillä.

## Asennus
Aloitin asennuksen 22.01.2024 kello 0.18 ohjeen https://terokarvinen.com/2021/install-debian-on-virtualbox/ mukaan. Expert mode - Nimen asettaminen, ISO image, Type = Linux ja Debian (64-bit), klikkasin myös "Skip Unattended Installation". RAMia pitäisi olla riittävästi, joten valitsin 4096MB ja tunnilla käydyn ohjeen mukaan laitoin 4 prosessoria. Laitoin File-Sizen Hard Disk kohdassa 60GB, muut jäivät defaulteiksi.
### ISO-image
Asetin sen jo aikaisemmassa kohdassa, joten se on jo valmiiksi valittuna Storage-lehdellä.
## Käynnistys
Käynnistin kernelin 0.27, valitaan Live system (amd64). Käynnistys kesti noin 3min ja valmistui 0.30. Ei näyttänyt olevan logeissa ongelmia. Myös kuvan osoittama testi toimi.

![TeroKarvinenTesti](https://github.com/NicoSaario/Tunti1/assets/156778628/5db56345-5515-4a4b-b3aa-ec688eb8df8c)


Pienen testailun jälkeen avasin Debian GNU/Linux Installerin työpöydältä kello 0.35.
## Installer
- -> American English
- Next -> Region: Europe, Zone: Helsinki
- Next -> Keyboard model Generic 105-key PC Defaulttina, Finnish ja Default -> Tässä kohtaa on myös hyvä kokeilla näppäimistön toimivuutta ja kuten kuvasta näkyy, kaikki toimi
 ![Nappaimistotesti](https://github.com/NicoSaario/Tunti1/assets/156778628/0921b0b7-f89c-44b4-9581-55f27b70e41d)

- Next -> Erase Disk, jotta päästään turhista "roskista" eroon ja tämä poistaa kaiken virtuaalikoneelta -> Encrypt: no, koska kyseessä on virtuaalikone, Boot Loader defaulttina "Master Boot Record..."
- Next -> User-tiedot - tärkeintä, ettei ole omaa, yrityksen tai tietokoneen specksejä, koska joissain verkoissa siitä tulee julkinen verkkotunnus ja sen pystyy näkemään
- -> Summary ja pitää muistaa laittaa installer full screenille, jotta "Install-button" tulee näkyville.

- Osio kesti raporttia samalla kirjoittaessa noin 13 minuuttia. Asennus alkoi 0.52 ja päättyi 1.10.
Pääsin kirjautumaan sisään ja myös verkkosivustot toimivat. Jouduin kerran käynnistämään uudestaan koko Debianin, sillä se kaatui jostain syystä.


### Lähteet:
Raportin kirjoittaminen, Tero karvinen 2006: https://terokarvinen.com/2006/raportin-kirjoittaminen-4/
What is Free Software?, Free Software Foundation (FSF): https://www.gnu.org/philosophy/free-sw.html#four-freedoms
Install Debian on Virtualbox - Updated 2023, Tero Karvinen: https://terokarvinen.com/2021/install-debian-on-virtualbox/






