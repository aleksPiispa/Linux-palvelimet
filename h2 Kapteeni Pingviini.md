Tämä, ja kaikki tulevat tehtävät pohjautuvat Tero Karvisen Linux palvelimet kurssin tehtävänantoihin. 
Suoritan kurssia alkasyksyllä 2024.

Teen kurssin tehtäviä Lenovon Ideapad 5 Pro 13ARH7 -kannettavalla. Käyttöjärjestelmänä koneessa on Windows 11 Home,
ja koneessa on 16GB RAM-muistia sekä suorittimena AMD Ryzen 5 6600HS Creator Edition.
Näytönohjain: AMD Radeon 660M Graphics. Storage: M.2 SSD 512Gt, vapaana 343Gt.

Aloitin tämän tehtävän tekemisen 1.9.2024 klo 16.15-17 ja jatkoin tehtävien tekoa klo TBD

# h2 Komentaja Pingviini

## x) Command line basics revisited

Linuxin komentorivi käyttää monia komentoja, jotka olivat olemassa jo aikana ennen Linuxia. Komennot ovat kestäneet hyvin aikaa,
sillä niiden avulla työskentely on nopeaa. Tärkeimpiä komentoja, jotka olisi hyvä opetella ulkoa:

pwd = "print working directory" eli tulosta nykyisen työhakemiston sijainti
mkdir "nimi" = luo uusi hakemisto eli kansio
ls = listaa hakemiston sisältö, eli tiedostot sekä alihakemistot
cd .. = liiku ylöspäin hakemistossa
cd "hakemiston nimi" = liiku haluttuun hakemistoon
nano FOO.txt = avataan nano-tekstieditori ja avataan tai luodaan siellä tiedosto nimeltään FOO.txt
less teksti.txt = näytä sivu kerrallaan tiedostosta, sivuja voi vaihtaa b = edellinen sivu ja välilyönti = seuraava sivu
man ls = listaa ohjeita

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







