# Koko juttu

Asennetaan uusi, tyhjä virtuaalikone ja tehdään siihen Apache-webbipalvelin ja SSH-etähallintapalvelin. 
Etusivu weppialvelimelle, jolle normaalikäyttäjän oikeudet.

### Tehtävien suoritus
Tehtävät on suoritettu Oracle VM VirtualBoxilla, taustalla Windows 11 - Home - käyttöjärjestelmä, päivitykset ajettu 26.02.2024 asti. AMD Ryzen 5 4500U, RAM 8 Gt. 

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
