# Analiza pretnji

U ovom dokumenti su izdvojene ključne mete napada. Za neke od njih je odrađena analiza pretnji, odnosno izdvojeni su napadi, kao i mitigacije ili odbrane koje te napade ublažavaju ili sprečavaju.

<br>

## Uvod

Ovaj dokument će se posvetiti identifikaciji i pregledu nekoliko opštih pretnji i napada sa kojima Smart Home sistem može da se sretne. Taj pregled će omogućiti sticanje osnovnog razumevanja sigurnosnih izazova sa kojima vlasnici pametnih domaćinstava mogu da se suoče.

Osvrt na sigurnost može biti veliki izazov zbog heterogene prirode ovih sistema, odnosno zbog raznolikosti mehanizama samih uređaja, kao i postojanja različitih protokola komunikacije koji u isto vreme mogu da postoje u istom sistemu [1].

Neki od protokola [1] su:
- **Žičani:** Homeplug, X10, Batibus, Cebus, Ethernet, USB
- **Bežični:** IEEE 802.11 (opšte poznat kao Wi-Fi), Bluetooth, Zigbee [2], Hiperlan

Zbog toga, sprovođenje sigurnosti često varira od uređaja do uređaja. Tako na primer, u slučaju bežičnog sistema, ako napadač uspe da ostvari nekakav pristup sistemu, velika je šansa da može doći do poverljivih informacija o korisniku ili može manipulisati njima.

Wi-Fi mreže mogu biti podložne napadima [3] zbog korišćenja fabrički postavljenih ili slabih lozinki. Korišćenje podrazumevanih pristupnih podataka omogućava napadaču da bez ikakvog truda pristupi ruteru, a samim tim i Smart Home sistemu.

<br>

## Dekompozicija modula - površine napada

Na modulu koji je sačinjen od Home Network-a i Gateway-a definisana je površina napada, odnosno definisane su tačke koje napadač može da presretne ili napadne.

<img src="slike/dekompozicija-napadi.png" alt="Dekompozizija" width="600"/>

*Dekompozicija modula: prikaz površina napada*

1. Fizički napad na uređaje, što je retko izvodljiva i često nepristupačna opcija.
2. Napad na Gateway (preuzimanje kontrole ili presretanje komunikacije), gde se dolazi do kompletne kontrole nad sistemom.
3. Napad na mrežu, gde se ostvaruje pristup svim povezanim uređajima.
4. Napad na server ili kanal kojim server komunicira sa Smart Home-om.  

<br>

## Pretnje - Napadi - Mitigacije
U narednom delu će se obraditi nekoliko pretnji, kroz prikaz stabala napada, sa načinima odbrana od istih [4][5].

<br>

### Pristup Home Network-u
Pristup mreži Smart Home uređaja je možda i najopasniji scenario koji može da zadesi jedan ovakav sistem. Pristupom Home Network-u, napadač ima na raspolaganju sve uređaje koji su u njemu povezani, što uključuje i Gateway. Jako je važno zaštititi se od napada koji mogu da dovedu do pristupa Smart Home mreži.

<img src="slike/stabla/pristup.png" alt="Pristup Home Network-u" width="650"/>

<br>

#### **Password cracking**
Password cracking napadi [6] obuhvataju više različitih načina za dobavljanje, odnosno razbijanje (cracking) šifre. Jedan od načina za sprovođenje password cracking-a je brute force [6][7] napad. Ovaj način funkcioniše po "trial-and-error" principu, odnosno napadač se služi raznim skriptama i programima kako bi pokušao što veći broj permutacija za probijanje i pogađanje šifre. Postoji nekoliko vrsta brute force napada. Može biti jednostavan brute force mehanizam, gde se napadač služi poznatim informacijama o korisniku, poput imena dece, kućnog ljubimca, godine rođenja, i od njih pokušava da sastavi šifru, ili prosto pokušava ustaljene, standardno postavljene šifre (default password), u nadi da ih korisnik nije menjao prilikom podešavanja sistema. Još jedan od brute force napada je credential stuffing, odnosno upotreba već kompromitovanih kredencijala koji su pokupljeni sa neke druge ranjive stranice ili aplikacije. Napadači se u ovom slučaju služe činjenicom da ljudi koriste iste kombinacije na više servisa. Postoji i obrnuti brute force napad, gde napadač ima poznatu šifru, i traži korisnička imena koja se podudaraju sa njom.

