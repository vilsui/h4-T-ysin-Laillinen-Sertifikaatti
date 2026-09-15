H4 Täysin laillinen sertifikaatti
Ville Suikki

x) Lue/katso ja tiivistä.

OWASP 2021: OWASP Top 10:2021

1. Broken Access Control - Puutteellinen pääsynhallinta on yleisin web-sovellustason haavoittuvuus. Kyseessä tilanne jossa jossa järjestelmä ei tarpeeksi varmista onko käyttäjällä oikeutta pyydettryyn tietoon tai toimeen. Mahdollistaa hyökkääjän pääsyn toisten tietojen muokkauksen, omien käyttöoikeuksien korotus esim. Adminin tasolle. Suojatuminen vaatii että ACL-tarkistukset luotettavasti palvelimelta, oikeuksien evääminen oletuksena (deny by default) ja jokaisen pyynön yhteydessä vahvistus tieetueiden todellisesta omistajuudesta. 

2. Cryptographic Failures - Riittävän saualauksen epäonnistuminnen tai sen puuttuminen. Mahdollistaa arkaluontoisen datan (henkilötiedot, salasanat, luottokorttitiedot, liikesalaisuudet) paljastumisen. Yleisimmät ongelmat ja juurisyyt ovat että tietoa siirretään verkon yli tai tallennetaan tietokantoihin ilman salausta. Jos protokollat, 
huono avaintenhallintra ja heikot salasanat ovat arkipäivää, hyökkäysrajapinta suurenee. Suojaudutaan että ei tallenneta arkaluontoista dataa, salataan data vahvasti myös levossa ja käytetään vahvoja salasanoja ja hallitaan avaimia oikein varmistamalla niiden turvallisuus kryptografialla.

3. Injecton - Tilanne jossa sovellus ei käsittele käyttäjän syötettä turvallisesti jolloin hyökkääjä pystyy syöttämään väärää/haitallista dataa ja niiden 
komentojen suorittamisen. Mahdollistaa koko tietokannan varastamisen, muokkaamisen tai palvelimen haltuunoton (esim. SQL-injektio) Yleisin ongelma ja juurisyy 
on että käyttäjän syöttämää dataa ei validoida tai puhdisteta ja se yhdistetään sellaisenaan suoraan tietokantakyselyyn/komentoihin. Suojaudutaan pitämällä data
ja komennot aina tiukasti erillään toisistaan käyttämällä turvallisia parametroituja kyselyjä tai ORM- työkaluja ja vahvistetaan syötteet palvelimen puolella.

4. Insecure Design - Ohjelmiston arkkitehtuurin ja alkuperäise suunnitteluun liittyvät puuteet tai sen kokonaan puuttuvat turvakontrollit. Mahdollistaa erilaistan
toimintalogiikan virheiden hyödyntämisen (botit, järjestelmän mainipulointi) joita välttämättä taydellisesti kirjoitetut koodit eivät voi estää sillä supojausmekanisemjä ei ole. Yleisimpinä ongelmina tässä että tietoturvavaatimuksia ja liiketoimisia riskejä ei määritellä tarpeeksi ennen koodaukse aloittamista eikä järjestelmän uhkia ole tunnnistettu. Suojaudutaan integroimalla tietoturva osaksi ohjelmistokehityksen elinkaarta alusta alkaen hyödyntämällä "threat modeling" uhkamallinnnusta ja turvalllisija arkkitehtuurimalleja. 

