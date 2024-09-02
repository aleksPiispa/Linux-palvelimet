Tämä, ja kaikki tulevat tehtävät pohjautuvat Tero Karvisen Linux palvelimet kurssin tehtävänantoihin. 
Suoritan kurssia alkasyksyllä 2024.

Teen kurssin tehtäviä Lenovon Ideapad 5 Pro 13ARH7 -kannettavalla. Käyttöjärjestelmänä koneessa on Windows 11 Home,
ja koneessa on 16GB RAM-muistia sekä suorittimena AMD Ryzen 5 6600HS Creator Edition.
Näytönohjain: AMD Radeon 660M Graphics. Storage: M.2 SSD 512Gt, vapaana 343Gt.

Aloitin tämän tehtävän tekemisen 1.9.2024 klo 16.15-17 ja jatkoin klo 20.30-22.30. Tein loput harjoitukset ja raportoinnin loppuun 2.9.2024 klo 13.15-14.30.

# h2 Komentaja Pingviini

## x) Command line basics revisited

Linuxin komentorivi käyttää monia komentoja, jotka olivat olemassa jo aikana ennen Linuxia ja internetiä. Komennot ovat kestäneet hyvin aikaa,
sillä niiden avulla työskentely on tänäkin päivänä nopeaa. Tärkeimpiä komentoja, jotka olisi hyvä opetella ulkoa:

- pwd = "print working directory" eli tulosta nykyisen työhakemiston sijainti
- mkdir "nimi" = luo uusi hakemisto eli kansio
- ls = listaa hakemiston sisältö, eli tiedostot sekä alihakemistot
- cd .. = liiku ylöspäin hakemistossa
- cd "hakemiston nimi" = liiku haluttuun hakemistoon
- nano FOO.txt = avataan nano-tekstieditori ja avataan tai luodaan siellä tiedosto nimeltään FOO.txt
- less teksti.txt = näytä sivu kerrallaan tiedostosta, sivuja voi vaihtaa b = edellinen sivu ja välilyönti = seuraava sivu
- man ls = listaa ohjeita

(Karvinen, 2020)

Sivulla oli listattu myös todella paljon muitakin komentoja, mutta kävin läpi vain murto osan. Vaikka komentoja 
tuntuu olevan hirvittävä määrä, eikä kaikkea tunnu muistavan, niin ne oppii varmasti parhaiten harjoittelemalla niitä
käytännön tasolla. 

## a) Micro. Asenna Micro-editori

Ensimmäinen oikea tehtävä tämän viikon tehtävistä, oli asentaa Micro-tekstieditori. Asensin Micron
terminaalissa komennolla "sudo apt-get install micro". Komennon syötettyäni tajusin, että olisin voinut ennen 
asennusta kuitenkin päivittää järjestelmän, joten ajoin komennon "sudo apt-get update". Huomasin päivityksen myötä, että 
käyttöjärjestelmän versio vaihtui Debianin uuteen versioon 12.7. Tein vielä varmuuden vuoksi uudelleen komennon asentaa
micro, ja sain ilmoituksen, että microsta on olemassa jo uusin versio.  Eli vaikka teinkin asennuksen ennen päivitystä, ei siitä
vaikuttanut olevan haittaa.

