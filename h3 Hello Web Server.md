Tämä, ja kaikki tulevat tehtävät pohjautuvat Tero Karvisen Linux palvelimet kurssin tehtävänantoihin. Suoritan kurssia alkasyksyllä 2024.
Teen kurssin tehtäviä Lenovon Ideapad 5 Pro 13ARH7 -kannettavalla. Käyttöjärjestelmänä koneessa on Windows 11 Home, ja koneessa on 16GB RAM-muistia sekä suorittimena AMD Ryzen 5 6600HS Creator Edition. Näytönohjain: AMD Radeon 660M Graphics. Storage: M.2 SSD 512Gt, vapaana 343Gt.

Aloitin tehtävän tekemisen 8.9.2024 klo 21.14.
# h3 Hello Web Server

## x) Tiivistelmä
- Name Based Virtual Host eli nimipohjainen virtuaalipalvelin.
- Mahdollistaa useamman palvelimen ajamisen samalta IP-osoitteelta.
- Konfiguroimiseen tarvitaan DNS ja APACHE HTTP-palvelimet.
- host-nimi tehdään HTTP-otsikkoon asiakkaan(client) toimesta.

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support.
Luettavissa. https://httpd.apache.org/docs/2.4/vhosts/name-based.html. Luettu 8.9.2024.

- Asenna Apache2: $ sudo apt-get -y install apache2
- Korvaa oletussivu: $ echo "Default"|sudo tee /var/www/html/index.html
- Testataan oletussivusto: $ curl localhost

Karvinen, T. 2018. 

## a) Asenna Apache2-weppipalvelin
Viime oppitunnilla 4.9.2024 seurasimme Tero Karvista, kun hän opetti meille Apachesta, ja kokeilimme terminaalissa hakea "curl http://localhost".
Tarkoitus oli nähdä, mitä saa ilmoitukseksi, kun Apachea ei oltu vielä asennettu. Nämä kuvat ovat siis taltioutu tuolloin.

