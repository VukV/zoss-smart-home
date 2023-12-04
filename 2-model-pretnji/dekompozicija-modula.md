# Dekompozicija modula

### Na visokom nivou

![Dijagram 1](slike/dijagram-1.png)
<br>
Na najvišem nivou su izdvojeni sledeći moduli
* Korisnička aplikacija - predstavlja interfejs preko kog korisnik Smart Home sistema stupa u kontakt sa sistemom, dobavlja informacije, upravlja sistemom, sprovodi komande, itd.
* Smart Home server - modul koji direknto komunicira sa Smart Home sistemom, prosleđuje korisnikove zahteve, reguliše podatke, komunicira sa bazom, itd.
* Smart Home sistem - modul u kome se zapravo nalaze smart home komponente; spolja je "otkriven" preko smart home gateway-a

### Dekompozicija Smart Home servera 

![Dijagram 2](slike/dijagram-2.png)
<br>
Smart Home server se u određenoj meri ne može detaljno dekomponovati, jer to zavisi od same arhitekture aplikacije koja je na serveru.
Ona može biti monolitna, i kao takva sve komponente sadržati u sebi, može biti i servisno orijentisane ili mikroservisne arhitekture. Od toga će i zavisiti pristup prilikom modelovanja pretnji.
Ono što jeste sigurno je sledeće:
* Adminski portal - zaseban servis, ili deo u sistemu preko koga samo privilegovani (admin) korisnik unosi promene i ostvaruje pristup osetljivim komandama ili podacima
* Korisnički podaci - osetljivi podaci koji se koriste za pristup sistemu (kredencijali, šifre, itd.)
* Podaci sistema - Baza podataka koja čuva zbivanja, merenja i sve ostale (istorijske) podatke koji se dobavljaju uređajima unutar Smart Home sistema


### Dekompozicija Smart Home sistema
![Dijagram 3](slike/dijagram-3.png)
<br>
Unutar samog Smart Home sistema se izdvajaju dve bitne komponente:
* Smart Home gateway - centralna jedinicat, srž sistema, zadužen za kontrolu i komunikaciju sa spoljašnjim okruženjem
* Uređaji
    * Senzori (merači pritiska, temperature, itd.)
    * Smart (bela) tehnika (klime, frižideri, itd.)
    * Ostali tipovi IoT uređaja