Da bi se ublažili brute force napadi, postavljanje složenih šifri, kao i njihova periodična promena su dve ključne strategije. Složene šifre sadrže kombinaciju velikih i malih slova, brojeva i specijalnih znakova, kao i veći broj karaktera, odnosno povećanu dužinu šifre. Duže lozinke sa nasumičnim karakterima su teže za probijanje, jer se broj mogućih kombinacija drastično povećava. To znači da će brute force metode, koje se oslanjaju na isprobavanje svih mogućih kombinacija, zahtevati znatno više vremena i resursa kako bi pokušale da probiju šifru. Redovna promena šifri može da spreči dugotrajne password cracking napade. Ako napadač počne da se približava pogađanju šifre, promena iste resetuje sav dotadašnji napredak. Takođe, promena šifre pomaže u slučaju da su neke šifre već kompromitovane bez znanja korisnika.

#### **Man in the Middle**
Man in the Middle napad [8][9] predstavlja presretanje i potencijalnu izmenu komunikacije između dve strane. Napadač se umeće između, na primer, korisnika i servera, ili servera i Gateway-a, i presreće i menja podatke pre nego što ih prosledi originalnom primaocu. Ovo omogućava napadaču da ukrade poverljive informacije ili da manipuliše podacima koji se šalju ili primaju. Man in the Middle napadi mogu biti pasivni, gde napadač samo presreće komunikaciju, ili aktivni, gde se radi manipulacija i injektovanje podataka. Ovi napadi mogu biti vrlo opasni, jer često korisnici uopšte nisu svesni da im se komunikacija presreće.

Proces izvršavanja MitM napada se sastoji iz sledećih koraka [9]:
1. **Network Scanning and Targeting:** Napadač identifikuje IP adresu mete upotrebom nekog network scanning alata poput Nmap [10].
2. **Interception and Traffic Analysis:** Kada je meta identifikovana, napadač koristi alate kao što je Bettercap [11], da presretne komunikaciju. Tada analizira saobraćaj, odnosno pakete, upotrebom softvera poput Wireshark-a [12], kako bi uočio ranjivosti u komunikaciji. 
3. **Data Modification and Exploitation of Vulnerabilities:** Nakon pronalaženja ranjivosti, napadači mogu da manipulišu podacima koji se prenose. Koriste se alati kao što je Mallory [13], kako bi se ubacili maliciozni podaci, ili ukrale poverljive informacije, kako bi se ostvario pristup uređajima ili podacima Smart Home sistema.

Kako bi se odradila mitigacija MitM napada u Smart Home sistemima, enkripcija komunikacijskih kanala igra ključnu ulogu. Potrebno je sprovesti TLS, odnosno Transport Layer Security, kriptografski protokol koji enkriptuje podatke koji se šalju između uređaja, tako da u slučaju presretanja oni budu u nečitljivom formatu. Pored TLS-a, važno je primeniti HTTP Strict Transport Security (HSTS), odnosno web sigurnosni mehanizam koji štiti od MitM napada tako što forsira komunikaciju isključivo preko sigurne HTTPS konekcije, umesto putem običnog HTTP-a. Još jedan način zaštite je upotreba RBAC-a, odnosno Role-Based Access Control-a. RBAC ograničava pristup mreži po principu korisničkih uloga, pružajući način za ograničavanje pristupa mrežnim resursima, što pomaže u sprečavanju neovlašćenog prostupa. Upotreba ovih mehanizama može znatno da smanji rizik MitM napada.

#### **Phishing**
Phishing [14] je vrsta napada gde napadači koriste lažne mejlove, poruke ili web stranice da bi prevarili žrtve da otkriju, odnosno predaju svoje osetljive informacije. Napadači često kreiraju poruke koje izgledaju kao da dolaze od legitimnih izvora, u ovom slučaju Smart Home provajdera, kako bi ubedili žrtve da im veruju i izvrše radnje poput klika na maliciozni link ili unosa poverljivih informacija na lažnim web stranicama. Phishing je efikasan jer se oslanja na socijalni inženjering i manipulaciju, a ne samo na tehničke slabosti.