5. Security Misconfiguration - Puutteelliset, virheelliset tai oletusarvoiset tietoturva-asetukset missä tahansa sovelluksen, palvelimen tai pilvipalvelun osassa. Mahdollistaa luvattoman pääsyn järjestelmään, arkaluontoisen datan paljastumisen tai palvelimen haltuunoton. Ongelmina ja juurisyinä että järjestelmään jätetään 
sellaiset ominaisuudet, portit tai oletussovellukset jotka tarpeettomia. Ei oletussalasanojen vaihtoa, pilvipalveluiden liian avoimet käyttöoikeudet ja security
headers:ien puuttuminen lisäävät riskejä. Suojaudutaan poistamalla kaikki ylimääräiset komponentit ja ominaisuudet asenusvaiheessa ja segmentoimalla arkkitehtuuria. 
Automatisoitu ja toistettava koventamisprosessi varmistaa että kehitys, testaus ja tuotanto on konffattu turvallisesti.

6. Vulnerable and Outdated Components - Järjestelmässä käytettyjen kolmannen osapuolen komponenttien kute ohjelmistokehysten, kirjastojen, tietokantojen tai OS 
turvapuutteet tai vanhetuneet versiot. Koska komponentit suoritetaan usein samoilla oikeuksilla kuin itse sovellus, niiden haavouttuvuudet voivat johtaa 
tietomurtoihin tai haitallisen koodin suoritukseen (Esim. Struts 2). Ongelmina ja jyyrisyinä ettei sovelluksessa käytettyjä komponentteja ja aliriippuvuuksia 
tunneta. Niitä ei skannata säännöllisesti haavoittuvuuksien varalta ja päivitetään harvoin. Suojaudutaan poistamalla tarpeettomat riippuvuudet ja ominaisuudet
automatisoidulla inventaariolla (esim. ohjelmistokoostumuksetn analyysityökalut)) ja lataamalla paketit vain luotettavista virallisista lähteistä sekä luomalla 
säännöllisten päivitysten hallintaprosessi. 

7. Identification and Authentication Failures - Käyttäjän henkilöllisyyden, todennuksen tai istunnon varmistamisen epäonnistuminen. Mahdollistaa luvattoman pääsyn 
järjestelmään, käyttäjätililien kaappaamisen ja toisen identiteetillä toimimisen. Ongelmina ja juurisyinä että järjestelmä sallii automaattiset salasanahyökkäykset 
(brute force ja tunnuksien kokeilun eli credential stuffing), hyväksyy heikot tai oletus-salasanat, käyttää turvattomia salasanan palautusmekanismeja (Turvakysymykset), 
ei hyödynä MFA'ta tai käsittelee istuntoja turvattomasti paljastamalla istuntotunnisteen URL-osoitteesta. Suojaudutaan ottamalla MFA-tunnistus käyttöön, estämällä 
oletus- tai liian heikot salasanat, rajoittamalla epäonnistuneita kirjautumisyrityksiä ja käyttämällä turvallista palvelinpuolen istunnonhallintaa joka luo 
joka kerta uuden istuntotunnisteen sisäänkirjautuessa. 

8. Software and Data Integrity Failures - Oletuksiin luottaminen ohjelmistopäivityste, kriittisen datan ja CI/CD-kehitysputkien kohdalla ilman että niiden eheyttä 
ja alkuperä varmistetaa. Mahdollistaa luvattoman pääsyn haittakoodin suorittamisen- tai järjestelmän vaarantumise (esim. toimitusketjuhyökkäyksen kute SolarWinds, 
tai haitallisen datan deserialisoinnin kauuttta). Ongelmat ja juurisyyt ovat että sovellus hyödyntää kirjastoja, moduuleja, tai automaattisia päivityksiä epäluotettavista lähteistä, ohjelmistokehityksen CI/CD-putken tietoturva on puutteellinen tai järjestelmä purkaa käyttäjän manipuloitavissa olevaa dataa ilman eheystarkistusta. Suoajudutaan käyttämällä aina digitaalisia allekirjoituksia päivitysten ja datan vahvistamiseen, lataamalla komponentit vain luotetuista lähteistä, varmistamalla ohjelmiston toimitusketjun turvallisuuden (esim. OWASP Dependecy Check työkalulla), turvaamalla julkaisuprosessi )CI/CD)

