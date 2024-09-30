Tämä, ja kaikki tulevat tehtävät pohjautuvat Tero Karvisen Linux palvelimet kurssin tehtävänantoihin. Suoritan kurssia alkasyksyllä 2024. 
Teen kurssin tehtäviä Lenovon Ideapad 5 Pro 13ARH7 -kannettavalla. Käyttöjärjestelmänä koneessa on Windows 11 Home, ja koneessa on 16GB RAM-muistia
sekä suorittimena AMD Ryzen 5 6600HS Creator Edition. 
Näytönohjain: AMD Radeon 660M Graphics. Storage: M.2 SSD 512Gt, vapaana 343Gt.
Koneelle on asennettu VirtualBox virtualisointiohjelma, joka pyörittää tehtävissä näkyvää Linux Debian-virtuaalikonetta.

# h6 Hello Django

## a) Tee yksinkertainen esimerkkiohjelma Djangolla.

*Voit käyttää testipalvelinta, kunhan se ei näy Internetiin.
Riittää, kun ohjelmasi näkyy esimerkiksi Django Adminsissa.
Voit halutessasi tehdä aivan samanlaisen kuin Teron CRM-esimerkissä. Jos olet jo taitavampi, voit hieman soveltaa.
Karvinen 2021: Django 4 Instant Customer Database Tutorial*

Aloitin tämän viikon tehtävän tekemisen sunnuntaina 29.9.2024 klo 18.30.
Ensiksi luin läpi Teron ohjeet Djangon tutoriaalista. Teron ohjeissa mainittiin, että tätä ei saa laittaa internetiin, joten ollaan siis tarkkoina!

Karvinen, 2021. https://terokarvinen.com/2022/django-instant-crm-tutorial/.

Tämän jälkeen käynnistelin VirtualBoxia ja kirjauduin sisään Linuxilleni. 
Tuttuun tapaan päivitykset, eli **sudo apt-get update**. Tein vielä varmistukseksi upgrade-pyynnön distrolle, mikäli siellä olisi jotain päivitettävää.
Eli komento **sudo apt-get dist-upgrade**. Näytti kuitenkin siltä, että kaikki on ajantasalla, eli mitään isompaa ei nyt päivittynyt.

