Tämä, ja kaikki tulevat tehtävät pohjautuvat Tero Karvisen Linux palvelimet kurssin tehtävänantoihin. Suoritan kurssia alkusyksyllä 2024. 
Teen kurssin tehtäviä Lenovon Ideapad 5 Pro 13ARH7 -kannettavalla. Käyttöjärjestelmänä koneessa on Windows 11 Home, ja koneessa on 16GB RAM-muistia
sekä suorittimena AMD Ryzen 5 6600HS Creator Edition. 
Näytönohjain: AMD Radeon 660M Graphics. Storage: M.2 SSD 512Gt, vapaana 343Gt.
Koneelle on asennettu VirtualBox virtualisointiohjelma, joka pyörittää tehtävissä näkyvää Linux Debian-virtuaalikonetta.

# h7 Maalisuora

Aloitin tekemään tehtävää 2.10.2024 klo 21.05

## Tiivistelmä

Kurssi alkaa olemaan loppusuoralla, ja nyt on aika hieman opetella ohjelmointia.
- Tässä tehtävässä tulen käyttämään muutamaa eri ohjelmointikieltä ja tekemään yksinkertaisen 'Hello World' koodin.
- Lisäksi luon uuden shellscript komennon, joka on julkisessa käytössä. 
- Käy läpi vanhaa arvioitavaa labraharjoitusta hieman soveltaen, sekä asennan uuden Linux-virtuaalikoneen erillistä arvioitavaa labratehtävää varten.

## a) Kirjoita ja aja "Hei maailma" kolmella kielellä.

Valitsin tätä tehtävää varten kieliksi C, Pythonin sekä Rubyn.

Ensiksi päivitin paketit **sudo apt-get update** komennolla. Tämän jälkeen asensin Rubyn **sudo apt-get install ruby-full**.
Loin micro-editorilla tiedoston 'hello.rb' ja ajoin sen. Tajusin tämän jälkeen, että loin tiedoston suoraan /home-hakemistoon, joten kävin vielä siirtämässä sen aiemmin 
tunnilla tekemääni /code-tiedostokansioon.