9. Security Logging and Monitoring Failures - Puutteelinen lokien kerääminen, järjestelmien valvonta ja poikkeamiiin reagointi, mikä tekee aktiivisten tietomurtojen 
havaitsemisesta mahdotonta. Mahdollistaa sen, että hyökkääjät voivat toimia järjestelmässä huomaamatta pitkiä aikoja ja peittää jälkensä. Yeisimpinä ongelmina ja juurisyinä että epäonistuneita kirjautumisia tai "arvokkaita transaktioita" ei kirjata, lokit säilytetään vain paikallisesti jolloin eivät laukaise hälytyksiä epäilyttävästä toiminnasta, tai lokidata paljastaa arkaluontoista dataa ja on altis injektiohyökkäyksille huonon ohjelmoinnin vuoksi. Suojaudutaa kirjaamalla tarkasti kaikki kirjautumis- 
ja pääsynhallinan epoäonnistumiset, tallentamalla lokit keskitetysti yhdenmukaiseen ja turvalliseen muotoon, asettamalla eheystarkistuksia kriittisille tapahtumille (esim. kuten vain lisäyksen sallivat taulut) sekä luomalla selkeät reaaliaikaiset valvonta, hälytys ja poikkeamatilanteiden hallintaprosessit (incident response plan) nopeaaan reagointiin.

10. Server-Side Request Forgery - Tilanne, jossa sovellus hakee etäresurssin käyttäjän syöttämän URL-osoitteen perusteella ilman riittävää validointia. 
Mahdollistaa sen, että hyökkääjä voi pakottaa palvelimen lähettämään pyyntöjä kohteisiin, ja ohittamaan palomuurit sekä verkon suojaukset,  joka johtaa sisäverkon skannaamiseen, arkaluonteisten paikallisten tiedostojen lukemiseen tai pilvipalveluiden metadatan vaarantumiseen. Oongelmina ja syinä käyttäjän URL-syötteisiin sokeasti luottaminen sekä puutteelliset verkkotason eristykset. Suojaudutaan segmentoimalla verkot ja asettamalla palomuureihin tiukat deny by default säännöt, validoimalla kaikki syötteet yksinomaan positiivisella sallittujen listalla (allow list) estolistojen (deny list) sijaan, estämällä HTTP-uudelleenohjaukset skeä varmistamalla, ettei sovellus välitä sisäisten pyyntöjen raakavastauksia suoraan takaisin käyttäjälle.

11. Insecure direct object references (IDOR) - Pääsynhallinan haavoittuvuus joka syntyy kun verkkosovellus käyttää käyttäjä syöttämää dataa (tunnukset, ASNRO) suoraan
viitatakseen taustajärjestelmän objekteihin ilman riittäviä käyttöoikeuksien tarkistusta. Mahdollistaa URL-osoitteen parametrin arvon muutoksen hyökkääjän toimesta, jolloin 
toisten käyttäjien tietoihin pääseminen onnistuu ja toteuttamaan horisontaalista/vertikaalista oikeuksien korotusta (privilige escalation). Yleisimmät ongelmat ja juurisyyt ovat että sovellus luottaa täysin käytäjän antamaan suoraan objektiviittaukseen varmistamatta, onko pyynnön esittäjällä todellista oikeutta resurssiin. Suojaudutaan varmistamalla aina palvelinpuolen koodissa että kirjautuneella käyttäjällä on oikeus pyydettyyn kohteeseen/dataan, riippumatta siitäm itä tunnisteita sovellluksessa käytetään.