Ključna zaštita protiv phishing-a je obrazovanje i svest korisnika. Ovo uključuje redovno informisanje korisnika o najnovijim taktikama koje koriste napadači, kao i o tome kako prepoznati sumnjive mejlove, poruke i web stranice. Trening treba da obuhvati primere phishing napada i upute o tome šta raditi ako se sumnja na phishing. Pored toga, preporučljivo je korišćenje spam filtera, kako bi se broj pristiglih phishing poruka sveo na minimum.

<br>

<img src="slike//mitigacije/mitigacije.png" alt="Mitigacije" width="500"/>

*Dijagram na kome su predstavljene neke od navedenih mitigacija*

<br>

### Onesposobljavanje sistema
Veliki problem sa kojim Smart Home sistemi mogu da se suoče je nefunkcionisanje ili nedostupnost istog. Onesposobljavanje jednog uređaja može narušiti rad celog sistema. Isto tako, nedostupnost sistema, odnosno njegova nemogućnost komunikacije sa korisnikom predstavlja ozbiljan problem. U ovom delu su obrađeni napadi koji dovode do onesposobljavanja Smart Home komponenti ili nedostupnosti Smart Home-a.

<img src="slike/stabla/onesposobljavanje.png" alt="Pristup Home Network-u" width="650"/>

<br>

#### **Wi-Fi jamming**
Wi-Fi jamming [15][16] je vrsta Denial of Service (DoS) napada. DoS napadi pokušavaju da utiču na dostupnost mreže tako što pokušavaju da spreče korisnike da pristupe mreži, održe komunikaciju sa mrežom i izazivaju ogroman pad performansi mreže, u pogledu njene propusnosti. Remećenje osnovnih usluga mreže totalno poremetiti njenu upotrebljivost, i čak ugroziti integritet, poverljivost i dostupnost podataka.

Jamming napadi su DoS napadi u kojima napadač šalje radio frekvencije koje se sukobljavaju i mešaju sa frekvencijama Wi-Fi mreže. Cilj je da se blokiraju mrežni uređaji i pristupne tačke (access points), kako podaci ne bi mogli da se prenose ili primaju na fizičkom sloju OSI modela [18], tako da ne mogu da se prenesu ni na više slojeve mreže.

Postoji nekoliko vrsta jamming napada:
* **Resource Unlimited Attack (RUA)** [16]: Napadač raspolaže velikom količinom resusra i konstanto preplavljuje mrežu intenzivnim signalima, narušavajući svu wireless komunikaciju u okruženju.
* **Reactive Attack** [16]: Predstavlja napad koji troši znatno manje energije, zato što čeka da detektuje slanje podataka. Tek kada ga detektuje, onda remeti mrežu, odnosno sprovodi jamming.
* **Hit and Run (HR) Attack** [16]: Ovaj napad se okida periodično, često na nasumične vremenske intervale. Na taj način je dosta teže uočiti da je u pitanju jamming napad.
* **Symbol Attack** [16]: Napad u kome napadač menja samo jedan simbol, ali kako jedan oštećeni simbol utiče na paket, onda će ceo paket podataka biti oštećen.

Na više načina se može izbegavati jamming ili štititi od istog:
* **Channel hopping** [19]: Tehnika koja podrazumeva promenu kanala za komunikaciju, odnosno promenu opsega frekvencije koji se koristi za prenos podataka. Svaki kanal funkcioniše sa drugačijom frekvencijom, što umanjuje sukobljavanje pri komunikaciji, i omogućava više uređaja da komuniciraju istovremeno. Postoji više tehnika za channel hopping. Jedan od njih je proaktivna promena, koja predstavlja promenu kanala na određeni vremenski period, nevezano od jamming napada. Pored toga postoji i reaktivna promena, koja se dešava ukoliko kanal zadesi kašnjenje, ili je na neki drugi način pretpostavljeno da se sprovodi jamming napad.
* **Detekcija reactive napada upotrebom Bit Rate Error-a (BER)** [19]: Podrazumeva praćenje grešaka u prenosu podataka. U Wi-Fi mrežama, podaci se šalju u bitovima, a BER meri koliko od tih bitova je pogrešno primljeno. Tokom reaktivnog napada ometanja, ometač čeka da detektuje prenos, a zatim sprovodi jamming napad, što dovodi do naglog povećanja BER-a. Praćenjem i analiziranjem BER-a, sistem može da detektuje prisustvo ometača kada dođe do neočekivanog povećanja grešaka u prenosu. Ova mitigacija je vrlo efikasna jer direktno sagledava uticaj jamming napada na integritet podataka.
* **Ant sistem** [19]: Ova mitigacija, nazvana po načinu na koji mravi u prirodi nalaze najkrači put do hrane, predstavlja algoritam za detekciju ometanja. Njegov rad se zasniva na inteligentnom agentu, koji se iterativno kreće kroz mrežu i prikuplja informacije sa različitih kanala. Te informacije se čuvaju u listi koja se zove "tabu", i koriste se za odlučivanje o redirekcijama unutar mreže. Sistem izvršava procenu potencijalnog ometanja na osnovu podataka o gubitku pateka, Signal-to-Noise odnosu (SNR), Bit Error Rate-u (BER), Packet Delivery odnosu (PDR), itd. Model tada računa verovatnoću jamming napada. Sistem iterativno računa ove verovatnoće između čvorova u mreži, i tako izbegava rute u kojima je ometanje detektovano. Na taj način održava integritet mreže uprkos jamming napadu.