![Näyttökuva 2024-09-01 165139](https://github.com/user-attachments/assets/49bbd77f-5124-4ba9-93ff-58db0aaa5f20)

![Näyttökuva 2024-09-01 165315](https://github.com/user-attachments/assets/c76fd24d-9cc1-47f4-8cec-486c6005e61a)

![Näyttökuva 2024-09-01 165406](https://github.com/user-attachments/assets/efba7890-1ca8-44bc-88ca-d9a290c65ba3)

## b) Apt. Uusien komentoriviohjelmien asentaminen

Seuraavaksi tehtävänäni oli asentaa terminaalia käyttäen itselleni komentoriviohjelmia. En ennestään tiennyt nimeltä yhtään tällaista, joten jouduin etsimään tietoa Googlesta.
Löysin monia mielenkiintoisia ohjelmia, mutta päädyin seuraaviin, sillä ne eivät tarvinneet useita esiasennuksia muista ohjelmista, jotta ne toimisivat. Asensin ohjelmat: Httpie, Asciinema sekä Hexyl. 

![Näyttökuva 2024-09-01 205431](https://github.com/user-attachments/assets/a79d8f05-5f0b-4729-9dbd-20801a99483b)

Löysin Asciineman asentamiseen ja käyttöön ohjeet täältä: https://docs.asciinema.org/getting-started/#__tabbed_1_2
Asciinema on siis ohjelma, jolla voin tallentaa ja toistaa terminaalissa antamiani komentoja. Se ei ainoastaan tallenna komentoja vaan nauhoittaa ne, oli se toistaa nauhoitusta yhtä kauan kuin sitä tein. Aika siistiä!

![Näyttökuva 2024-09-01 211931](https://github.com/user-attachments/assets/18a1b4f9-e5b5-4ce4-8676-bb3cefc00d0a)

Hexyl on ohjelma, joka jolla voi tutkia hexa-merkkejä ja se näyttää eri värein eri bittejä (en ole aivan satavarma, mihin tätä käyttää, mutta se tuli minulle vastaan kun etsin asennettavia ohjelmia...) (https://github.com/sharkdp/hexyl)

![Näyttökuva 2024-09-01 212252](https://github.com/user-attachments/assets/f26874f5-ae71-4a44-a18b-172bb87b0b6c)

Httpie on Open Source ohjelma, jolla kehittäjät voivat testata APIen toimivuutta. Ohjelmaa voi varmasti käyttää muuhunkin, mutta tämän verran siitä sain asiaa irti. (https://httpie.io/)

![Näyttökuva 2024-09-01 213104](https://github.com/user-attachments/assets/e66bd8b4-0af3-4d7a-a7a1-7d991083d052)

Yritin asentaa kaikkia kolmea ohjelmaa komennolla "sudo apt-get install hexyl asciinema httpie", mutta jostain syystä tämä ei toiminut. Päädyin asentamaan kaikki yksitellen. 

## c) FHS

Tässä tehtävässä kävin läpi Tero Karvisen Command Line Basics Revisited-sivun Important directories-osuudessa mainittuja kansioita esimerkein.

/root directory eli juurihakemisto

![Näyttökuva 2024-09-01 214358](https://github.com/user-attachments/assets/c5018f49-e2a1-46f1-848b-b7489bbda667)

/home/ eli kotihakemisto

![Näyttökuva 2024-09-01 214652](https://github.com/user-attachments/assets/bc564f68-44af-457b-80c1-b4d361dbeae4)

/home/aleksp/ = käyttäjän aleksp eli allekirjoittaneen kotihakemisto. Sieltä löytyy aiemmin nanolla luomani FOOBAR.txt tiedosto sekä luomani kansio linuxkurssi.

![Näyttökuva 2024-09-01 214938](https://github.com/user-attachments/assets/975d82b1-5944-4255-aa0a-0f8eac90a429)

/etc/ eli järjestelmäasetukset

![Näyttökuva 2024-09-01 215510](https://github.com/user-attachments/assets/b2a5d5c2-3cf9-435f-b4fc-b143823ed343)
![Näyttökuva 2024-09-01 215720](https://github.com/user-attachments/assets/8ffed2b0-0c83-4f7d-8915-12fe957a8ecf)

En saanut kuvankaappauksella koko komennon listaamaa hakua näkyviin. Siksi laitoin kaksi kuvaa tästä.

/media/ = Jos koneellani olisi esimerkiksi ulkoisia kovalevyjä, ne olisivat täällä

![Näyttökuva 2024-09-01 215954](https://github.com/user-attachments/assets/8d0b775a-adc9-42e2-b6bb-f15b27e2c95b)

/var/log/ = Täältä löytyy järjestelmän lokitietoja

![Näyttökuva 2024-09-01 220400](https://github.com/user-attachments/assets/0a9e4cff-feae-485a-b1dd-381c91aa076a)

## d) The Friendly M

Tässä tehtävässä tuli käyttää grep-komentoa sekä näyttää esimerkkejä sen käytöstä.
Grep on tehokas työkalu, jonka avulla voidaan etsiä tiettyjä sanoja tai merkkijonoja tiedostoista. 
Grep tulee sanoista "search **g**lobally for a **r**egular **e**xpression and **p**rint".

(Ikonen, Hynninen, Vanhala, 2015)

Loin tätä tehtävää varten muutaman tiedoston, joita etsin terminaalista käyttäen grep-komentoa. En törmännyt virheisiin, joten vaikutti toimivan kuten pitikin.

![Näyttökuva 2024-09-02 133703](https://github.com/user-attachments/assets/7b90e6b8-9f54-46a4-a5a1-c5f135871567)

## e) Pipe

Pipe eli putki, terminaalissa "|" merkki. Sen avulla on mahdollista yhdistää kaksi tai useampi komento samaan lausekkeeseen. Kokeilin putkea jo edellisessä esimerkissä, mutta tässä vielä lisää. Käytin putkea listaamaan tekstitiedostoja.

![Näyttökuva 2024-09-02 134108](https://github.com/user-attachments/assets/056d2bb5-0124-4e91-9507-3c190dc5ba77)

## f) Rauta

Tehtävänä oli ajaa terminaalissa komento "sudo lshw -short -sanitize". Ensialkuun asensin lshw:n komennolla "sudo apt-get install lshw" ja päivitin "sudo apt-get update".
Tämän jälkeen ajoin komennon "sudo lshw -short -sanitize", lshw tulee sanoista list hardware.
Tulosteena tuli listaus virtuaalikoneeni osista (mitä siihen asentaessa tuli) ja niiden yksityiskohtaisemmista tiedoista. Esimerkiksi siinä näkyi, kuinka paljon muistia koneelle on määritetty (4Gb) ja mitä prosessoria virtuaalikoneeni käyttää (AMD Ryzen 5). 

![Näyttökuva 2024-09-02 134657](https://github.com/user-attachments/assets/325fd05d-98d5-4f55-9a45-2fc0a8e85c2a)


Minulla meni tämän viikon tehtävien tekoon aikaa noin 4 tuntia. Tein tehtävän pätkissä, silloin kun minun oli mahdollisuus päästä koneen ääreen. Oli äärimmäisen helppoa jatkaa raportin tekoa GitHubissa, kun siihen palasi ja näki senhetkisen tilan. Tällä kertaa minulla ei myöskään mennyt läheskään yhtä kauan GH:n opetteluun, kuin edellisen viikon tehtävässä. 


## Lähteet

Ikonen, A. Hynninen, T. Vanhala, E. 2015. Terminaali tutuksi - Linux ja komentorivin hallinta. Luettavissa: https://lutpub.lut.fi/bitstream/handle/10024/104311/Linux-opas.pdf?sequence=2. Luettu 2.9.2024.

Karvinen, T. 2024. Linux palvelimet 2024 alkusyksy. Luettavissa. https://terokarvinen.com/linux-palvelimet/. Luettu 1.9.2024.

Karvinen, T. 2020. Command Line Basics Revisited. Luettavissa. https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited. Luettu 1.9.2024.

Kulik, M. 2023. Asciinema Getting started. Luettavissa. https://docs.asciinema.org/getting-started/#__tabbed_1_2. Luettu. 1.9.2024.

Lesonen L. 2023. h2 Kapteeeni Pingviini. Luettavissa. https://github.com/LiisaLesonen/linux-palvelimet/blob/main/h2.md. Luettu. 1.9.2024.

LinuxLinks.com n.d. Luettavissa. https://www.linuxlinks.com/100-great-must-have-cli-linux-applications/. Luettu 1.9.2024.