12. Path traversal - Syntyy kun verkkosovellus käyttää käyttäjän syöttämää dataa suoraan palvelimen tiedostojärjestelmään ilman riittävää validointia. Mahdollistaa esimerkiksi ../-komentojen avulla siirtymisen hakemistopuusa ylemmäs, jolloin hyökkääjä voi päästä käsiksi sovelluksen hakemiston ulkopuolisiin tiedostoihin kuten salasanoihin. Yleisimmät ongelmat ja juurisyyt ovat, että sovellus luottaa käyttäjän antamaan tiedostopolkuun eikä tarkista, pysyykö pyydetty tiedosto sallitun hakemiston sisällä. Haavoittuvuus voi mahdollistaa esimerkiksi järjestelmä-, asetus- tai lähdekooditiedostojen luvattoman lukemisen. Suojaudutaan validoimalla käyttäjän syöte ja varmistamalla aina palvelinpuolella, jotta lopullinen tiedostopolku pysyy sille tarkoitetun hakemiston sisällä riippumatta millasen polun käyttäjä sovellukselle antaa.

13. Cross-site scripting XSS - käyttää käyttäjän syöttämää dataa suoraan osana verkkosivun sisältöä ilman riittävää suodatusta tai enkoodausta. Hyökääjä voi syöttää sivulle esim. JavaScript koodia, joka suoritetaan toisen käyttäjän selaimessa. XSS voi olla esim. reflected, jolloin haitallinen syöte kulkee pyynnön mukana ja palautuu vastauksessa, tai stored, jolloin haitalinen sisältö tallennetaan palvelimelle ja suoritetaan myöhemmin sivulla vieraileville toisille käyttäjille. Hyökkäyksen avulla voidaan esimerkiksi muokata ssivuja, suorittaa toimintoja uhrin oikeuksilla tai käsitellä käyttäjän selaimessa olevaa arkaluonteista dataa. Juurisyynä on yleensä se, että sovellus luottaa käyttäjän syötteeseen eikä enkoodaa sitä oikein siinä kontekstissa, jossa se sijoitetaan HTML-sivulle. Suojaudutaan validoimalla ja enkoodaamalla käyttäjän syöte oikean tyypin mukaisesti sekä käyttämällä tarvittaessa CSP'tä lisäsuojana. Mahdollistaa hyökkääjälle lukuisia eri tapoja aiheuttaa haittaa (Keylogging, istuntokaappaus, etc)



Lähteet: https://top10.owasp.org/2021/A05_2021-Security_Misconfiguration/ 
         https://portswigger.net/web-security/access-control/idor
         https://portswigger.net/web-security/file-path-traversal
         https://portswigger.net/web-security/cross-site-scripting


A) Totally Legit Certificate

Lähdin etenemään Kalissa ajamalla sudo apt update ja sudo apt-get install zaproxy, jonka jälkeen sain zaproxyn auki. Tämän jälkeen avasin Tools --> Options ---> Network --->
Server Certificates ja tallensin generoidun CA-sertifikaatin työpöydälle. Tämän jälkeen siirryin Firefoxiin importtaamaan certin itse selaimeen ja laittamaan proxyn päälle.
Firefoxissa  siirryin asetusvalikon kautta Settings -kohtaan, hakukenttään "Certificates" ---> "View Certificates" ---> "Authorities" ja klikattiin "Import". Tämän jälkeen
hain työpöydälle tallenetun certin, ja täppä kohtaan "Trust this CA to identify websites". 

Proxy asetusten säätö firefoxissa hoitui "Settings" kohdasta "proxy", josta määritettiin manual proxy configuration. HTTP proxy kohtaan 127.0.0.1 ja kohtaan port 8080 ja
vielä täppä ruutuun "Also use this proxy for HTTPS". Tämän jälkeen viimeinen kohta olikin kun osoiterivin about:config asetuksesta käytiin muuttamassa network.proxy.allow_hijacking_localhost
kohta booleanin "true"-ksi. 

<img width="1084" height="909" alt="Näyttökuva 2026-09-15 kello 18 40 52" src="https://github.com/user-attachments/assets/8ceb00d5-45e8-4b31-86b4-943f878cadaf" />



