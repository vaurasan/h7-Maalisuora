# h7 Maalisuora

#### Oma Host kokoonpanoni:

| Komponentti | Kuvaus | Lisätiedot |
| :---        |    :----:   |          ---: |
| Emolevy | MSI B550-A PRO | ATX, AM4 |
| Prosessori   | AMD Ryzen 9 5900X | 12-Core 3.70 GHz |
| RAM   | G.Skill  Ripjaws V |  32GB (4x8GB) DDR4 3600MHz, CL 16, 1.3  |
| Näytönohjain   | Sapphire PULSE AMD Radeon RX 7900 GRE        | 16GB     |
| Kovalevy   | Kingston 1TB        | A2000 NVMe PCIe SSD M.2      |
| Kovalevy   | Crucial 512GB        | MX100 SSD     |
| Kovalevy   | Crucial 256GB        | MX100 SSD     |
| Virtalähde   | Asus 750W TUF Gaming Gold        | ATX 80 Plus      |
| Kotelo   | Phanteks Enthoo Pro       |  Full Tower      |

Käyttöjärjestelmä: Windows 11 Pro 23H2

#### Virtuaalikone
Oracle VirtualBox 7 - Debian 12 GNU/Linux bookworm<br>
6 Prosessoriydintä - 4GB RAM-muistia - 60GB tallennustilaa

## a)

#### Kirjoita ja aja "Hei maailma" kolmella kielellä

Ohjelmointitaidot ovat kohtalaisen ruosteessa, joten käytän röyhkeästi apuna Karvisen [Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04 ohjetta](https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/)

*3.10.2024 klo 13:01*

### Python

Pikaisen vilkaisun jälkeen otan ensimmäisenä käsittelyyn vanhan kunnon Pythonin. Luon python tiedoston ``micro hello.py``. Kirjoitan tiedostoon: print("Heippa muailma") ja tallennan ``ctrl+s´´

Sitten ajetaan tiedosto ``python3 hello.py``

