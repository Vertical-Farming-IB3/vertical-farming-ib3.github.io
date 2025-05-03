---
icon: fas fa-seedling
title: Plantenbak
order: 1
---

> Under construction
{: .prompt-warning }

## Inhoud
1. [De bedoeling](#de-bedoeling)
2. [Benodigdheden](#benodigdheden)
   - [Elektronische componenten](#elektronische-componenten)
   - [Materialen](#materialen)
3. [Planten](#planten)
4. [PCB's](#pcbs)
5. [De twee lades](#de-twee-lades)
   - [Bak 1: flood & drain](#bak-1-flood--drain)
   - [Bak 2: drip hydroponics in rockwol](#bak-2-drip-hydroponics-in-rockwol)

## De bedoeling
Onze slimme plantenbak is ontworpen om de groeiomstandigheden van planten optimaal te monitoren en automatisch te regelen. De PCB’s in elke lade hebben de volgende functionaliteiten:

- Uitlezen van het vochtgehalte van het substraat
- Meten van lichtintensiteit via een lichtsensor
- Uitlezen van temperatuur en CO₂-concentratie
- Aansturen van ventilatoren via relais
- Aansturen van een water- of nutriëntventiel via relais
- Gebruik van NFC-tags om plantensoorten te herkennen
- Energieverbruik monitoren

## Benodigdheden
Om onze slimme plantenbak te bouwen en te verbeteren, gebruiken we de volgende onderdelen en materialen:

## Elektronische componenten

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>ESP-WROOM-32</strong><br>
    Deze microcontroller met Wi-Fi- en Bluetooth-functionaliteit is het brein van elke plantenbak. Alle metingen van de verbonden sensoren worden hier op verwerkt, terwijl andere componenten worden aangestuurd. Deze wordt via ESPHome geprogrammeerd.
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/esp.png" alt="ESP-WROOM-32" style="max-width: 60%;">
  </div>
</div>

<div style="margin-bottom: 2rem;">
  <strong>NFC-tags</strong><br>
  Voor identificatie en automatisering per plantensoort
</div>

<div style="margin-bottom: 2rem;">
  <strong>PCB's</strong><br>
  Per bak één PCB
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>5V relais</strong><br>
    Om ventilatoren te schakelen
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/5vrelais.png" alt="5V relais" style="max-width: 60%;">
  </div>
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>MP1584</strong><br>
    DC-DC buck converter: 12V → 5V
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/mp1584.png" alt="MP1584" style="max-width: 60%;">
  </div>
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>Dupont kabels</strong><br>
    Voor verbindingen tussen componenten
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/dupont.png" alt="Dupont kabels" style="max-width: 60%;">
  </div>
</div>

---

## Sensoren en actuatoren

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>Capacitive soil moisture sensor</strong><br>
    Deze sensor meet het vochtgehalte van het substraat via een analoge pin van de ESP
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/csms.png" alt="CSMS" style="max-width: 60%;">
  </div>
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>GY-SCD40 module</strong><br>
    Dit component meet de CO₂-concentratie, de luchtvochtigheid en de temperatuur van de omgeving.
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/gyscd40.png" alt="GY-SCD40" style="max-width: 60%;">
  </div>
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>NFC-reader PN532</strong><br>
    Voor interactie met NFC-tags, om per bak te weten welke plant er in de kast zit
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/pn532.png" alt="PN532" style="max-width: 60%;">
  </div>
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>BH1750 lichtsensor</strong><br>
    Meet de lichtintensiteit in de kast, om te detecteren of er te veel of te weinig licht is voor de plantengroei
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/bh1750.png" alt="BH1750" style="max-width: 60%;">
  </div>
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>Ventilatoren (12V)</strong><br>
    Voor luchtcirculatie, maar ook vooral om plantjes met sterkere en dikkere stengels te kweken
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/fans.png" alt="Ventilatoren" style="max-width: 60%;">
  </div>
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>ACS712 current sensor</strong><br>
    Om het verbruik te berekenen aan de hand van de gemeten stroom die het bordje binnenkomt
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/acs712.png" alt="ACS712" style="max-width: 60%;">
  </div>
</div>

---

## Materialen

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>Rockwol</strong><br>
    Substraat voor hydrocultuur
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/rockwol.png" alt="Rockwol" style="max-width: 60%;">
  </div>
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>Potjes</strong><br>
    Voor het kweken van planten
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/cups.png" alt="Potjes" style="max-width: 60%;">
  </div>
</div>

<div style="margin-bottom: 2rem;">
  <strong>Kokosvezel</strong><br>
  Alternatief groeimedium
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>Plantenvoeding</strong><br>
    Essentiële voedingsstoffen voor gezonde plantengroei
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/voedingsstof.png" alt="Plantenvoeding" style="max-width: 60%;">
  </div>
</div>

<div style="margin-bottom: 2rem;">
  <strong>Bloempotjes</strong><br>
  Voor individuele planten in te zaaien
</div>

<div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
  <div style="flex: 1;">
    <strong>Hydrokorrels en watjes</strong><br>
    Om de plantjes in te zetten in de potjes
  </div>
  <div style="flex: 1;">
    <img src="/assets/img/Plantenbak/hydrokorrel.png" alt="Hydrokorrels" style="max-width: 60%;">
  </div>
</div>

<div style="margin-bottom: 2rem;">
  <strong>Witte verf</strong><br>
  Witte binnenkast zorgt voor optimale reflectie en lichtverdeling
</div>

<div style="margin-bottom: 2rem;">
  <strong>Consumables</strong><br>
  Zoals schroeven, kabels, soldeermateriaal, 3D-prints, ...
</div>




## Planten
We kozen deze soorten:

- Koriander ★★★
- Basilicum ★★
- Oregano ★
- Snijsla ★★★
- Munt ★

Volgens ons zijn dit handige, veelzijdige gewassen om beschikbaar te hebben in de keuken. Ze zijn ook relatief makkelijk te groeien. Hoe meer sterren, hoe makkelijker en sneller te groeien.
We zaaiden deze in aarde, om de kleine plantjes dan later te verplanten in onze vertical farm. Het is beter om in de kast met een klein plantje

## PCB's 
<!-- Bovenste afbeelding over volledige breedte -->
<div style="display: flex; justify-content: center; width: 100%; margin-bottom: 20px;">
  <img src="{{ site.baseurl }}/assets/img/Plantenbak/pb2_front.png" alt="PCB Front" style="width: 100%; max-width: 1000px; height: auto; object-fit: contain;">
</div>

<!-- Onderste twee afbeeldingen naast elkaar met gelijke hoogte -->
<div style="display: flex; justify-content: center; align-items: flex-start; width: 100%; gap: 10px;">
  <div style="flex: 1; display: flex; justify-content: center;">
    <img src="{{ site.baseurl }}/assets/img/Plantenbak/pb_back.png" alt="PCB Back" style="height: 250px; width: auto; object-fit: contain;">
  </div>
  <div style="flex: 1; display: flex; justify-content: center;">
    <img src="{{ site.baseurl }}/assets/img/Plantenbak/relais_pinout.png" alt="Relais Pinout" style="height: 250px; width: auto; object-fit: contain;">
  </div>
</div>


## De twee lades
We werken met twee technieken:
- *Drip hydroponics (drip-systeem):* Bij deze techniek wordt een voedingsoplossing langzaam en gecontroleerd druppelsgewijs over de wortels van de planten gedruppeld. Dit zorgt ervoor dat de planten altijd toegang hebben tot voldoende water en voedingsstoffen, zonder dat het wortelgedeelte constant in water staat.

- *Flood & Drain (ebb & flow):* De groeibak wordt periodiek tijdelijk overstroomd met de voedingsoplossing, waarna deze weer terugloopt naar het reservoir. Tijdens de "flood"-fase worden de wortels volledig ondergedompeld, en tijdens de "drain"-fase krijgen ze zuurstof. Dit afwisselend patroon stimuleert wortelgezondheid en efficiënte opname van nutriënten.
  
Dit laat toe om beide technieken te testen en onderling te vergelijken.

### Bak 1: flood & drain
#### De opstelling:

<img src="/assets/img/Plantenbak/bak_water.png" alt="bak met water">

### Bak 2: drip hydroponics in rockwol
#### De opstelling:

