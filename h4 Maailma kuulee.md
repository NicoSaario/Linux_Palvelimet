# Tehtävät - Pilvipalvelun vuokraus ja webbipalvelin

Valitsin DigitalOcean - palvelun GitHubin kautta. Palvelu kysyi aluksi jongenjoutavia kysymyksiä, joihin vastasin opiskelijan näkökulmasta. 
Lopputulokseen ei näyttänyt olevan vaikutusta, sillä sain linkitettyä käyttäjän Githubin kanssa ja palvelu toimii.
Miten liikkeelle?
Käytän Tero Karvisen oppitunnilla opettamia ohjeita ja lisämateriaaleina https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/ sekä https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/.
1. Ensiksi valitaan se, mitä ollaan tekemässä - DigitalOceanin tapauksessa "Droplet" vastaa virtuaalipalvelinta ja sen vuokraamista.
2. Palvelu pyytää ensiksi serverin valitsemista, jolloin valitaan tässä tapauksessa lähin palvelin, jotta yhteys on paras (latenssi pienin). EU:n sisältä löytyy myös mukavat GDPR-asetukset.
3. Image - Debian, 12x64 (12 viimeisin versio)
4. Tilauksesta Basic (SharedCPU) - älä maksa siitä, mistä et mitään tiedä. 1GB/25GB Disk, sillä se riittää mainiosti.
5. Tähän hetkeen ei tarvita mitään ylimääräistä lisäpalveluita - Host name on hyvä olla joku julkisuuteen kelpaava, joka ei paljasta mitään ylimääräistä.
