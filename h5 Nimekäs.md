Tämä, ja kaikki tulevat tehtävät pohjautuvat Tero Karvisen Linux palvelimet kurssin tehtävänantoihin. Suoritan kurssia alkasyksyllä 2024. 
Teen kurssin tehtäviä Lenovon Ideapad 5 Pro 13ARH7 -kannettavalla. Käyttöjärjestelmänä koneessa on Windows 11 Home, ja koneessa on 16GB RAM-muistia sekä suorittimena AMD Ryzen 5 6600HS Creator Edition. 
Näytönohjain: AMD Radeon 660M Graphics. Storage: M.2 SSD 512Gt, vapaana 343Gt.

# h5 Nimekäs

## b) Alidomain

*Tee kaksi uutta alidomainia, jotka osoittava omaan koneeseesi. Esimerkiksi palvelu on example.com -> linuxkurssi.example.com. 
Tee toinen alidomain A-tietueella ja toinen CNAME-tietueella. 
Alidomainit ovat tyypillisesti ilmaisia, kun sinulla on päädomain (example.com).*

Aloitin tehtävän tekemisen 22.9.2024 klo 18.35. 

Päätin aloittaa tehtävän tekemisen b-kohdasta, jotta voin hyödyntää alidomaineja a-kohdan tehtävässä sen sijaan, että olisin käyttänyt local hosteja.
Kirjauduin NameCheapin sivuille, josta vuokrasin nimipalvelimen edellisellä oppitunnilla. Vuokrasin nimen piispa.me, joka oli ilmainen vuodeksi.