![Näyttökuva 2024-09-29 181625](https://github.com/user-attachments/assets/3a082681-3319-4adc-82a4-65fdc734615e)

![Näyttökuva 2024-09-29 182017](https://github.com/user-attachments/assets/403f1418-16f6-4c07-8596-102997cbd96b)

Päivitysten jälkeen en ehtinyt sen enempää tekemään, sillä alkoi lapsen iltatoimet, joten tekeminen keskeytyi klo 19 aikoihin. Palasin tehtävän pariin klo 20.30

Asensin komentorivillä virtuaalisen kehitysympäristön komennolla **sudo apt-get -y install virtualenv** . Tässä virtuaaliympäristössä tehdään tämän viikon tehtävä.

![Näyttökuva 2024-09-29 203246](https://github.com/user-attachments/assets/70871a00-f938-4864-9e72-59387d2f010f)

Loin virtuaaliympäristön ja asensin Python3-paketit komennolla **virtualenv --system-site-packages -p python3 env/**. Samalla komento loi kansion env/, jossa sijaitsee viimeisimmät paketit.

![Näyttökuva 2024-09-29 203954](https://github.com/user-attachments/assets/f8009c37-4dd6-41ca-9768-7acf22d3bd29)

Otin virtuaaliympäristön käyttöön **source env/bin/activate** sekä tarkistin, että olen varmasti virtuaaliympäristössä komennolla **which pip**. Katsoin DuckDuckGosta, mikä pip on, ja ensimmäisenä tuli vastaan wikipedia-artikkeli, jossa luki, "pip is a package-management system written in Python". https://en.wikipedia.org/wiki/pip_(package_manager).  

![Näyttökuva 2024-09-29 204219](https://github.com/user-attachments/assets/1e573c45-3670-4098-83fa-6ae7f1c7f0f6)

Tämän jälkeen kirjoitin micro-editorilla uuden tiedoston requirements.txt, johon kirjoitin django. Tallensin CTRL+S ja poistuin CTRL+Q editorista. Sitten tarkistin cat-komentoa käyttäen, että olin varmasti kirjoittanut oikein. Tero varoitteli oppitunnilla, että "mikäli kirjoittaa väärin ja jatkaa eteenpäin, kone kaapataan ja ulkovaltioiden hakkerit pääsevät valloilleen." Eli tarkkuutta kirjoittamisessa.
Sitten vielä asentamaan Djangoa komennolla **pip install -r requirements.txt**

![Näyttökuva 2024-09-29 205431](https://github.com/user-attachments/assets/c51fcea4-3cd3-4f0e-8698-d0779daf0a2a)

**django-admin --version** komennolla tarkistin, mikä versio asentui. Viimeisin taisi asentua, 5.1.1, ja sama oli mielestäni myös oppitunnilla Teron näyttämässä demossa.

![Näyttökuva 2024-09-29 205718](https://github.com/user-attachments/assets/401acb65-d55c-403f-9526-2a6c9be1b2e4)

Seuraavaksi vuorossa oli aloittaa projekti tehtävää varten, joten loin projektin "aleksco" ja tarkistin, lähtikö djangon avaruuskiituri lentämään.
Avasin selaimen, ja URL-kenttään kirjotin localhost-osoitteen, ja porttinumeron :8000.

![Näyttökuva 2024-09-29 210411](https://github.com/user-attachments/assets/5557f4ce-4392-4971-8326-911e205b5c52)

Avaruuskiituri lähti liikkeelle, seuraavaksi Tatooinen kiiturikisaan siis :D

Sitten oli aika luoda pääkäyttäjä. Lisäsin osoitekenttään localhostin perään vielä /admin, josta tulisi avautua kirjautumista varten sivu. Mitään ei kuitenkaan siellä ollut, joten palasin terminaaliin. Palasin terminaaliin CTRL+C, ja keskeytin testin. 

![Näyttökuva 2024-09-29 210846](https://github.com/user-attachments/assets/c848f805-e14e-4c5c-9c4e-f10293463071)

![Näyttökuva 2024-09-29 211039](https://github.com/user-attachments/assets/e2a472bf-3c65-4795-85c7-1c354ec30227)

Päivitin tietokannat:

![Näyttökuva 2024-09-29 211538](https://github.com/user-attachments/assets/8284973a-6c97-4a31-ab86-3353b531ba9e)

Ja aloin luomaan pääkäyttäjää, mutta ensin asensin salasanageneraattorin 
komennolla **sudo apt-get install pwgen** ja generoin sillä vahvan salasanan **pwgen -s 20 1**. Sitten loin pääkäyttäjän komennolla **./manage.py createsuperuser** ja kokeilin uudestaan mennä /admin-sivulle.

![Näyttökuva 2024-09-29 212856](https://github.com/user-attachments/assets/9780b395-a78f-4ba8-9162-15457b6e3b04)

Tuli sen verran vahva salasana, että sain pari kertaa kirjoitettua sen väärin. Törmäsin kuitenkin selaimessa ongelmaan, sillä sivu ei toiminut.

![Näyttökuva 2024-09-29 213239](https://github.com/user-attachments/assets/dfc6355f-32b7-4c2c-b133-b7c9f8624cf2)

Hetken pähkäilin, miksi ei, missä on vika. Kunnes tajusin, että minun tulee käynnistää homma uusiksi. Eli **./manage.py runserver**
Tuon jälkeen Shift+F5 ja voíla! Alkoi Lyyti kirjoittaa. Syötin pääkäyttäjän tiedot.

![Näyttökuva 2024-09-29 213511](https://github.com/user-attachments/assets/ce8fc66d-208d-4b8e-a880-aafb5a95a5da)

![Näyttökuva 2024-09-29 213704](https://github.com/user-attachments/assets/3d0d3f3a-4397-443d-95c1-531468a368b4)

Sitten lähdin lisäämään uutta käyttäjää käyttöliittymässä, eli kohdasta +Add klikkasin ja loin uuden käyttäjän. Käyttäjä sai nimekseen *Testinen* ja myönsin hänelle *Staff* sekä *Superuser*-oikeudet.

![Näyttökuva 2024-09-29 214210](https://github.com/user-attachments/assets/6ea7c740-8084-40a4-a4e7-7831778ebfc3)

![Näyttökuva 2024-09-29 214440](https://github.com/user-attachments/assets/ef87a563-cf45-4bde-9257-64359ed91a93)

Kirjauduin ulos pääkäyttäjänä, ja kirjauduin sisään juuri luomallani käyttäjällä.

![Näyttökuva 2024-09-29 214615](https://github.com/user-attachments/assets/8b0e14d5-acb4-41d7-91f2-57bb31ca9b69)

Seuraavaksi lähdin luomaan tietokantaa. Sammutin Djangon, ja syötin komennon **./manage.py startapp crm**. Käynnistin Djangon uudestaan, kunnes tajusin, että en voi käyttää komentoriviä tuolloin, joten sammutin sen. Annoin uudestaan komennon **./manage.py startapp crm**, mutta tuli virheilmoitus, että kyseinen kansio on jo olemassa. Eli siis seuraavaan vaiheeseen.

![Näyttökuva 2024-09-29 215818](https://github.com/user-attachments/assets/644e9b09-bd0f-4b12-8fb4-5011398dfe37)

Avasin micro-editorin ja lisäsin crm-sovelluksen muiden joukkoon.

![Näyttökuva 2024-09-29 220117](https://github.com/user-attachments/assets/ce6ad076-b393-4a30-900a-efdabf4cd9dc)

![Näyttökuva 2024-09-29 220048](https://github.com/user-attachments/assets/e06ab7a7-6846-47e0-8300-29e166a47fb1)

Sitten rupesin luomaan komennolla **micro crm/models.py** tietokantaan "Customer"-taulua, ja kenttä sai nimekseen "name". Sitten ajoin uudestaan komennot **./manage.py makemigrations** ja **./manage.py migrate**.

![Näyttökuva 2024-09-29 220818](https://github.com/user-attachments/assets/a06fb452-9924-4276-8d94-d74437306dce)

![Näyttökuva 2024-09-29 220915](https://github.com/user-attachments/assets/f4720876-0b96-4ee6-8c0e-ed0eac11350f)

Rekisteröin tietokannan komennolla **micro crm/admin.py**.

![Näyttökuva 2024-09-29 221109](https://github.com/user-attachments/assets/8903b17f-b222-4aaf-980b-030a99688371)

Käynnistin Djangon komennolla **./manage.py runserver** ja nyt siellä näkyi Customers-kenttä. Lähdin lisäämään sinne kaksi asiakasta. Nimet eivät kuitenkaan tallentuneet, vaan näkyivät muodossa "Customer object(1)" ja "Customer object(2)". Tämä olikin vissiin ihan tarkoituskin.

![Näyttökuva 2024-09-29 221645](https://github.com/user-attachments/assets/8924b198-2dde-4e87-ac99-8b26b7ccaa7d)

Poistuin Djangosta ja palasin komentoriville. 
Siellä avasin jälleen micro-editorin, jossa lähdin muokkaamaan models-tiedoston tietoja. Eli **micro crm/models.py**.
Muokkasin customer-luokkaa siten, että nyt se palauttaa arvot, jotka määritettiin käyttäjien nimiksi.

![Näyttökuva 2024-09-29 222611](https://github.com/user-attachments/assets/cb0629f2-8e05-411a-ac0b-6040682aa123)

Lähdin antamaan komentoa **./manage.py makemigrations**, mutta sain syntax error-viestiä. Aloin miettimään, että missä vika, sillä seurasin Teron ohjeita tarkasti. Myönnettäköön, että koodaaminen ei ole vahvuuksiani, ja viime kerrasta on aikaa jo noin vuosi, koska ei ole aikaa harrastaa :(. Luin error-logia läpi, ja kävin tarkistamassa äsken muokkaamaani crm/models.py tiedostoa. Vika löytyi onneksi helposti, koska koodia oli jopa huimat 5 riviä, minulta oli jäänyt yksi välilyönti välistä...

![Näyttökuva 2024-09-29 223540](https://github.com/user-attachments/assets/f5412696-1bcd-42e1-abee-29ea2a9ad8ec)


Sitten uudestaan **./manage.py makemigrations** ja **./manage.py migrate**. Django käyntiin **./manage.py runserver** ja nyt nimet tulivat esiin. Hei Pentti, Hei Matti!

![Näyttökuva 2024-09-29 224501](https://github.com/user-attachments/assets/82772fba-0487-43f2-880d-c90f3752e406)

![Näyttökuva 2024-09-29 224306](https://github.com/user-attachments/assets/ba827e36-68c7-466a-aae5-45f8a932c925)

Ensimmäinen osa viikon kotitehtävistä oli nyt valmis. Päätin jatkaa seuraavana päivänä, sillä lapsi tykkää herätä aikaisin, ja minä en. Lopetin siis tältä erää tekemisen 29.9.2024 klo 22.47.

## b) Tee Djangon tuotantotyyppinen asennus
*Voit halutessasi tehdä asennuksen omalle, paikalliselle virtuaalikoneelle. Sen ei tarvitse näkyä Internetiin.*

Karvinen 2021: Deploy Django 4 - Production Install

Palasin tehtävän pariin 30.9.2024 klo 20.42, kun illan luento oli päättynyt. 
Aloitin tehtävän lukemalla läpi Teron dokumentin, kuinka tehdä tuotantotyyppinen Djangon asennus. 

Ohjeiden alussa käskettiin asentamaan Apache, mutta se oli jo tehty useita viikkoja sitten, joten en lähtenyt sitä asentamaan. Aiemmassa tehtävässä korvattiin Apachen default-sivu Hattu Examplella, joten näytän sen vielä tässä.

Aloitin päivittämällä paketit **sudo apt-get update** 

![Näyttökuva 2024-09-30 204817](https://github.com/user-attachments/assets/a9b11764-2671-4ac9-9025-3d295a07467d)
 
![Näyttökuva 2024-09-30 205536](https://github.com/user-attachments/assets/38e1fcb0-3b10-4c51-aa03-69505d7964d7)

Apache toimii. Seuraavaksi loin uusia hakemistoja Teron ohjeiden mukaisesti. Olin jo luomassa uutta virtual hostia, kunnes totesin, että parempi korvata nano-editori ja poistuin editorista. Sitten määritin micro-editorin pääeditoriksi komennolla **export EDITOR=micro**. Microon pääsi jo tehtävän ensimmäisessä vaiheessa paremmin sisälle, ja on helpompaa, kun on samat näppäinmääritykset käytössä, eikä eri editoreja ja eri näppäinmäärityksiä, siksi siis tein näin. Tämän jälkeen lähdin uudestaan luomaan virtual hostia totuttuun tapaan.

![Näyttökuva 2024-09-30 210246](https://github.com/user-attachments/assets/54b3754e-4781-4322-80c6-6055893f5048)

![Näyttökuva 2024-09-30 211511](https://github.com/user-attachments/assets/8b71b262-a272-4d5e-8860-f7a715100b8b)

![Näyttökuva 2024-09-30 211428](https://github.com/user-attachments/assets/0f76709a-03b5-41e1-b516-e59bd3e8eb19)

Sitten päivitettiin Apache. **sudo a2ensite aleksco.conf**, jotta saadaan sivu päälle. **Sudo a2dissite 000-default.conf** oletussivun lopettamiseksi, tästä tuli kuitenkin viesti, että on jo aiemmin disabloitu. Sitten ajoin konfigurointitestin Apachelle, **/sbin/apache2ctl configtest**, mutta sain ohjeista poiketen error-viestin. Luin tämän läpi, ja menin muokkaamaan aiemmin tekemääni aleksco.conf-virtuaalihostia. Siellä oli ylimääräinen sarkain (<). Sitten CTRL+S ja CTRL+Q, ja uusiksi configtest.

![Näyttökuva 2024-09-30 212541](https://github.com/user-attachments/assets/901c6823-0241-4961-bfd4-6c04b442b33f)

Teron ohjeissa luki näin *If it only complains about not know it's public name (AH00558) and says "Syntax OK", the config files are good to go.*

![Näyttökuva 2024-09-30 212709](https://github.com/user-attachments/assets/e07e68dc-1f17-476e-b72f-7d23ba16e7db)

Eli sama koodi AH00558 tuli minullakin, eli GG.
Seuraavaksi käynnistin Apachen uudelleen **sudo systemctl restart apache2** ja kävin curl-komennolla tarkistamassa, lähtikö static-tiedosto pelittämään. Näyttäisi siltä, että toimii!

![Näyttökuva 2024-09-30 213051](https://github.com/user-attachments/assets/d13a6e0e-8d0f-4fde-a48c-f9c0f87ba537)

Sitten aloitin asentamaan virtuaaliympäristöä. Hieman jäi mietityttämään, että pitääkö ympäristö asentaa uudelleen, kun tehtävän ensimmäisessä osassa se jo asennettiin. Seurasin kuitenkin ohjeita, enkä alkanut sen enempää niitä kyseenalaistamaan.

![Näyttökuva 2024-09-30 213813](https://github.com/user-attachments/assets/b308214d-f4db-4dbe-bf3d-4e4ce818a432)

Aktivoin virtuaaliympäristön, ja tarkistin, että missä ollaan **which pip** komennolla.

![Näyttökuva 2024-09-30 213950](https://github.com/user-attachments/assets/609cae7a-97f4-4c04-b67b-59c201e65935)

Sitten uudestaan asentamaan Djangoa, ensin loin microlla tekstitiedoston *requirements.txt* ja sinne kirjoitin *django*. Tallensin CTRL+S ja poistuin CTRL+Q. **cat requirements.txt** tarkistin vielä, että tulihan kirjoitettua varmasti oikein.

![Näyttökuva 2024-09-30 214338](https://github.com/user-attachments/assets/2440b868-ae41-4fd0-8fa0-7269fe592b7d)

![Näyttökuva 2024-09-30 214414](https://github.com/user-attachments/assets/a3cdc646-24e1-46c5-bc2b-46e4af5e27bf)

Sitten asensin Djangon. Tällä kertaa ei tullut latauspalkkeja ym. kuten edellisessä osassa, joten saattaa olla, että turhaan nyt asensin uudestaan. Noh, näillä mennään. Tarkistin vielä testillä, mikä versio Djangosta. Ei näyttänyt siltä, että olisi tullut versiopäivitystä yön aikana.

![Näyttökuva 2024-09-30 214705](https://github.com/user-attachments/assets/da45e44c-36f3-4fc6-9852-be15b4d28177)

![Näyttökuva 2024-09-30 214926](https://github.com/user-attachments/assets/04d6db75-d570-401d-9436-bb2549fa4527)

Tämän jälkeen aloitin uuden projektin. Jouduin antamaan sille uuden nimen, sillä olin jo aiemmin tehnyt aleksco-nimisen projektin. Tämä sai siis nimekseen alekspro.

![Näyttökuva 2024-09-30 215204](https://github.com/user-attachments/assets/e14d2ea5-bb80-491c-8796-9e058ae709ff)

Tässä vaiheessa pidin hetken levähdystauon. Olin istunut tietokoneen äärellä tauotta klo 17.40 saakka, ja kello oli nyt 21.54. Menin keittämään kupillisen teetä. Palasin projektin pariin klo 22.00

Seuraavana vuorossa oli yhdistää python Apacheen käyttäen mod_wsgi:tä. En ollut varma, saiko virtuaaliympäristössä käyttää sudoa, joten deaktivoin ympäristön **deactivate** komennolla, ja vasta sitten aloin muokkaamaan virtual host-tiedostoa. Kopioin ohjeet Teron sivuilta, kuten hän suositteli tekemään, jotta välttyy kirjoitusvirheiltä.

![Näyttökuva 2024-09-30 221258](https://github.com/user-attachments/assets/421a521d-ffbf-48c6-9607-9c5a84a5f40b)

![Näyttökuva 2024-09-30 222203](https://github.com/user-attachments/assets/10f90c67-7a72-4668-8514-435d55421f4b)

CTRL+S ja CTRL+Q, jonka jälkeen palasin virtuaaliympäristöön. Sitten asensin WSGI-moduulin Apacheen, käyttämällä komentoa **sudo apt-get -y install libapache2-mod-wsgi-py3** toki tämän tein ja tajusin, että olin jälleen virtuaaliympäristössä, ja käytin sudoa. Teinkö nyt väärin? Joudunko tekemään uudelleen WSGI-määritykset virtual host-confiin? Se varmaan selviää pian...

![Näyttökuva 2024-09-30 222637](https://github.com/user-attachments/assets/4595879e-1e09-44c3-86d6-7883ad71af4c)

Tarkistin syntaksin **/sbin/apache2ctl configtest**, ja näytti SYNTAX OK. Sitten käynnistin Apachen uudestaan **sudo systemctl restart apache2**

![Näyttökuva 2024-09-30 223118](https://github.com/user-attachments/assets/8563cb79-e759-46ce-9f30-dabd17a52e9b)

Ohjeiden mukaisesti kävin curl-komennolla tarkistamassa, toimiiko Djangon avaruuskiituri tällä kertaa. Ainakin komentorivillä näytti toimivan, sitten vielä tarkistin selaimella.

![Näyttökuva 2024-09-30 224222](https://github.com/user-attachments/assets/e84b3ff2-1d57-410c-9976-0e6b8fef7808)

Selaimella sain kuitenkin seuraavan virheen:

![Näyttökuva 2024-09-30 224646](https://github.com/user-attachments/assets/2b385896-7666-4e35-bf0d-adb8c63dd61b)

Luin virheilmoitusta läpi, enkä oikein tajunnut missä vika. Kysyin ChatGPT:ltä vastausta, ja se sanoi seuraavaa: *Avaa Django-projektisi asetustiedosto: Tämä tiedosto sijaitsee yleensä settings.py-nimisessä tiedostossa, joka on projektisi juurihakemistossa.*
*Lisää ALLOWED_HOSTS-asetukseen 127.0.1.1: Etsi rivi, joka alkaa ALLOWED_HOSTS.*

Tämän lisäksi virheilmoituksen aivan lopussa luki näin: *You’re seeing this error because you have DEBUG = True in your Django settings file. Change that to False, and Django will display a standard page generated by the handler for this status code.* 

Lähdin tekemään muutoksia, eli laittamaan DEBUGIN pois päältä ja lisäämään hostin.

![Näyttökuva 2024-09-30 225840](https://github.com/user-attachments/assets/c4ac3bbd-ec44-47ba-8d09-881b7c4b0d10)

Tältä näytti settings.py-tiedostossa, kun sinne menin.

![Näyttökuva 2024-09-30 230050](https://github.com/user-attachments/assets/547d9f44-fe53-45e2-a722-e4c37c017bb5)

Ja muokkasin sitä näin.

![Näyttökuva 2024-09-30 230255](https://github.com/user-attachments/assets/14c1d379-c8f8-4b62-9d16-9b738b84f203)

Kokeilin vielä curlia **curl -sI localhost|grep Server** ja **curl -s localhost|grep title**
vastauksena ohjeiden mukaisesti.

![Näyttökuva 2024-09-30 230530](https://github.com/user-attachments/assets/8afde59d-4366-46c6-b791-f10902b7cbc4)

![Näyttökuva 2024-09-30 230854](https://github.com/user-attachments/assets/1505862c-add6-4961-ba48-ff2ba845f81a)

Tein vielä uudelleen seuraavat komennot:

![Näyttökuva 2024-09-30 231135](https://github.com/user-attachments/assets/542e035b-eb52-4e90-a1cf-6561f6b320ca)

ja kävin nyt tarkistamassa selaimella localhostin. Minua jäi nimittäin aiemmin häiritsemään configtest-pyynnön ilmoitus osoitteesta 127.0.1.1. ja se sai aikaan tuon ylhäällä olleen virheilmoituksen, eikä localhost eli 127.0.0.1. antanut kuin Forbidden-erroria. 

Kävin tarkistamassa siis nuo osoitteet. 
127.0.1.1. antoi tämän:

![Näyttökuva 2024-09-30 231504](https://github.com/user-attachments/assets/9e1cb18a-5088-4d34-88a0-3b7d55532ac0)

ja localhost tämän:

![Näyttökuva 2024-09-30 231600](https://github.com/user-attachments/assets/ae6f244b-0121-4cfb-8213-906dcf1d7950)

Tiedostossa kuitenkin näkyy, että localhost olisi tunnetuissa hosteissa... kävin tarkistamassa vielä manage.py sekä settings.py tiedostoja, olisko siellä ollut virheitä. Ei näyttänyt olevan, mutta vaihdoin DEBUG=True, jonka jälkeen tallensin ja käynnistin Apachen uudelleen. Nyt Django taas toimi.

![Näyttökuva 2024-09-30 233019](https://github.com/user-attachments/assets/6a132db9-5769-46a3-8232-521486679f95)

Sitten menin uudestaan järjestyksessä Teron ohjeiden mukaan, nyt toivoen, että toimisi.

![Näyttökuva 2024-09-30 233512](https://github.com/user-attachments/assets/4d3622e7-f41c-460e-be4d-c5c7f5c5741d)

![Näyttökuva 2024-09-30 233654](https://github.com/user-attachments/assets/ad48b92d-2ca0-41fb-a44f-36d7c6b05285)

Kokeilin uudestaa curlia, kuten ohjeissa sanottiin eli **curl -s localhost|grep title**. 

![Näyttökuva 2024-09-30 233831](https://github.com/user-attachments/assets/8d4c2935-7b44-4c76-a375-3b1d796dc628)

<title>Not Found</title>, kuten ohjeissa. Eli saatoin sittenki aiemmin tehdä asiat aivan oikein, mutta paniikki ja ahdistus iskivät, enkä ollut riittävän tarkkana ohjeiden seuraamisessa. Tästä oppineena etenin vaihe vaiheelta eteenpäin.

![Näyttökuva 2024-09-30 234047](https://github.com/user-attachments/assets/9d473ad1-f9d8-44c4-ac15-8e1ff1fb8b69)

![Näyttökuva 2024-09-30 234104](https://github.com/user-attachments/assets/382b45cc-44f3-4f2f-8997-0fea22af4479)

Eli nyt localhost ei toimi, kuten kuuluukin olla, mutta /admin sivulla tulee edes jotain näkyviin.
Menin takasin settings.py tiedstoon, lisäämään hieman asiaa.

![Näyttökuva 2024-09-30 234637](https://github.com/user-attachments/assets/ab79043c-fa93-4075-9b84-e7d6515df93f)

![Näyttökuva 2024-09-30 234621](https://github.com/user-attachments/assets/0147b2ee-5d70-4c47-ae63-8bbc102ad5a0)

Sitten ajettiin **./manage.py collectstatic** eli kerätään kaikki staattiset tiedostot talteen.
Kävin tämän jälkeen tarkistamassa Firefoxissa, toimiiko localhost/admin, ja nyt näytti toimivan!

![Näyttökuva 2024-09-30 235028](https://github.com/user-attachments/assets/46a9256a-d485-4fb9-9fe0-d50835b9d109)

Eli nyt olisi Djangon tuotantoympäristö toiminnassa.

Sain tehtävän valmiiksi 30.9.2024 klo 23.52. 
Eli kokonaisaika joka meni tämän viikon tehtävään oli 7,5 tuntia.

Kunniamaininta  kaverilleni Liisalle, jonka raportista sain apua, ja jota ilman en varmastikaan olisi selvinnyt tämän viikon tehtävästä. 

## Lähteet

Karvinen, T. 20222. Deploy Django 4 – Production Install. Saatavissa: https://terokarvinen.com/2022/deploy-django/. Luettu 30.9.2024.

Karvinen, T. 2022.  Django 4 Instant Customer Database Tutorial. Saatavissa: https://terokarvinen.com/2022/django-instant-crm-tutorial/. Luettu 29.9.2024.

Karvinen, T. 2024. Linux Palvelimet 2024 alkusyksy. Saatavissa: https://terokarvinen.com/linux-palvelimet/. Luettu 29.9.2024.

Lesonen, L. 2023. h6. Saatavissa: https://github.com/LiisaLesonen/linux-palvelimet/blob/main/h6.md. Luettu 29.9.2024. 
