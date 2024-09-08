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
Apache2 asennuksen jälkeen komennolla "sudo systemctl start apache2" saimme palvelimen käynnistettyä. Minulta kesti hetki muistella, mitä tarkalleenottaen teimmekään. Joten yritin etsiä lokitiedoista merkintää tästä, tajuamatta oikeastaan mitään. Sitten mieleeni juolahti, että käynnistimme Apachen terminaalissa. Eli samalla tavoin palvelimen saa myös suljettua komennolla "sudo systemctl stop apache2". Kokeilin tuota, ja palvelin lakkasi toimimasta. Sitten uudestaan käynnistys, ja voíla!

![Näyttökuva 2024-09-08 221042](https://github.com/user-attachments/assets/0328083f-9347-41a4-9957-97366a99051f)

## b) Lokirivit
Tässä tehtävässä







## Lähteet

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support.
Luettavissa. https://httpd.apache.org/docs/2.4/vhosts/name-based.html. Luettu 8.9.2024.

Karvinen, T. 2018. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/. Luettu 8.9.2024