![Näyttökuva 2024-09-22 222135](https://github.com/user-attachments/assets/99d6c1ff-820a-499a-8f7e-a9ef02845446)

Lisäsin nimipalveluuni uuden A-recordin ja laitoin host-kohtaan a ja valueen aiemmin vuokraamani palvelimen IP-osoitteen. TTL annoin 5 minuuttia. Tämän seurauksena URL haulla a.piispa.me pitäisi päästä saman domainin alidomainiin.
Tein lisäksi CNAME-recordin, jonka host kohtaan syötin info ja value kohtaan piispa.me. En ole aivan varma, mitä eroa on CNAME ja A-recordeilla, mutta ohjeissa käskettiin tekemään näin. Lisäksi CNAME-record kohtaan yritin antaa IP-osoitetta, mutta silloin tuli virheilmoitus. Siksi sen arvoksi
tuli piispa.me.

![Näyttökuva 2024-09-22 190615](https://github.com/user-attachments/assets/f300cb45-e865-4b69-a99f-962e96c7f421)

eli nyt minulla oli voimassa domain *piispa.me* sekä alidomainit *a.piispa.me* sekä *info.piispa.me*.

## a) Kotisivu

*Tee vähintään kolmen erillisen weppisivun kotisivu ja kopioi se näkymään palvelimellesi. Jos sinulla on oikea palvelin Internetissä, kannattaa käyttää sitä. 
Käytä name based virtual hosting tekniikkaa. Sivujen muokkaamisen pitää onnistua ilman pääkäyttäjän oikeuksia, niiden kopioiminen pääkäyttäjänä testisivun paikalle ei käy. 
Kotisivujen ei tarvitse olla hienoja, mutta niiden tulee olla validia HTML:ää ja linkittää toisiinsa.*

Myönnän suoraan, että koodaaminen, varsinkaan HTML ei ole minun juttuni. Kävin johdantokurssin keväällä 2023, ja turhauduin silloin pahemman kerran sivujen tekoon. Käytin silloin sivujeni tekemiseen lähemmäs 200 tuntia, ja kyseinen kurssi oli 5 opintopisteen, eli n. 135 tunnin mittainen.
Lisäksi sivut ladattiin silloin Haaga-Helian Myy-palvelimelle, jota ei enää ole eli sivuni ovat kadonneet maan päältä... Päätin siis tässä tehtävässä tyytyä siihen että sivut ovat mahdollisimman simppelit, vastaavat omista domaineistaan ja linkittyvät toisiinsa.

Käytin apunanani Tero Karvisen yksinkertaisen html-sivun ohjeita.
Aluksi otin Linu-koneeltani ssh-yhteyden aiemmin vuokraamaani palvelimeen ja kirjauduin sisään aleks@localhost. Tein tyypilliset päivitykset **sudo apt-get update**.
Tämän jälkeen kaivoin muistista Tero Karvisen ohjeet, sekä aiemman Name Based Virtual Hosting-tehtävän, ja seurasin ohjeita. 

![Näyttökuva 2024-09-22 195923](https://github.com/user-attachments/assets/996fe786-0dc4-4b0c-9c2d-06b3da99f1cf)

![Näyttökuva 2024-09-22 200507](https://github.com/user-attachments/assets/9f012523-c558-49c8-a6db-84006d1f9132)

Seurasin Karvisen ohjeita tarkasti, mutta tämän komennon annettuani törmäsin ongelmiin.

![Näyttökuva 2024-09-22 202125](https://github.com/user-attachments/assets/a33ec333-3088-4b6a-b48e-8aaf55e3d095)

Yritin luoda sivua normaalina käyttäjänä ilman pääkäyttäjän oikeuksia. Kokeilin curlia ja tämä tuli vastaukseksi. Näytti siltä, että ainoastaan root-käyttäjällä olisi oikeudet tiedostopolkuun. 
ChatGPT antoi neuvon, että **sudo chown aleks:aleks /home/aleks/publicsites** saisin muutettua kansion oikeudet pois root-käyttäjältä.

![Näyttökuva 2024-09-22 204708](https://github.com/user-attachments/assets/9242c15a-da41-40e4-986a-4d8c4e516ee3)

Tämän jälkeen onnistuin luomaan publicsites alikansiot piispa.me, a.piispa.me sekä info.piispa.me ja kirjoittaa niihin HTML-koodia micro-editorilla. (Korjasin koodit sen jälkeen, kun olin varmistanut sivujen toimivuuden, eli n. klo 22.30 aikoihin)

![Näyttökuva 2024-09-22 232354](https://github.com/user-attachments/assets/2305a61b-b355-44f9-91db-f6ea5701e5f1)

![Näyttökuva 2024-09-22 231640](https://github.com/user-attachments/assets/d3079b69-2028-483c-a29c-01ba3d128a90)

![Näyttökuva 2024-09-22 231739](https://github.com/user-attachments/assets/fb196137-8825-4e69-8212-b400f0db6ed5)

![Näyttökuva 2024-09-22 232205](https://github.com/user-attachments/assets/5110a66f-6aa4-4ce0-9d84-8ac17bc797f7)

Olin myös tarkistanut koodin w3 validatorilla, että se on validia HTML-koodia.

![Näyttökuva 2024-09-22 232547](https://github.com/user-attachments/assets/0b00a956-ae38-43af-91f6-21ab5c6f8478)

Kysyin virheilmoitukseen liittyen apua ChatGPT:ltä, ja se mainitsi virheestä, että käyttäjällä ei ole oikeuksia, eikä myöskään Apachella nähdä kohdekansioihin. Sen takia minulle tuli virheilmoitus HTTP/1.1 403 Forbidden. Pyörittelin tätä pitkään, ihmettelin ja aloin jo menettää uskoni.
ChatGPT käski minun antaa komennon **sudo chmod 755 /home/aleks** jolloin muilla kun pääkäyttäjällä, on oikeudet lukea ja suorittaa.

Sain kuin sainkin korjattua ongelman, ja tarkistin **curl -I http://piispa.me** ja sain tulokseksi seuraavan, 200, OK! Eli nyt pitäisi toimia. (kellonaika oli oikeasti 21.48, en ole ehtinyt/muuttanut koneen kelloa).

![Näyttökuva 2024-09-22 215136](https://github.com/user-attachments/assets/796da4ea-7635-4aca-a89f-7ce6bdb99f3f)

Tämän jälkeen annoin vielä komennot **sudo a2ensite a.piispa.me.conf** jolle olin tehnyt jo aiemmin VirtualHostin.

![Näyttökuva 2024-09-22 220721](https://github.com/user-attachments/assets/662687ff-3191-4040-9393-7aed681306a4)

![Näyttökuva 2024-09-22 220819](https://github.com/user-attachments/assets/4888424a-97f0-4b61-ac1b-81ec414e4964)

Saman tein myös info.piispa.me -alidomainille.

![Näyttökuva 2024-09-22 221222](https://github.com/user-attachments/assets/5f0703b1-115f-4f6a-9e80-9e2930b5f0b6)

Kävin tarkistamassa sivujen toimivuuden ensin host-koneeltani (Windows-käyttöjärjestelmä, Brave-selain) ja sen jälkeen VirtualBoxin Linuxilta. Molemmilla sivut toimivat!!

![Näyttökuva 2024-09-22 221606](https://github.com/user-attachments/assets/d4b624a9-d87c-4e4f-b133-5d050610170d)

![Näyttökuva 2024-09-22 221618](https://github.com/user-attachments/assets/f38db03d-7192-4a2b-9029-3636d21a8ec9)

![Näyttökuva 2024-09-22 221627](https://github.com/user-attachments/assets/ca437a40-85fc-47ac-b2b2-bcbf1baee115)

Päätin laittaa tältä erää pillit pussiin ja painua pehkuihin. Suljin ssh-yhteyden palvelimeeni klo 23. Jatkoin tehtävien tekoa ja seuraavan osion eli SSH-avaimen luomista 23.9.2024 klo 21.30

## c) Pubkey

*Automatisoi kirjautuminen julkisella SSH-avaimella.*

Tässä osiossa minun tuli luoda SSH avainpari, jonka avulla voin jatkossa kirjautua VirtualBoxin Linuxilla pilvessä sijaitsevaan palvelimeeni ilman, että minun tarvitsee jatkossa syöttää salasanaa. Hain tietoa SSH-avaimista mm. seuraavilta sivuilta: https://www.ssh.com/academy/ssh/keygen, https://en.wikipedia.org/wiki/Public-key_cryptography, https://en.wikipedia.org/wiki/Ssh-keygen, https://en.wikipedia.org/wiki/Secure_Shell.

![Näyttökuva 2024-09-23 215139](https://github.com/user-attachments/assets/6d727a65-f6da-4feb-ad70-b7b57ffcd4cc)

Alkuun tarkistin **whoami** komennolla, kuka olen. Sitten syötin komennon **ssh-keygen -t rsa -b 4096**
-t määritää salauksen tyypin ja -b bittien koon, eli 4096 oli ainakin lukemani perusteella turvallinen ja riittävän pitkä.
Enterillä SSH-avain luotiin sille ennalta määriteltyyn sijaintiin, en antanut SSH-avaimelle erillistä "passphrasea" eli enterillä tästäkin eteenpäin.
Yksityinen (Private) avain sijaitsee nyt täällä: ~/.ssh/id_rsa
Julkinen avain, jonka jaoin pilvessä olevalle palvelimelle, sijaitsee täällä: ~/.ssh/id_rsa.pub

Kopioin avaimen komennolla **ssh-copy-id aleks@ip-osoite**, jonka jälkeen minulta vaadittiin vielä palvelinkoneen salasanaa.

![Näyttökuva 2024-09-23 215606](https://github.com/user-attachments/assets/40e36d81-bacb-4980-a2eb-96f086677790)

Kirjauduin sisään varmistaakseni, että SSH-avaimeni toimii, 

![Näyttökuva 2024-09-23 215707](https://github.com/user-attachments/assets/e1598c44-f13d-4e4d-b851-39c7f5c2287f)

Ja näytti toimivan, sillä minulta ei nyt kysytty salasanaa! Palvelinkoneelleni kopioitu SSH-avain sijaitsee ~/.ssh/authorized_keys.

## d) DNS-tiedot "host"- ja "dig"-komennoilla

*Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla. Käytä kumpaakin komentoa kaikkiin nimiin ja vertaa tuloksia. Katso man-sivulta, miten komennot toimivat - esimerkiksi miten 'dig' näyttää kaikki kentät. Analysoi tulokset. Etsi tarvittaessa uusia lähteitä haastaviin kohtiin. Sähköpostin todentamiseen liittyvät SPF ja DMARC -tietojen yksityiskohdat on jätetty vapaaehtoiseksi lisätehtäväksi. 
Tutkittavat nimet:*

*- Oma domain-nimesi. Vertaa tuloksia nimen vuokraajan (namecheap.com, name.com...) weppiliittymässä näkyviin asetuksiin.*

*- Jonkin pikkuyrityksen, kerhon tai yksittäisen henkilön weppisivut. (Ei kuitenkaan kurssikaverin tällä viikolla vuokrattua nimeä).*

*- Jonkin suuren ja kaikkien tunteman palvelun tiedot.*

Aluksi päivitin ohjelmiston **sudo apt-get update**, jonka jälkeen asensin tldr-työkalun. Sen avulla saan tiivistetyn ja helposti ymmärrettävän version manuaalista (man-komento).

![Näyttökuva 2024-09-23 222724](https://github.com/user-attachments/assets/c6210b76-89b0-420b-9ced-e6db7a7c5a2c)

Host-komento käyttäen tldr-työkalua:

![Näyttökuva 2024-09-23 222818](https://github.com/user-attachments/assets/55e26ef0-50b2-4bd7-8bf8-eca2f1b686cf)

Voin siis hakea komennolla host domainia, ip-osoitteita yms.

Dig-komennon tulos käyttäen tldr-työkalua:

![Näyttökuva 2024-09-23 223337](https://github.com/user-attachments/assets/f3a8cea2-5327-4db0-a3bb-6bcc0fe785ef)

Kysyin ChatGPT:ltä vielä varmistukseksi, mitä eri dig-komennoilla voin tehdä ja sain seuraavan vastauksen:

*Tulokset tarjoavat erilaisia tapoja kysyä DNS-tietoja, sekä peruskäytön että edistyneemmät vaihtoehdot, kuten tietyntyyppisten tietueiden haku, palautteen saaminen eri DNS-palvelimilta, ja DNS-yhteyksien suojaaminen TLS
avulla. Voit käyttää näitä komentoja selvittääksesi verkkotunnusten ja IP-osoitteiden välisiä suhteita tai ratkaistaksesi DNS-ongelmia.*

## piispa.me haku host-komennolla (oma domain)

![Näyttökuva 2024-09-23 224154](https://github.com/user-attachments/assets/fd2eb31a-3e5b-4658-b9e7-964778c8ac15)

Ainoa, mitä tuloksesta ymmärsin, oli domainin julkinen ip-osoite.

Oman domainin haku dig-komennolla. 

![Näyttökuva 2024-09-23 224510](https://github.com/user-attachments/assets/4f00560d-4870-40a8-a83f-01bff6eac66a)

Ymmärsin, että minun tulee ensin asentaa paketti, joka sisältää dig-työkalun. Eli tein siis sen.

![Näyttökuva 2024-09-23 224658](https://github.com/user-attachments/assets/844a65c1-3072-4e16-9454-e01e5d5ccd8f)

Uusi yritys tuotti paremman tuloksen.

![Näyttökuva 2024-09-23 224738](https://github.com/user-attachments/assets/7b6ee46e-88ba-40d2-bbdd-055321eafc08)

Kysyin saamastani vastauksesta jälleen apua ChatGPT:ltä.
- Näyttää käytössä olevan dig-työkalun version, ja mitä sillä hain
- global options näyttää, että käytössä on globaaleja asetuksia
- **Got answer** - haulle on vastaus
- **QUERY** ja **NOERROR** viittaavat kyselyyn, ja siihen, että se ei tuottanut virheitä, sekä niiden perässä kyselyn tunnus.
- flags: qr rd ra kertovat seuraavaa: **qr** eli vastaus kyselyyn, **rd** eli rekursiivinen lippu, eli palvelin voi kysyä myös toisia palvelimia, sekä **ra** tarkoittaa, että rekursiivinen kysely on mahdollinen.
- Question section, näyttää mitä kysyttiin, eli A-recordia domainille piispa.me
- Answer section näyttää palvelimen antaman vastauksen. Domainin IP-osoite, ja kuinka kauan se on voimassa (300 sekuntia)
- Query time kertoo  kyselyn keston
- Server-kohta kertoo, mille palvelimelle kysely suoritettiin, ja missä portissa (#) sekä mitä protokollaa käytettiin
- Kyseyn aikaleima
- Vastauksen koko, 54 tavua

## Pienen yrityksen weppisivut

Tutkin yrityksen www.hierojahelsinki.fi sivuja, sillä tehtävää tehdessä minua särki päähän ja kaipasin hierontaa...

![Näyttökuva 2024-09-23 231218](https://github.com/user-attachments/assets/307b6dd3-3394-4a04-83df-779c3548408c)

Yrityksellä näyttäisi olevan useampi IP-osoite. Oma veikkaukseni on, että tämä on siksi, että jos yksi palvelin kaatuu, eivät sivut kaadu. (Load Balancing).

![Näyttökuva 2024-09-23 231444](https://github.com/user-attachments/assets/a07f7af0-ec52-4155-bacf-25bd2d08f1a2)

## Suuren tai kaikkien tuntema palvelu

Ensimmäisenä mieleeni tuli jokaisen suomalaisen ylpeyden aihe (joskin ei enää), Nokia.

![Näyttökuva 2024-09-23 231737](https://github.com/user-attachments/assets/3e91b214-451e-4e27-b32b-d1af381f7170)

![Näyttökuva 2024-09-23 231828](https://github.com/user-attachments/assets/08fb4dc4-fe1c-45eb-a458-39f1e6d72174)

Olisin toivonut hieman enemmän tutkittavaa näin suuren yrityksen tiedoista, mutta päätin tyytyä tähän. Avasin jo aiemmin, mitä dig-työkalun eri kohdat kertovat, joten en lähde niitä tässä enää avaamaan. Sain tehtävät valmiiksi 23.9.2024 klo 23.32, eli viimeisiin osioihin käytin aikaa 2 tuntia, kokonaisaika tämän viikon tehtäviin siis 6,5 tuntia, plus muu mietiskely ja pohdinta, eli noin + 7 tuntia kaikenkaikkiaan.


## Lähteet

Karvinen T. 2024. Linux Palvelimet 2024 alkusyksy. Luettavissa: https://terokarvinen.com/linux-palvelimet/. Luettu 22.9.2024

Karvinen T. 2018. Name Based Virtual Hosts on Apache. Luettavissa: https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/?fromSearch=name%20based. Luettu 22.9.2024

Karvinen T. 2012. Short HTML5 page. Luettavissa: https://terokarvinen.com/2012/short-html5-page/. Luettu 22.9.2024

Namecheap. 2024. Luettavissa: https://www.namecheap.com/. Luettu 22.9.2024.

SSH 2024. How to use ssh-keygen to generate a new ssh-key? Luettavissa: https://www.ssh.com/academy/ssh/keygen. Luettu 23.9.2024
 
Wikipedia. 2024. Public-key cryptography. Luettavissa: https://en.wikipedia.org/wiki/Public-key_cryptography. Luettu 23.9.2024

Wikipedia. 2024. Secure Shell. Luettavissa: https://en.wikipedia.org/wiki/Secure_Shell. Luettu 23.9.2024

Wikipedia. 2024. ssh-keygen, Luettavissa: https://en.wikipedia.org/wiki/Ssh-keygen. Luettu 23.9.2024

W3C, 2024. Markup Validation Service. Saatavilla https://validator.w3.org/. 

ChatGPT, OpenAI. 2024. Saatavilla https://chat.openai.com. 














