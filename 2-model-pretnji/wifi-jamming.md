# Wi-Fi jamming

U ovom dokumentu je prikazano sprovođenje [Wi-Fi jamming napada](analiza-pretnji.md#wi-fi-jamming). Ovi napadi se oslanjaju na upotrebu Wi-Fi jammer-a, odnosno uređaja koji preplavljuju mrežu radio frenkvencijama, kako bi istu onesposobili da prima podatke.

<img src="slike/jamming/jammer2.png" alt="WiFi Jammer" width="220"/>
<img src="slike/jamming/jammer1.jpg" alt="WiFi Jammer" width="280"/>

*Wi-Fi jamming uređaji*

<br>

Kako se cene ovih uređaja kreću po nekoliko stotina, pa i hiljada dolara, a pritom je njihova upotreba nelegalna, za akademske potrebe izvođenja ovog napada upotrebljen je ESP8266 mikročip [1][2] na NodeMCU tabli [3]. 

NodeMCU je platforma za izradu prototipova IoT projekata koja se zasniva na ESP8266 mikročipu. Ova platforma omogućava pisanje softvera u različitim jezicima kao što su Lua, C++ i MicroPython, što pruža fleksibilan razvoj. NodeMCU sadrži ESP8266 Wi-Fi mikročip, koji ima ugrađen TCP/IP modul, što mu omogućava da se poveže na Wi-Fi mrežu i izvršava jednostavne TCP/IP konekcije.

ESP8266 mikročip, srce NodeMCU platforme, je niskobudžetni Wi-Fi mikročip sa punim TCP/IP stekom i mikrokontrolerskom funkcionalnošću. Proizveden je od strane Espressif Systems-a, kompanije iz Šangaja, koja se bavi proizvodnjom čipova, IoT i cloud rešenjima. Sa malim dimenzijama i niskom potrošnjom energije, ovaj čip je pogodan za projekte gde su prostor i energetska efikasnost ključni. 

Zbog svoje pristupačne cene, ESP8266 je privukao mnoge hakere da istražuju čip i softver na njemu.

<img src="slike/jamming/ESP8266-NodeMCU.jpg" alt="WiFi Jammer" width="350"/>

*NodeMCU ESP8266*

<br>

## Napad

TO DO
- opis napada
- deauth packets

### Priprema i instalacija
* proces
* kod
* itd.

### Izvršavanje napada
* to do

<br>

## Literatura:

[1] https://www.espressif.com/en/products/socs/esp8266

[2] https://hackaday.com/2014/08/26/new-chip-alert-the-esp8266-wifi-module-its-5/

[3] https://github.com/nodemcu/nodemcu-devkit