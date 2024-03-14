## Yksinkertainen esimerkkiohjelma Djangolla

Käytän apuna https://terokarvinen.com/2022/django-instant-crm-tutorial/ sekä https://terokarvinen.com/2022/deploy-django/ ohjeita.
- Aloitetaan asentamalla Development environment ja sille uusimmat Python-paketit (Django 4)
- Tehdään myös virtualenv env/ kansio, jossa on uusimmat paketit. System-site-packages antaa mahdollisuuden käyttää paketteja virtuaaliympäristön ulkopuolella
```
sudo apt-get update
sudo apt-get -y install virtualenv
virtualenv --system-site-packages -p python3 env/
```
- Asennus kesti noin 30s

Aloitetaan virtuaaliympäristön käyttö
```
source env/bin/activate
```

![enviactiv](https://github.com/NicoSaario/Linux_Palvelimet/assets/156778628/184cd30d-c86e-4739-8a87-27886edca03f)

- Nyt pitää ehdottomasti tarkistaa, että ollaan virtualenvissä, virtuaaliympäristössä ja missään nimessä pip ei käytetä sudona!
  ```
  which pip
  ```
- ![whichpip](https://github.com/NicoSaario/Linux_Palvelimet/assets/156778628/32409828-13d2-4c42-a2a2-aa44a19592ce)

  ```
  micro requirements.txt
  ```
- Yleensä asennettavat pakettilistat laitetaan tekstitiedostolle, joten vain yksi sana "django" riittää.
- Sitten asennetaan ja testataan

```
pip install -r requirements.txt
django-admin --version
```
![djangotest](https://github.com/NicoSaario/Linux_Palvelimet/assets/156778628/aeb97847-cdc1-442a-bd47-cf046291e356)

### Uusi Django - projekti
```
django-admin startproject kukkoko
cd kukkoko
./manage.py runserver #EI nettiin!!
```
- Raketti lentää, hyvin menee.
- Tehdään admin - interface
- Päivitellään tietokantaa
```
.manage.py makemigrations
.manage.py migrate
```
- Lisätään käyttäjä
```
sudo apt-get install pwgen
pwgen -s 20 1 # randomisalasana
./manage.py createsuperuser
```
![djangoadmin](https://github.com/NicoSaario/Linux_Palvelimet/assets/156778628/9a020eae-1d68-4d05-a44f-88ddf4898231)
- Saatiin admin-sivu näkyviin
- Nähtävästi en päässyt kirjautumaan eikä ollut pwgeniä, joten sen jouduin asentamaan Teron aikaisemmilla ohjeilla komennolla
- ```
  sudo apt-get install pwgen
  ```
  - Nyt heitti virheilmoituksen ./manage.py runserveristä, että "Error: That port is already in use"
  - Nopealla Googlaamisella, löysin postauksen https://stackoverflow.com/questions/20239232/django-server-error-port-is-already-in-use, jossa neuvottiin käyttämään komentoa ja "tappamaan prosessit, jotka käyttävät porttia 8000:
    ```
    sudo fuser -k 8000/tcp
    ```
- Ilmeisesti olin lopettanut jonkun toiminnon komennolla Control+Z, jolloin se ei lopettanut serveriä, heitti itseni vain sieltä ulos. Control+C toimii tähän. Testasin sen siis uudelleen ja jouduin jälleen käyttämään tuota komentoa fuser
- Homma toimii. Sain sen takaisin aktivoitua. Admin-sivu ei jostain syystä kyllä toimi, vaikka pwgenillä salasanan tein ja copypastesin sen sinne oikean käyttäjän kanssa... Lisäselvityksiä siis
- Ta - Daa!
- ![changepassw](https://github.com/NicoSaario/Linux_Palvelimet/assets/156778628/ac7f2428-b6da-4d41-b095-81560bc829de)
- Tajusin siis, että salasanan asettamisessa on luultavasti mennyt joku vikaan ja Googlasin salasanan vaihto-operaation (joka ilmeisesti tullut vasta hiljattain komentoriville)
- Komento siis:
  ```
  manage.py changepassword <käyttäjä>
  # pyytää uuden salasanan
  ```
![changepassw](https://github.com/NicoSaario/Linux_Palvelimet/assets/156778628/361ee5d9-105d-4ca6-bd93-ff6e244ad965)

### Customer Database
- Ohjeessa annettiin lupa käyttää Teron esimerkki CRM, joten kokeilen sitä ensimmäisenä
```
./manage.py startup crm
micro kukkoko/settings.py
```
- Mennään muokkaamaan Installed_Apps alapuolelle ja lisätään CRM kuvan mukaisesti
- ![kukkosettings](https://github.com/NicoSaario/Linux_Palvelimet/assets/156778628/d309aab4-6753-4b53-a76b-06121290ee88)

  
