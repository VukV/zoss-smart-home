# ZOSS projekat

### Model pretnji Smart Home sistema, Vuk Vuković R2 4/2023

<br>

## Meta napada
Meta napada u kontekstu Smart Home sistema obuhvata kompletnu infrastrukturu koja omogućava povezanost i upravljanje raznih uređaja unutar pametnog domaćinstva.

Svaki od elemenata celog sistema može biti potencijalna tačka napada.

Korisnik upotrebom klijentske aplikacije komunicira sa svojim domaćinstvom. Klijentska aplikacija dobavlja informacije od Smart Home servera, i istom šalje instrukcije za upravljanje Smart Home-a. Server je u vezi sa određenom komponentom Smart Home-a koja koordiniše sve operacije i povezuje sve ostale pametne komponente.

Ovaj složeni lanac komponenti predstavlja širok spektar mogućih meta napada, od pojedinačnih uređaja koji mogu biti kompromitovani, do kanala za komunikaciju koji mogu biti predmet presretanja ili napada koji ometaju servis.

Smart Home server, kao i komponenta koja upravlja svim uređajima, predstavljaju posebno vredne mete za napadače. Kompromitovanje takvih elemenata može dovesti do velikog broja pretnji, uključujući gubitak privatnosti, neautorizovano praćenje i kontrolu nad domaćinstvom, napad na same uređaje domaćinstva, itd.

<br>

## Cilj istraživanja
Cilj ovog istraživanja je detaljno istražiti i razumeti arhitekturu Smart Home sistema, kao i njegovih pojedinačnih komponenata. 

Jako je važno identifikovati i analizirati sigurnosne ranjivosti takvog sistema. Kroz dekompoziciju celog sistema, i razmatranje njegovih komponenata potrebno je uočiti ključne tačke koje bi mogle biti mete napada.

Neophodno je izraditi model pretnji koji bi jasno prikazao moguće napade i strategije koje napadači mogu koristiti. Ovaj model mora da pruži dublji uvid u  sigurnosne izazove sa kojima se Smart Home sistemi suočavaju.

Na kraju, istraživanje će se fokusirati na predlaganje strategija zaštite kojima napadi mogu da se ublaže ili eliminišu.

<br>

## Sadržaj (u izradi)
- [Predlog projekta](1-predlog-projekta/predlog.md) (Opis i arhitektura sistema, definicija komponenata)
- Model pretnji
    - [Dekompozicija modula](2-model-pretnji/dekompozicija-modula.md) (Grafički prikaz modula na osnovu arhitekture sistema)
    - TO DO