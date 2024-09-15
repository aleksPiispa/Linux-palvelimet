Tämä, ja kaikki tulevat tehtävät pohjautuvat Tero Karvisen Linux palvelimet kurssin tehtävänantoihin. Suoritan kurssia alkasyksyllä 2024. 
Teen kurssin tehtäviä Lenovon Ideapad 5 Pro 13ARH7 -kannettavalla. Käyttöjärjestelmänä koneessa on Windows 11 Home, ja koneessa on 16GB RAM-muistia sekä suorittimena AMD Ryzen 5 6600HS Creator Edition. 
Näytönohjain: AMD Radeon 660M Graphics. Storage: M.2 SSD 512Gt, vapaana 343Gt.

Aloitin tehtävän tekemisen 15.9.2024 klo 21.04

#h4 Maailma kuulee

## x) Tiivistelmä
Tero Karvinen mainitsi viime oppitunnilla, sekä myös kotisivuillaan tärkeitä vinkkejä, kuinka toimia kun vuokraa palvelinta.
- Käytä todella vahvoja salasanoja, sillä aivan varmasti koneellesi yritetään murtautua!
- Kannattaa valita palvelimen sijainti läheltä asiakkaita.
- Kun luot palvelinta, tarkista IP-osoitteesi, sillä ilman sitä et voi ottaa SSH-yhteyttä palvelimeen.
- Ensimmäisellä kerralla, otetaan yhteys root@10.0.0.1 (tuohon tulee oman palvelimesi IP-osoite)
- asenna palomuuri ja tee siihen reikä SSH-yhteyttä varten komennolla $sudo ufw allow 22/tcp, vasta tämän jälkeen kytke palomuuri päälle $sudo ufw enable.
- Määritetään sudo käyttäjä, $sudo adduser "nimi" sudo
- päivitä paketit $sudo apt-get update ja $sudo apt-get upgrade

(Karvinen, 2017)

## a) Virtuaalisen palvelimen vuokraus
Aloitin tehtävän tekemisen klo 21.04

Ensimmäisenä tehtävänä oli vuokrata palvelin, jolla tämän viikon tehtävä tuli tehdä. Tämä osoittautuikin itselleni kaikkein haasteellisimmaksi.
Olin aiemmin viikolla saanut hyväksyttyä hakemukseni GitHub Educationiin, ja ajattelin hyödyntää sitä, sillä sen avulla pääsisin ilmaiseksi vuokraamaan palvelimen Digital Oceanista.
Sain yhdistettyä GitHub tunnukseni Digital Oceaniin ja lisättyä laskutustiedot, joita sivu minulta vaati. Tässä kohtaa törmäsin virheeseen, nimittäin tililtäni meni katevarauksiin 10$ veloitus, mutta vastauksena
sain silti kieltävän tuloksen. Jokin ei mennyt oikein. Yritin selvittää asiaa verkkopankistani, ja rahat olivat palautuneet tililleni. Eli luultavasti pankkini ei hyväksynyt veloitusta ulkomaiselle tilille. Tämä jäi askarruttamaan minua.

No, ei se mitään. Kyselin kurssikavereilta hieman apua Teamsissa, sillä en muistanut muiden vastaavien palveluiden nimiä. Sain vinkiksi kokeilla UpCloudia. Sinne siis.
Siellä virtuaalipalvelimen vuokraus pysähtyi siihen, kun yritin luoda palvelinta. Ainoa vaihtoehto suojata palvelin oli SSH-avaimella, jollaista minulla ei ollut. Jätin leikin sikseen, ja siirryin yrittämään Azurella.

Azuren kanssa minulla oli myös alkuun hankaluuksia, sillä kun yritin yhdistää GitHubiani Azureen, sain virheilmoitusta. Yritin sitten kirjautua koulun tunnuksilla, ja pääsinkin sisään.
Seuraavaksi lähdin luomaan Virtual Machinea. 

![Näyttökuva 2024-09-15 224712](https://github.com/user-attachments/assets/33f6cf56-6718-481d-b1b7-a534a6ae7dea)

Sain luotua palvelimen ja sain sen käynnistymäänkin. Sillä aikaa asensin SSH:n kurssin palvelimelle.

![Näyttökuva 2024-09-15 225032](https://github.com/user-attachments/assets/45c314ce-0428-47ce-8b50-b226a9c1ca7b)

Yritin ottaa yhteyden uuteen palvelimeen komentorivillä, mutta sitten tulikin taas mutkia matkaan. En nimittäin saanut yhteyttä 

![Näyttökuva 2024-09-15 230510](https://github.com/user-attachments/assets/37eb92b4-752e-4ce4-965e-862996f18cb6)

Ajattelin, että ehkä luomassani palvelimessa on jotain vikaa, ja poistin palvelimen, ja loin uuden. 
Päädyin lopulta luomaan Azurella 5 palvelinta, ja jokaisen kanssa oli sama ongelma. Minulla oli salasanat olemassa, jotta pääsisin ottamaan yhteyden root@10.0.0.1 (jokaisella palvelimista oli uniikki IP-osoite).
Lopputulos oli kuitenkin joka kerta se, että sain vastauksena "Permission denied". 

Tässä vaiheessa olin jo valmis luovuttamaan, väsynyt ja ahdistunut.
Luin kuitenkin uudestaan Tero Karvisen First steps-sivua, jonka hän mainitsi edellisellä oppitunnilla. Siellä huomasin linkin Linoden sivuille.

Siirryin Linoden sivuilla ja loin tunnukset. Palvelimen luominen oli nopeaa ja selkeää. Siellä oli myös tarjouksena 60 päivän free trial. 
Sain luotua palvelimen!

![Näyttökuva 2024-09-16 003822](https://github.com/user-attachments/assets/dc391092-07f9-41f8-9e28-eab494bb13b5)

Tämän jälkeen otin ssh-yhteyden palvelimeeni antamalla komennon $ ssh root@172.232.133.74
Sain vihdoin yhteyden palvelimeeni! Eikä siihen mennyt aikaa kuin lähemmäs kolmisen tuntia...





