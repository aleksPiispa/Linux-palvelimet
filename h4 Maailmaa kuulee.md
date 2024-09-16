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
Aloitin tehtävän tekemisen 15.9.2024 klo 21.04

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

Siirryin Linoden sivuille ja loin tunnukset. Palvelimen luominen oli nopeaa ja selkeää. Siellä oli myös tarjouksena 100$ ilmaista creditiä. 
Sain luotua palvelimen!

![Näyttökuva 2024-09-16 003822](https://github.com/user-attachments/assets/dc391092-07f9-41f8-9e28-eab494bb13b5)

Tämän jälkeen otin ssh-yhteyden palvelimeeni antamalla komennon $ ssh root@172.232.133.74
Sain vihdoin yhteyden palvelimeeni! Eikä siihen mennyt aikaa kuin lähemmäs kolmisen tuntia...

![Näyttökuva 2024-09-16 003958](https://github.com/user-attachments/assets/52182d4f-a3cf-4df6-9007-9518b73cea1f)


## d) Palvelin suojaa palomuurilla 

klo 23.53

Seuraavana vuorossa oli asentaa palvelimelle palomuuri, sekä tehdä siihen reikä ssh-yhteyttä varten. Palomuurin asentaminen tapahtui komennolla $ sudo apt-get install ufw

![Näyttökuva 2024-09-16 004142](https://github.com/user-attachments/assets/58f02179-c3cf-4764-b49c-d6ba41ede768)

Tämän jälkeen tein palomuuriin reiän ssh-yhteyttä varten, komennolla $ sudo ufw allow 22/tcp. Vasta sen jälkeen kytkin palomuuin päälle $ sudo ufw enable.

![Näyttökuva 2024-09-16 004311](https://github.com/user-attachments/assets/9a669d3c-6dba-4bd6-8c9f-35d6347ff205)

Loin sitten itselleni käyttäjän $ sudo adduser aleks

![Näyttökuva 2024-09-16 004457](https://github.com/user-attachments/assets/a8c3346e-ed48-4aea-938a-e31a047e9830)

Vasta tämän jälkeen tajusin, että olisin voinut samalla antaa itselleni sudo-oikeudet, joten tein sitten komennon $ sudo adduser aleks sudo.

![Näyttökuva 2024-09-16 005007](https://github.com/user-attachments/assets/32f345af-4390-4a21-8e76-6e520805a5a1)

Nyt minulla oli sudo-oikeudet. Kirjauduin sisään käyttäjälleni.

![Näyttökuva 2024-09-16 010128](https://github.com/user-attachments/assets/963933bc-4ccc-4277-b62f-c8e3098a6896)

Kävin sitten lukitsemassa root-käyttäjän, sekä poistamassa mahdollisuuden kirjautua palvelimelle root-käyttäjänä.

![Näyttökuva 2024-09-16 010531](https://github.com/user-attachments/assets/cae1334e-de83-47bd-b7b4-8d4c521da4ad)

![Näyttökuva 2024-09-16 010443](https://github.com/user-attachments/assets/51ae4114-5d27-45b5-b103-814460a17633)


## e) Kotisivut palvelimelle

16.9.2024 klo 00.15

Tässä osiossa minun tuli luoda palvelimelleni omat kotisivut. Aloitin tehtävän ensin pävittämällä palvelimeni ja asentamalla Apache2 weppipalvelimen $sudo apt-get install apache2.

![Näyttökuva 2024-09-16 010649](https://github.com/user-attachments/assets/1b7ee0dc-ae2b-4aa3-8e15-8a5a8d0cd495)

![Näyttökuva 2024-09-16 010854](https://github.com/user-attachments/assets/6fe55fa4-2303-4b2e-92de-d3321c06f88e)

Käynnistin Apache2 palvelimen $sudo systemctl start apache2.
Tein myös palomuuriin reiän portille 80/tcp, jotta palvelimeeni voidaan ottaa suojaamaton yhteys. Sain tehtyä sen komennolla $sudo ufw allow 80/tcp.
Sitten menin Mozilla-selaimeen ja syötin URL-kenttään palvelimeni IP-osoitteen.

![Näyttökuva 2024-09-16 011218](https://github.com/user-attachments/assets/da54e61b-72f9-466c-af1b-fff50da3ea96)

Vaihdoin kotisivun viime tunnilla opitusta sudo tee-komennosta.

![Näyttökuva 2024-09-16 011356](https://github.com/user-attachments/assets/7a6b6770-5da9-4035-b517-8b7c27e96b40)

![Näyttökuva 2024-09-16 011410](https://github.com/user-attachments/assets/b14d9aaa-9028-4a11-a88e-2ac5e8d932fc)

## f) Ohjelmien päivitys

klo 00.34

Ajoin vielä lopuksi päivitykset komennoilla $sudo apt-get update ja $sudo apt-get upgrade.

![Näyttökuva 2024-09-16 022834](https://github.com/user-attachments/assets/7c9d1ae6-6a3a-451c-b28d-f3eaf4a3c2c2)

Mitään ei näyttänyt päivittyneen, sillä olin jo aiemmin päivittänyt uuden virtuaalipalvelimeni ohjelmat.


## Lähteet

Karvinen, T. 2017. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. Saatavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/. Luettu 15.9.2024.

Karvinen, T. 2024. Linux palvelimet 2024 alkusyksy. Saatavissa: https://terokarvinen.com/linux-palvelimet/. Luettu 15.9.2024.

Lesonen, L. 2023. h4 Maailma kuulee. Saatavissa: https://github.com/LiisaLesonen/linux-palvelimet/blob/main/h4.md. Luettu 15.9.2024.










