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
![whichpip](https://github.com/NicoSaario/Linux_Palvelimet/assets/156778628/32409828-13d2-4c42-a2a2-aa44a19592ce)
- Nyt pitää ehdottomasti tarkistaa, että ollaan virtualenvissä, virtuaaliympäristössä ja missään nimessä pip ei käytetä sudona!
- 