#### **Krađa uređaja**
Krađa uređaja u smart home sistemima predstavlja fizički napad, odnosno neovlašćeno provaljivanje u kuću ili stan i otimanje pametnih uređaja. Ovo ne samo da dovodi do gubitka skupocenih uređaja, odnosno do finasijskog troška, već i kompromituje sigurnost domaćinstva. Napadači mogu iskoristiti ukradene uređaje da pristupe podacima, ili da poremete funkcionisanje celokupnog Smart Home sistema.

Glavna mitigacija je obezbeđivanje domaćinstva, odnosno postavljanje čvrstih brava, instalaciju alarmnih sistema, i korišćenje bezbednosnih kamera. 

<br>

### Dodatne mitigacije
#### **Firewall**
Firewall [1] pruža zažtitu komunikacije na nivou celog modula. Primenjuje se kako bi se kontrolisao saobraćaj mreže. Gateway, kao pristupna tačka, komunicira sa Internetom. Sav saobraćaj Smart Home mreže koji se prenosi iz interne mreže na Internet ili s Interneta na internu mrežu prolazi kroz Gateway. Prema tome, firewall se može postaviti na Gateway kako bi se sprečili svi neautorizovani pristupi ili sumnjive informacije. Firewall takođe prati i analizira sav saobraćaj, što može dati dodatni uvid u potencijalne napade.

<img src="slike/mitigacije/firewall.png" alt="Firewall" width="500"/>

<br><br>

## Literatura:

[1] A Study of Smart Home Environment and its Security Threats: Shaﬁq Ul Rehman, Selvakumar Manickam

[2] A ZigBee-Based Home Automation System: Khusvinder Gill, Shuang-Hua Yang, Fang Yao, Xin Lu

[3] https://www.wevolver.com/article/smart-home-security-security-and-vulnerabilities

[4] Threat Model and Risk Management for a Smart Home IoT System: Ahmed Redha Mahlous

[5] A Threat Modelling Approach to Analyze and Mitigate Botnet Attacks in Smart Home Use Case: Syed Ghazanfar Abbas, Shahzaib Zahid, Faisal Hussain, Ghalib A. Shah, Muhammad Husnain

[6] Password Cracking: Sam Martin, Mark Tokutomi

[7] https://crashtest-security.com/password-attack/

[8] https://www.imperva.com/learn/application-security/man-in-the-middle-attack-mitm/

[9] IoT and Man-in-the-Middle Attacks: Hamidreza Fereidouni, Olga Fadeitcheva, Mehdi Zalai

[10] https://nmap.org/

[11] https://www.bettercap.org/

[12] https://www.wireshark.org/

[13] https://github.com/intrepidusgroup/mallory

[14] https://www.ibm.com/topics/phishing

[15] Jamming DoS in IEEE 802.11 WLANs: Sunitha Azad, Eitan Altman, Majed Haddad

[16] Effects of DoS Attack in Wi-Fi Broadband Network: Akende Y. Nalukui, Charles S. Lubobya

[17] https://www.cisa.gov/news-events/news/understanding-denial-service-attacks

[18] https://www.imperva.com/learn/application-security/osi-model/

[19] Jamming and Anti-jamming Techniques in Wireless Networks: Kanika Grover, Alvin Lim, Qing Yang