B) Siirryin lataamaan FoxyProxyn addonin firefoxiin ja ladattuani sen siirryin sen asetuksiin josta käytiin määrittämässä uusi proxy painamalla add, ja määrittämällä tänne asetuksiksi hostnameen: 127.0.0.1 ja porttiin 8080. Määritin vielä erilliset proxy by patternsit localhostille- sekä portswiggerille jotta foxyproxy ohjaa ZAPiin vain silloin kun avaan localhost- tai portswigger.net osoitteita ja muut sivut toimivat normaalisti ilman proxyä. 

<img width="2256" height="1906" alt="image" src="https://github.com/user-attachments/assets/10c56f62-39e6-4f1d-87cb-267bc70eb333" />
<img width="2168" height="1818" alt="image" src="https://github.com/user-attachments/assets/9a4eff56-d927-481a-996d-d50f9cbac552" />



C) Lab: Reflected XSS into HTML context with nothing encoded

Siirryin portswiggerin sivustolle aloittaakseni labran. Laitoin "Search" -hakukenttään: "morjesta pöytään" ja tulos näytti tulostuneen ZAP'in request historiatietoihin  
<img width="2168" height="1818" alt="image" src="https://github.com/user-attachments/assets/4d2c0692-c808-4563-95e0-f7ea6a83cb5c" />
Tapa millä löysin haavoittuvuuden konkreettisesti oli kun katsoin ZAP'ista, niin heijasti syötteeni "Response" -osiossa sellaisenaan minä olin sen hakukenttään syöttänyt. 

Seurattuani portswiggerin ohjeistusta, ajoin labrasivun hakukentässä <script>alert(1)</script> -komennon. Kyseinen skripti on kyberturvallisuudessa käytetty vakiotestikomento (proof of concept) XSS-haavoittuvuuksien löytämiseen ja todistamiseen. Syy miksi se toimii on se että se on HTML tägi, joka kertoo verkkoselaimelle että komennossa on suoritettavaa JS-koodia, eikä normi tekstiä. Alert toimii komentona joka käskee selainta avaamaan ponnahdusikkunan (alert-laatikon) jonka sisällä numero 1. Jotta saadaan haitaton turvallisuustesti tehtyä niin käytetään tuota että ponnahdusikkuna tulostaa vain numeron 1 ja on täten turvallinen tapa todistaa palvelimelle eettä selain suoritti syötetyn koodin. 

<img width="2256" height="1906" alt="image" src="https://github.com/user-attachments/assets/41d89c72-d09e-4a89-a798-d6c401770b9e" />
<img width="2256" height="1906" alt="image" src="https://github.com/user-attachments/assets/5b489896-f304-4734-aef1-a985b008c395" />

Lähteet: https://portswigger.net/burp/documentation/desktop/testing-workflow/vulnerabilities/input-validation/xss/testing-for-reflected-xss

D) Lab: Stored XSS into HTML context with nothing encoded

Tässä tehtävässä lähdin eteemään portswiggerin ohjeistuksen mukaisesti avaamalla blogipostauksen, täyttämällä tarvittavat kentän kommentin kirjoittamiseen ja syöttämällä "<script>alert(1)</script>" koodin itse kommenttikenttään. Haavoittuvuus johtuu siitä, että palvelin ottaa käyttäjän syöttämän kommentin vastaan ja tallentaa sen suoraan tietokantaansa ilman minkäänlaista validointia tai vaarallisten merkkien puhdistusta. Kun sivu ladataan uudelleen, palvelin hakee koodin tietokannasta ja tulostaa sen selaimeen ilman HTML-enkoodausta (nothing encoded). Tämän takia selain luulee hyökkääjän syötettä osaksi sivuston alkuperäistä koodia ja suorittaa sen. Siinä missä Reflected XSS vaatii että klikkaa erillistä linkkiä tai tekee haun, Stored XSS hyökkääjä syöttää koodin sovellukseen (Tässä tapauksessa kommenttikenttä), sovellus tallentaa koodin tietokantaansa ja aina kun joku käyttäjä vierailee sivulla joka näyttää kyseisen kommentin, haitallinen skripti ajautuu myös muilla. 

