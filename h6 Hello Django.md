Tämä, ja kaikki tulevat tehtävät pohjautuvat Tero Karvisen Linux palvelimet kurssin tehtävänantoihin. Suoritan kurssia alkasyksyllä 2024. 
Teen kurssin tehtäviä Lenovon Ideapad 5 Pro 13ARH7 -kannettavalla. Käyttöjärjestelmänä koneessa on Windows 11 Home, ja koneessa on 16GB RAM-muistia
sekä suorittimena AMD Ryzen 5 6600HS Creator Edition. 
Näytönohjain: AMD Radeon 660M Graphics. Storage: M.2 SSD 512Gt, vapaana 343Gt.
Koneelle on asennettu VirtualBox virtualisointiohjelma, joka pyörittää tehtävissä näkyvää Linux Debian-virtuaalikonetta.

# h6 Hello Django

a) Tee yksinkertainen esimerkkiohjelma Djangolla.

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

Avaruuskiituri lähti liikkeelle, seuraavaksi Tatoiinen kiiturikisaan siis :D

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