![Näyttökuva 2024-09-04 195642](https://github.com/user-attachments/assets/fd917a30-8851-449f-902b-880a6938cab9)

Tämän jälkeen asensin Apache2-weppipalvelime sudo-oikeuksin "sudo apt-get install apache2".

![Näyttökuva 2024-09-04 195718](https://github.com/user-attachments/assets/3cf6dbb3-c2b4-4790-ba60-1d5d8b373f84)

Tämän jälkeen tein muutoksia terminaalissa, jotta pääsimme localhost 404 error näkymästä apache2-oletussivulle.
Apache2 asennuksen jälkeen komennolla "sudo systemctl start apache2" saimme palvelimen käynnistettyä. Minulta kesti hetki muistella, mitä tarkalleenottaen teimmekään aiemmin tällä viikolla. Joten yritin etsiä lokitiedoista merkintää tästä, tajuamatta oikeastaan mitään. Sitten mieleeni juolahti, että käynnistimme Apachen terminaalissa. Eli samalla tavoin palvelimen saa myös suljettua komennolla "sudo systemctl stop apache2". Kokeilin tuota, ja palvelin lakkasi toimimasta. Sitten uudestaan käynnistys, ja voíla!

![Näyttökuva 2024-09-08 221042](https://github.com/user-attachments/assets/0328083f-9347-41a4-9957-97366a99051f)

## b) Lokirivit
Tämän jälkeen tehtävänä oli tutkia terminaalissa lokirivejä, jotka syntyivät, kun latasin palvelimeltani sivun. Avasin Mozilla-selaimen ja kirjoitin URL-kenttään localhost/~aleksp. Tulos oli oletettu, koska kyseistä sivua en ollut vielä luonut. Eli tuloksena erroria, not found. Seuraavaksi tarkastin lokirivit terminaalista. Hain lokit komennoilla "sudo tail -1 /var/log/apache2/access.log" sekä "sudo tail /var/log/apache2/error.log"

![Näyttökuva 2024-09-08 222240](https://github.com/user-attachments/assets/f7ec3da2-fc17-4641-bcef-c444e55a353b)

![Näyttökuva 2024-09-08 224659](https://github.com/user-attachments/assets/0a8b769d-5757-498d-81e5-1ee82349e0a9)

![Näyttökuva 2024-09-08 223729](https://github.com/user-attachments/assets/38ca3972-5f20-489f-9c27-b8b8ea9883bc)

Access logissa näkyvä GET- hae sivua palvelimelta. "200" eli tilakoodi, joka kertoo, että haku onnistui.
Tilakoodin jälkeinen 3380 tarkoittaa pyynön kokoa tavuina. 404 on virhekoodi. Mozilla on selain, jolla haku tehtiin ja Linux x86_64 taas viittaa koneeseen (tapauksessani tähän virtuaalikoneeseen).

## c) Etusivu uusiksi

Alkuun, poistin Apache2 oletussivun käytöstä komennolla "sudo a2dissite 000-default.conf".
Tämän jälkeen syötin sudo-oikeuksillani salasanan. Oletussivu oli nyt poistettu käytöstä. Jotta konfiguraatio voisi astua voimaan, minun tuli syöttää komento "sudo systemctl reload apache2".
![Näyttökuva 2024-09-08 225847](https://github.com/user-attachments/assets/aa88eba8-0799-4d74-bd18-b3c33c942a9b)

Seuraavaksi loin uuden Name Based virtuaalipalvelimen. Komennolla "sudoedit /etc/apache2/sites-available/hattuexample.com.conf". Tämä vaati jälleen salasanaani.
Seuraavaksi komentorivin sijaan minulle aukesi GNU nano 7.2. tekstieditori. 
Tero Karvisen https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/ ohjeita seuraten, syötin seuraavaanlaisen "koodin".

![Näyttökuva 2024-09-08 233100](https://github.com/user-attachments/assets/35e24888-2a6b-44bc-98bc-e360c25309a4)
Tallensin Ctrl+S ja poistuin Ctrl+X. Toivoin parasta, että tein oikein.

Tämän jälkeen aktivoin uuden http://localhost oletussivun.
Syötin komennon "sudo a2ensite hattu.example.com.conf" ja "sudo systemctl reload apache2". 

![Näyttökuva 2024-09-08 233307](https://github.com/user-attachments/assets/0f35573f-5536-43dc-84a1-2a1a58abad85)

Komennolla echo pääsin tekemään suoraan komentorivillä html-koodia, joka tulee etusivulle.

![Näyttökuva 2024-09-09 000221](https://github.com/user-attachments/assets/5e766fe3-dce2-49d9-aea3-3f8c35d86cee)

Testasin, onnistuiko ja syötin komennon curl localhost. Näyttäisi toimivan.

![Näyttökuva 2024-09-09 000744](https://github.com/user-attachments/assets/73dd2148-6fd0-4b76-ab1d-ae47b42f4f8c)

Kokeilin samaa selaimessa. Mutta nyt törmäsinkin virheeseen. Päädyin edelleen Apache-aloitussivulle.

![Näyttökuva 2024-09-09 000926](https://github.com/user-attachments/assets/38b6df14-4e5b-42b7-af0f-b3c3b0442423)

Kysyin tästä ChatGPT:ltä, ja sain seuraavan vastauksen:
"Tämä tilanne johtuu todennäköisesti siitä, että Apache palvelee edelleen oletussivustoa, kun selaimessa käytät osoitetta localhost, koska selaimessa ei ole määritetty pyydettävää verkkotunnusta. Koska olet luonut nimipohjaisen virtuaalipalvelimen hattu.example.com, se toimii vain silloin, kun kyseinen nimi (verkkotunnus) on pyynnössä mukana."

Eli siis kaikki oli edelleen kuten pitikin. Seuraavaksi simuloin paikallisesti nimipalvelinta (DNS).

"sudoedit /etc/hosts" pääsin näkemään ja muokkaamaan host-palvelimia. Lisäsin uudelle riville 127.0.0.1 hattu.example.com

![Näyttökuva 2024-09-09 001604](https://github.com/user-attachments/assets/3b86b73a-07b1-4d6b-8a69-e7b2725b62b7)

Kokeilin, ja edelleen curl localhost näyttää oikein, mutta Mozilla ei. Mietin, olisiko minun tullut kirjoittaa hattu.example.com tuon localhostin päälle? 
Kirjoitin hakukentään hattu.example.com, ja sivut näyttivät toimivan kuten pitää. Ainoastaan Ä-kirjainten kanssa hieman vaikeuksia.

![Näyttökuva 2024-09-09 001914](https://github.com/user-attachments/assets/fe44508a-86bd-4643-be8a-28e2010fdc55)

Tämän tehtyäni, olin notkunut tietokoneella jo pitkään, ja päätin, että suoritan tehtävän viimeiset osiot seuraavana päivänä. Ajoin vielä terminaalissa "sudo apt-get update" ja suljin koneen, sekä VirtualBoxin. Lopetin tehtävät 9.9.2024  klo 0.30.

Palasin tehtävien pariin 














## Lähteet

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support.
Luettavissa. https://httpd.apache.org/docs/2.4/vhosts/name-based.html. Luettu 8.9.2024.

Karvinen, T. 2018. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/. Luettu 8.9.2024