![heipyytton](https://github.com/user-attachments/assets/25690c00-06c7-4ca7-88cd-03ed3bb02727)

### Go

Seuraavana tuo Go vaikuttaisi järkevältä. Täytyy ensin asentaa golang-go komennolla ``sudo apt-get -y install golang-go``, hetken rullauksen jälkeen ohjelma on asennettu.

Kokeilen luoda go-tiedoston ``micro heippis.go``, tiedostoon kirjoitan:

![goheipatteksti](https://github.com/user-attachments/assets/330beac3-a5a8-489e-b489-3c44eba11eec)

Kokeilen luoda "hei.go" tiedostoa tuon pohjalta komennolla ``go build -o heippis.go hei.go``, mutta ei onnistu. Veikkaan että johtuu alkuperäisen tiedoston nimestä ".go"-päätteellä kokeilen muuttaa "heippis.go" tiedoston --> "heippis"

``mv heippis.go heippis``. Huomaan että olen tehnyt nämä suoraan /home/santeri kansioon, tämä ei vetele, joten teen "code/" kansion minne siirrän nämä. ``mkdir code``, ei sentään c0de, eikä myöskään sammy, ``mv heippis code/ mv hello.py code/``, ihme herjoja tuli, mutta tiedostot siirtyivät /code kansioon

![codekansio](https://github.com/user-attachments/assets/1d60eaea-cd24-483d-9e7c-95b75cccfdb8)

*Älkööt välittäkö teroco/ kansiosta, nothing to see here.* Ei pysty vieläkään käyttämään komentoa ``go build -o heippis heippis.go``, otetaanpa manuaali esille https://go.dev/doc/tutorial/getting-started#call.

Nyt kokeilen suoraan raa'asti ohjeen mukaan ``go mod init example/hello``

![gomodhel](https://github.com/user-attachments/assets/cba4a681-2ff6-41f2-abe4-caa0dcb2dc10)

Teen "heippis":stä takaisin "heippis.go" tiedoston ``mv heippis heippis.go`` ja avaan sen microlla ``micro heippis.go``

![taasgokoodi](https://github.com/user-attachments/assets/2270abb7-9617-4ae4-a465-a6daba297e1b)

Taas tämä sama, eli

- ensimmäisenä määritellään main paketti, paketti on ryhmä funktioita
- tuodaan suosittu ftm paketti joka sisältää functioita joilla alustetaan tekstiä, kuten tulostetaan tekstiä konsoliin
- käytetään main funktiota tulostamaan viesti konsoliin, main funktio suoritetaan oletuksena kun suoritetaan main paketti

Ohjeen mukaan ajoin seuraavaksi ``go mod tidy``, tästä en ole varma oliko pakollinen vaihe. Seuraavaksi komennolla ``go run .`` sain ajettua tuon koodin oikein.

![gotoimii](https://github.com/user-attachments/assets/ee7c2c0a-475b-4b0b-a289-21a799756815)

### C

Tästäkään kielestä ei ole kokemusta, paitsi C# alkeita on joskus tullut opeteltua, joten ainakin Karvisen ohje on paikallaan. Katson syventäviä ohjeita vielä täältä: https://www.scaler.com/topics/c/how-to-compile-c-program-in-linux/

``micro heitaas.c``, luon uuden c tiedoston, jonne kirjoitan:

![ctiedosto](https://github.com/user-attachments/assets/e49bdea7-6b98-4795-9e72-c78d414f16b4)

Täytyy vielä laatia .c-tiedostosta ohjelma ``gcc heitaas.c -o heitaasc``, nyt ohjelmaa voidaan ajaa komennolla ``./heitaasc``

![cworks](https://github.com/user-attachments/assets/06476fd2-6dfb-4ae6-bdc4-a5ed11f300c5)

*klo 13:40, 39min kaikkineen*

## b)

#### Laita Linuxiin uusi komento niin, että kaikki käyttäjät voivat ajaa sitä

Luen alkuun [Karvisen ohjeita aiheesta](https://terokarvinen.com/2007/12/04/shell-scripting-4/), vaikka tämä käytiin jo tunnilla läpi ja tein muistiinpanoja

Olipa lyhyt ohje, homma tuli selväksi, mutta yritän löytää pidemmän tekstin jossa selitetään hieman teoriaa taustalla, kuten tämä https://www.geeksforgeeks.org/shell-scripting-define-bin-bash/

*klo 13:56*

Eipä siihen sen enempää kaiketi ohjeita tarvita. Luon code/ kansioon uuden tiedoston ``micro kukamita.sh`` ja kirjoitan seuraavaa:

![binbashteksti](https://github.com/user-attachments/assets/8c3145dc-add8-4f7a-9d58-d7e87123fde9)

Annan kaikille oikeudet suorittaa tiedosto komennolla ``chmod a+x kukamita.sh``, jonka jälkeen suoritetaan tiedosto komennolla ``bash kukamita.sh``

![bashworksyes](https://github.com/user-attachments/assets/1f4a9956-25f7-4993-bc55-90077086dea2)

*klo 13:59*

## c)

#### Ratkaise vanha arvioitava laboratorioharjoitus soveltuvin osin

Etsin sopivan laboratorioharjoituksen hakukentästä "lab" haulla

![labhaku](https://github.com/user-attachments/assets/45dd2e30-a403-4555-8d1b-ff6d3723d568)

Alimpana tuolla haulla löytyi järkevän oloinen [Final Lab for Linux Palvelimet 2024 Spring](https://terokarvinen.com/2024/arvioitava-laboratorioharjoitus-2024-linux-palvelimet/?fromSearch=lab) labraharjoitus

Aloitan laboratorioharjoituksen d) kohdasta, sillä a-c on oikeaan koetilanteeseen tarkoitettuja asioita. Kirjoitan jonkun verran yksityiskohtaista raporttia, tai ainakin otan kuvia, vaikka tuon laboratorioharjoituksen tehtävänannossa sanotaan, että lähinnä testitulokset riittää

Tietenkin vielä täytyy asentaa täysin uusi virtuaalikone tätä tehtävää varten, joten siinä menee hetki. Tein tämän jo kertaalleen hiljattain, joten pitäisi olla hyvässä muistissa asia, siitä en raportoi kuitenkaan, ellei tule mutkia matkaan. Laitan tällä kertaa virtuaalikoneeseen 6 ydintä ja 8GB muistia, koska niitä riittää

### - d) 'howdy'

#### - Tee kaikkien käyttäjien käyttöön komento 'howdy'
#### - Tulosta haluamaasi ajankohtaista tietoa, esim päivämäärä, koneen osoite tms
#### - Pelkkä "hei maailma" ei riitä
#### - Komennon tulee toimia kaikilla käyttäjillä työhakemistosta riippumatta

*14:32*

Loin howdy.sh ``micro howdy.sh`` ja sinne

![bashsisaltaa](https://github.com/user-attachments/assets/23589740-b5fd-4c97-92ea-4c0867977b3f)

![bashajettu](https://github.com/user-attachments/assets/fba4a4be-309b-4b15-a36a-3efc90353501)

*klo 14:39*

### - e) Etusivu uusiksi

#### - Asenna Apache-weppipalvelin
#### - Tee yrityksellemme "AI Kakone" kotisivu
#### - Kotisivu tulee näkyä koneesi IP-osoitteella suoraan etusivulla
#### - Sivua pitää päästä muokkaamaan normaalin käyttäjän oikeuksin (ilman sudoa). Liitä raporttiisi listaus tarvittavien tiedostojen ja kansioiden oikeuksista.

Laitoin oikeudet ``chmod -R 750 /var/www`` ja ``sudo chown -R santeri:santeri /var/www``

![varjateeapache](https://github.com/user-attachments/assets/8d1a159f-6678-4194-9c3c-aef9d4029167)

![htmlkakone](https://github.com/user-attachments/assets/4dcd070f-c63a-4902-9cee-2d1acecc307b)

![conffikakone](https://github.com/user-attachments/assets/1f821e59-d44c-453d-96b5-b9b230146307)

![sivukakone](https://github.com/user-attachments/assets/ae1c7703-a8d2-474d-8bbf-ada5e529e60c)

### - g) Salattua hallintaa  127.0.0.1

#### - Asenna ssh-palvelin
#### - Tee uusi käyttäjä omalla nimelläsi, esim. minä tekisin "Tero Karvinen test", login name: "terote01"
#### - Automatisoi ssh-kirjautuminen julkisen avaimen menetelmällä, niin että et tarvitse salasanoja, kun kirjaudut sisään. Voit käyttää kirjautumiseen localhost-osoitetta

Katsoin ohjeita täältä: https://terokarvinen.com/2008/03/10/ssh-public-key-authentication-2/?fromSearch=ssh

``sudo apt-get install ssh``

![ekasanterite](https://github.com/user-attachments/assets/28e04a32-5bdb-4a0d-903d-9e5a05e227df)

``cd /home/santerite01/.ssh``

``ssh-keygen -t dsa``

![keygentsa](https://github.com/user-attachments/assets/a6bb5260-e7c6-4615-ac72-471ef5ef6639)

![keygen-tehty](https://github.com/user-attachments/assets/47c03bfa-ae93-4101-904e-724bce626792)

### - h) Djangon lahjat
#### - Asenna omalle käyttäjällesi Django-kehitysympäristö
#### - Tee tietokantaan lista tekoälyistämme, jossa on nämä ominaisuudet
#### - Kirjautuminen salasanalla
#### - Tietokannan muokkaus wepissä Djangon omalla ylläpitoliittymällä (Django admin)
#### - Käyttäjä Erkille, jossa ei ole ylläpito-oikeuksia
#### - Taulu Assistants, jossa jokaisella tietueella on nimi (name)
#### - Jos haluat, voit lisäksi bonuksena laittaa mukaan kentän koko (size)

Lähden tekemään tätä ohjetta soveltaen https://terokarvinen.com/2022/django-instant-crm-tutorial/

Tämmöistä sain tehtyä, en ole täysin varma oliko tässä kaikki mitä haettiin, lukuunottamatta "size"-kenttää

![jankko1](https://github.com/user-attachments/assets/6b6d9cc8-9ac4-4767-994f-776d9d8d050d)

---

![erkki](https://github.com/user-attachments/assets/19cf97ed-9e94-48b9-bdcf-b93299df4fcf)


---

![assyt](https://github.com/user-attachments/assets/6f08f956-9b4b-4215-828b-04752e7e84f8)

### - h) Tuotantopropelli

#### - Jos olet tässä kohdassa, olet kyllä työskennellyt todella nopeasti (tai sitten teet tätä tehtävää huviksesi kurssin jälkeen). Mutta älä huoli, tässä haastetta, jotta et joudu pyörittelemään peukaloita.
#### - Tee tuotantotyyppinen asennus Djangosta
#### - Laita Django-lahjatietokanta tuotantotyyppiseen asennukseen
#### - Voit vaihtaa tämän sivun näkymään etusivulla staattisen sivun sijasta

Tämä ohje on kovassa käytössä tätä tehtäessä https://terokarvinen.com/2022/deploy-django/

![lahjatietokanta](https://github.com/user-attachments/assets/8d38393e-6335-4bad-b842-d966f6323be9)

Kuvassa näkyy lahjatietokanta apachen pyörittämänä admin-näkymässä, viimeinen kohta tehtävästä jäi tekemättä

## d)

#### Asenna itsellesi tyhjä virtuaalikone arvioitavaa labraa varten. Suosittelen Debian 12-Bookworm amd64, riittävästi RAM ja kovalevyä. Koneella saa olla päivitetyt ohjelmistot (apt-get dist-upgrade) ja tulimuuri. Koneella ei saa olla mitään muita demoneja tai ohjelmia asennettuna kuin nuo ja asennuksen mukana tulevat. Virtuaalikoneella ei saa olla luottamuksellisia tiedostoja, koska opettaja saattaa tarkastella sitä

Tähän ohjeet alkavat olemaan jo päässä aika hyvin, mutta ohjeet asennukseen löytyvät täältä: https://terokarvinen.com/2021/install-debian-on-virtualbox/

![asen1](https://github.com/user-attachments/assets/d6aa390b-f1da-4606-9c08-03a395982e58)

---

Annetaan reilusti vääntöä koneelle niin jää enemmän aikaa ongelmanratkaisuun

![hardware](https://github.com/user-attachments/assets/0d83a37f-6987-45b7-92f6-92e07eff24a5)

---

60GB tallennustilaa riittänee enemmän kuin hyvin

![harddisk](https://github.com/user-attachments/assets/e7fbee20-4458-4689-bd43-df74518bbb70)

---

Nyt VirtualBoxissa näkyy juuri luotu LabRat, käynnistetään se tuplaklikkaamalla ja valitaan Boot menusta ylin vaihtoehto ``Live system (amd64)``

![kaynnistus](https://github.com/user-attachments/assets/152e247e-975e-469f-bccb-ab429047c248)

---



### Itse asennukseen

Työpöydältä tuplaklikataan ``Install Debian`` kuvaketta ja painetaan ``Launch Anyway``

---

![welcome](https://github.com/user-attachments/assets/61ffb99b-5523-4f27-8846-09d83d51ce1f)

Käytettävyyden vuoksi kannattaa käyttää seuraavia asetuksia:

- **Welcome** American English
- **Location** Region - Europe, Zone - Helsinki
- **Keyboard** Finnish - Default
- **Partitions** Erase disk
- **Users** Oma nimi, käyttäjänimi, tietokoneen nimi (tähän jotain ympäripyöreää mielellään, saattaa näkyä internetiin)

---

![asentuu](https://github.com/user-attachments/assets/f81a9203-b19b-4797-b0a6-5528b87803de)

Nyt on Debian asentumassa virtuaalikoneelle, joka kerta minulla on ollut sama ongelma noiden painikkeiden kanssa, tuossa kuvassa näkyy alhaalla kolme painiketta, joista keskimmäinen on kaiketi "Next", mitä painamalla ``Summary`` välilehdeltä painamalla asennus käynnistyi

---




## Lähteet

Chandra, A. How to Compile C Program in Linux?. Luettavissa: https://www.scaler.com/topics/c/how-to-compile-c-program-in-linux/. Luettu 3.10.2024<br>
Geeksforgeeks. Shell Scripting – Define #!/bin/bash. Luettavissa: https://www.geeksforgeeks.org/shell-scripting-define-bin-bash/. Luettu 3.10.2024<br>
Go Dev. Tutorial: Get started with Go. Luettavissa: https://go.dev/doc/tutorial/getting-started#call. Luettu 3.10.2024<br>
Karvinen, T 2007. Shell Scripting. Luettavissa: https://terokarvinen.com/2007/12/04/shell-scripting-4/. Luettu 3.10.2024<br>
Karvinen, T 2018. Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04. Luettavissa: https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/. Luettu 3.10.2024<br>
Karvinen, T. 2021 Install Debian on Virtualbox. Luettavissa: https://terokarvinen.com/2021/install-debian-on-virtualbox/. Luettu 7.10.2024

---

Tätä dokumenttia saa kopioida ja muokata GNU General Public License (versio 2 tai uudempi) mukaisesti. http://www.gnu.org/licenses/gpl.html<br>
Pohjana Tero Karvinen 2012: Linux kurssi, http://terokarvinen.com<br><br>
Kirjoittanut <em>Santeri Vauramo</em>, 2024