<img width="2256" height="1906" alt="image" src="https://github.com/user-attachments/assets/f237e4ef-1c6e-4b10-90c3-ae1c66cc8ca2" />

Lähteet: https://portswigger.net/burp/documentation/desktop/testing-workflow/vulnerabilities/input-validation/xss/testing-for-stored-xss

E) Mitä hyökkääjä hyötyy XSS-hyökkäyksestä?

Tehtävissä ajettu skripti osoittaa että haavoittuvuus on olemassa (proof of concept) mutta hyökkäävä pystyy tällä tiedolla hyödytämään useampaa eri mekanismia:

1. session Hijacking - JS lukee selaimen evästeitä tai paikallista muistia. Jos ei ole suojattu "httponly -lipulla", Hyökkääjä voi lähettää evästeet omalle palvelimelle ja tekeytyä uhriksi kaappaamalla hänen tilin.
2. Phishing - Hyökkääjä injetktoi sivulle aidon näköisen valekirjautumisikkuan joka voisi sanoa "Istunto vanheni, kirjaudu uudestaan" ja täten kaappaa käyttäjän salasanan.
3. Valtuutettujen toimintojen suoritus - Kun skripti pysyy uhrin selaimessa, se voi tehdä taustalla ties mitä. Esimerkkejä on että sähköpostia on lähtenyt, vaihtaa käyttäjän säpo/salasana tai verkko-ostokset.
4. Keylogging - Hyökkääjä lisää skriptin joka tallentaa käyttäjän kirjotetut näppäimet ja saa täten haltuunsa arkaluontoista tietoa kuten salasanat, jotka hyökkääjä ohjaa omalle palvelimelleen.

Lähteet: https://community.owasp.org/attacks/xss/
         https://portswigger.net/web-security/cross-site-scripting
         https://portswigger.net/web-security/cross-site-scripting
         https://www.paloaltonetworks.com/cyberpedia/xss-cross-site-scripting


F) File path traversal, simple case

Avasin labran ja tarkistin ensimmäisen ZAP'ista Options --> Display ja täppä ruutuun "Process images in http requests/responses" jotta kuvien latauspyynöt on historiassa. Avasin labran sivuilta kuvan oheisen linkin <img width="2256" height="1906" alt="image" src="https://github.com/user-attachments/assets/ee5e6f2d-5e2a-4cf3-bfa9-fb889e576692" />
jonka jälkeen tarkistin ZAP'ista että se näkyy siellä ja löytyi 
<img width="2256" height="1906" alt="image" src="https://github.com/user-attachments/assets/56f6e6cb-875d-473a-9051-720101f06da2" /> jonka jälkeen klikkasin ctrl + W ja pääsin requester välilehdelle, missä vaihdoin kohdan filename=21.jpg ---> filename=../../../etc/passwd 
<img width="2168" height="1818" alt="image" src="https://github.com/user-attachments/assets/53c36690-08c7-47f2-8f7c-3b0231a57837" /> jonka jälkeen painoin send. Tämän jälkeen siirryin vielä response puolelle ja sain labran valmiiksi! 
<img width="2336" height="1906" alt="image" src="https://github.com/user-attachments/assets/d019e793-46c4-42e4-bb4d-c2e539feede9" />