![Näyttökuva 2024-10-02 210821](https://github.com/user-attachments/assets/04ca1b99-5f91-4903-9173-df198995130c)

![Näyttökuva 2024-10-02 211035](https://github.com/user-attachments/assets/7f8e4856-9b28-49f4-b7a6-b6cef19e55f9)

![Näyttökuva 2024-10-02 211327](https://github.com/user-attachments/assets/9ec26dd8-14f7-4bd6-820e-8bf426dde98e)

![Näyttökuva 2024-10-02 211258](https://github.com/user-attachments/assets/8146c0ce-01b7-4050-aa37-bb4ffe4df1f7)

![Näyttökuva 2024-10-02 211849](https://github.com/user-attachments/assets/702baab0-5b6c-430b-9ccd-ef68f4804cfa)

Sitten oli vuorossa Python, joka olikin jo valmiiksi asennettuna Debianiin.
Ehdinkin jo illan luennon aikana tehdä koodin Pythonilla. Loin /home hakemistoon komennolla **mkdir code** kansion, jonne loin microlla Python-tiedoston.
Avasin tiedoston, jotta koodin näkee, ja sitten vielä erikseen komentorivillä kun se ajetaan.

![Näyttökuva 2024-10-02 212044](https://github.com/user-attachments/assets/96e94551-882b-44a3-8bd9-31d8e5574ff9)

![Näyttökuva 2024-10-02 212058](https://github.com/user-attachments/assets/7f6a63a1-ca87-4f75-afa3-6ab91de690a7)

![Näyttökuva 2024-10-02 212156](https://github.com/user-attachments/assets/7dd62654-5118-49ae-85b8-5c8bd1d90e32)

Viimeisenä olikin C-kielen vuoro. Tästä Tero näyttikin mallia tunnin päätteeksi, mutta meni niin hirmusita vauhtia eteenpäin, etten pysynyt ihan mukana.
Onneksi apua löytyi Teron sivulta Hello World https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/.

Eli jälleen loin /code-tiedostokansioon microlla uuden tiedoston, tällä kertaa hello.c-nimisen.
Microssa kirjoitin koodin, CTRL+S ja CTRL+Q tallensin ja poistuin.
**cat** komennolla näin ainoastaan koko koodin, enkä pelkkää haluttua viestiä. Mutta lisäkomentojen jälkeen tämäkin onnistui. Tässä välissä ehti
kuitenkin tulla jo perinteinen kardinaalimoka, eli (;) jäi puuttumaan. Viimeksi olen koodannut syksyllä 2023, Pythonia, jossa puolipisteitä ei tarvita...

![Näyttökuva 2024-10-02 212347](https://github.com/user-attachments/assets/d46fad96-0b0c-4649-955d-afae57c472ee)

![Näyttökuva 2024-10-02 212505](https://github.com/user-attachments/assets/cb21e28f-a373-489a-b9ca-596af6a330d1)

![Näyttökuva 2024-10-02 212836](https://github.com/user-attachments/assets/678bdd1d-8db7-4518-aee2-1c04c1be9080)

![Näyttökuva 2024-10-02 213105](https://github.com/user-attachments/assets/d765eed6-ef2f-40bf-b363-a2fe4a39943c)

![Näyttökuva 2024-10-02 213251](https://github.com/user-attachments/assets/0dcd335b-9cdc-4682-b91c-495084ce371e)

Eli sain kaikilla kolmella kielellä tulostumaan "Hello World"-tervehdyksen. Kielistä Ruby sekä C olivat itselleni täysin vieraita.

## b)  Laita Linuxiin uusi komento niin, että kaikki käyttäjät voivat ajaa sitä.

Tässä tehtävässä piti luoda ShellScripti, jota kaikki koneella olevat käyttäjät voivat ajaa. Eli tämä menee eri oikeuksien alle (**ugo+rwx**), vaikka käyttäjällä ei olisi sudo-oikeuksia, jos ymmärsin oikein, mitä tässä haettiin.
Aloitin sen luomalla microlla viesti.sh-tiedoston. Komento oli pelkkä viesti, jonka käyttäjälle ilmestyy kun antaa komennon.

![Näyttökuva 2024-10-02 213742](https://github.com/user-attachments/assets/f3e9ab7a-b349-46bc-a3d5-ed8613e4b301)

Ryhdyin tallentamisen jälkeen määrittämään oikeuksia tälle komennolle. Sitten kokeilin **sudo cp viesti.sh /usr/local/bin/** kopioida komennon, tässä kuitenkaan onnistumatta.
Sain erroria, että bash: komentoa ei löydy. Sitten tajusin, että unohdin laittaa **#!/bash/bin** tiedoston alkuun, eli menin korjaamaan sitä microon.
Edelleen sain erroria... kokeilin luoda peililinkkiä komennosta, käyttäen komentoa **sudo ln -s /home/aleksp/viesti.sh /usr/local/bin/viesti**
Tämän jälkeen kokeilin komentoa, ja se toimi! Tarkistin vielä siten,e ttä avasin uuden terminaalin, ja ajoin komennon, toimii myös siellä.

![Näyttökuva 2024-10-02 214533](https://github.com/user-attachments/assets/c8ffb144-d7d8-4fa8-9721-6dceb9275ec6)

![Näyttökuva 2024-10-02 215809](https://github.com/user-attachments/assets/f4a5540c-8428-4c71-9f1d-cbf968dc0e54)

Päätin nyt lopettaa tältä erää, ja jatkaa tehtävän seuraavat osat loppuun myöhemmin. Sain hommat tältä erää valmiiksi klo 22.00.

## c) Ratkaise vanha arvioitava labratehtävä soveltavin osin.

*Pääsin jatkamaan tehtävien tekemistä 7.10.2024 klo 23 ->*
Rehellisesti myönnän, että tämän tehtävän tekeminen jäi osaltani todella heikoksi. Yksinkertaisesti aikaa ei ollut riittävästi käytössäni, jotta olisin pystynyt pitkäjänteisesti ja perinpohjaisesti käymään aiempia labraharjoituksia läpi. Liian monta kurssia samaan aikaan sekä tentit ja aikaa opiskellaa aivan liian vähän (ja ainoastaan myöhään iltaisin, aina ei onnistu silloinkaan. kts. vanhempainvapaalla ja paljon itkevä 1-vuotias). 

*Tämä menee varmaan siihen Teron niin sanottuun sepittämiseen, vaikka totta puhunkin.* 

Luin kuitenkin vanhoja labratehtäviä läpi, ja huomasin, että monissa oli todella paljon eri asioita käyty kurssin aikana läpi vrt. tähän meidän kurssiimme. Tähän voi olla syynä muuttuneet käytännöt (lähiopetus vs. onlineopetus) sekä Ubuntun vaihtuminen Debianiin?

Siitä huolimatta, asensin kuitenkin VirtualBoxiin uuden virtuaalikoneen *LabHarjoitus*, johon loin käyttäjän, ajoin päivitykset **sudo apt-get -y dist-upgrade** sekä **sudo apt-get update** ja asensin palomuurin **sudo apt-get install ufw**. Harjoittelin Apachen asennusta ja käyttöä, sillä siinä tuntuu olevan muistamista. Aion vielä tutkia edellisiä labroja läpi mikäli vain ehdin ja yritän kuitenkin "syyslomalla" tehdä ja katsella näitä arvioitavia labroja paremmmalla aikataululla, vaikka kurssi onkin siinä vaiheessa jo taputeltu. Tietenkin päivitän tänne sitten lisää.

## d) Asenna itsellesi tyhjä virtuaalikone arvioitavaa labraa varten. 

Asensin Teron tehtävän h1 mukaisesti uuden virtuaalikoneen arvioitavaa labraa varten. Loin käyttäjän ja annoin sille vahvan salasanan. Tein pakettipäivitykset **sudo apt-get update**, **sudo apt-get -y dist-upgrade** sekä asensin myös palomuurin, ja laitoin sen päälle **sudo ufw enable**. Kone sai nimekseen *AleksLab*, jotta se erottuisi selkeästi kurssilla muuten käyttämästäni virtuaalikoneesta.

![Näyttökuva 2024-10-04 221055](https://github.com/user-attachments/assets/6b178401-febe-456f-9bdf-3953a3ecdbb8)

Sain asennukset valmiiksi arvioitavaa labraa varten 8.10.2024 klo 01

## Lähteet

Karvinen, T. 2024. Linux palvelimet alkusyksy 2024. Saatavissa: https://terokarvinen.com/linux-palvelimet/. Luettu 2.10.2024.

Karvinen, T. 2018, Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04. Saatavissa: 
https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/. Luettu 2.10.2024

Karvinen, T. 2007, Shell Scripting. Saatavissa: https://terokarvinen.com/2007/12/04/shell-scripting-4/. Luettu 2.10.2024.