Tässä haavoittuvuus johtuu siitä, että web-sovellus ottaa käyttäjän (tässä tapauksessa selaimen) lähettämän tiedostonimen vastaan ja käyttää sitä suoraan osana palvelimen sisäistä hakemistopolkua. Palvelin ei tarkista tai validoi syötettä millään tavalla (esim. estämällä polunvaihtomerkit), eikä se rajoita tiedostojen lukuoikeuksia pelkästään sallittuun tuotekuvakansioon. Testasin haavoittuvuutta muokkaamalla filename-parametrin arvoksi ../../../etc/passwd ja lähetin pyynnön eteenpäin. Merkkiyhdistelmä käskee palvelimen käyttöjärjestelmää siirtymään hakemistopuussa yhden tason ylöspäin. Toistamalla näitä merkkejä tarpeeksi monta kertaa hyökkääjä pääsee ulos web-palvelimen julkisesta hakemistosta ja voi lukea järjestelmätiedostoja. ZAPin Response-ikkunasta näin, että kuvan sijaan palvelin palautti pyyntööni Linux-palvelimen arkaluonteisen /etc/passwd -käyttäjätiedoston sisällön.

G) File path traversal, traversal sequences blocked with absolute path bypass

Tässä web-sovellus ottaa käyttäjän (Nyt selaimen) lähettämän tiedostonimen vastaan ja käyttää sitä suoraan osana palvelimen sisäistä tiedostopolkua. Palvelin koittaa estää tavalliset ../-tyyppiset "path traversal -sekvenssit", mutta suojaus ei estä absoluuttisen tiedstopolun käyttämistä. Seurattuani portswiggerin ohjeistusta löysin haavoittuvuuden ZAPilla tuotteen kuvan lataamiseen liittyvää pyyntöä, jossa filename-parametrin arvona oli esimerkiksi 29.jpg jonka tässäkin pystyi taklaamaan muuttamalla filename=/etc/passwd. Muokkasin ZAPin Requesterissa parametrin arvonja lähetin pyynnön uudelleen. Palvelin hyväksyi absoluuttisen polun ja palautti kuvan sijaan Linux-palvelimen /etc/passwd-tiedoston sisällön. Tämän perusteella palvelin ei rajoita tiedostojen lukemista ainoastaan sallittuun kuvakansioon, vaan käyttäjä pystyy vaikuttamaan siihen mitä tiedostoa palvelin yrittää avata. Haavoittuvuus mahdollistaa muiden palvelimen tiedostojen lukemisen.

<img width="2784" height="1904" alt="image" src="https://github.com/user-attachments/assets/d86aa94b-9c46-454e-8de6-207fb49547ad" />
<img width="2784" height="1904" alt="image" src="https://github.com/user-attachments/assets/ef0fa7e7-edb8-459c-915e-d863d9f5a0ce" />


H) File path traversal, traversal sequences stripped non-recursively

Tässä tehtävässä web sovellus koittaa sudoattaa käyttäjän lähettämästä polusta ../ tyyppiset traversal-sekvenssit pois, mutta suodatus tapahtuu vain kerran. Haavoittuvuus ZAP'issa löytyi kun katsoi tuotteen kuvan lataamiseen käytettyä filename -parametria ja kokeilemalla, miten palvelun käsittelee eri tiedosto polkuja tässä käytin portswiggerin ohjeistuksen mukaista "....//....//....//etc/passwd" merkkijonoa. Jos palvelin poistaa ../ sekvenssit, niin jöäkljelle jää uusia ../ -sekvenssejä koska syötettä ei käsitellä enää uudelleen. Tällä tavalla muodostunut polku mahdollistaa siirtymise hakemistopuussa ylöspäin ja /etc/passws tiedoston lukemisen. Haavoittuvuudelle syynä sen puutteellisen syötteen suodatus joka yrittää estää tietyn merkkijonon sen sijaan että lopullista tiedostopolun olevan sallittun hakemiston sisällä. 

<img width="2784" height="1904" alt="image" src="https://github.com/user-attachments/assets/386b22ca-bf96-403e-82c6-bb3d25b28319" />

Solved <img width="2784" height="1904" alt="image" src="https://github.com/user-attachments/assets/40de8b5f-131c-4ce7-b53b-dda8f10b775a" />

