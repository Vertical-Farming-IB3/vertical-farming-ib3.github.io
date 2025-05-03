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

### Elektronische componenten
- **ESP-WROOM-32**:
Deze microcontroller met Wi-Fi- en Bluetooth-functionaliteit is het brein van elke plantenbak. Alle metingen van de verbonden sensoren worden hier op verwerkt, terwijl andere componenten worden aangestuurd. Deze wordt via ESPHome geprogrammeerd
- **NFC-tags**: Voor identificatie en automatisering per plantensoort
- **PCB's**: Per bak één PCB
- **5V relais**: Om ventilatoren te schakelen
- **MP1584**: DC-DC buck converter: 12V → 5V
- **Dupont kabels**: Voor verbindingen tussen componenten


#### Sensoren en actuatoren
- **Capacitive soil moisture sensor**: Deze sensor meet het vochtgehalte van het substraat via een analoge pin van de ESP
- **GY-SCD40 module**: Dit component meet de CO₂-concentratie, de luchtvochtigheid en de temperatuur van de omgeving. Dit zijn interessante parameters om te controleren of de plant zich nog in een correct milieu bevindt om te overleven en te groeien
- **NFC-reader PN532**: Voor interactie met NFC-tags, om per bak te weten welke plant er in de kast zit
- **BH1750 lichtsensor**: Meet de lichtintensiteit in de kast, om te detecteren of er te veel of te weinig licht is voor de plantengroei
- **Ventilatoren (12V)**: Voor luchtcirculatie, maar ook vooral om plantjes met sterkere en dikkere stengels te kweken
- **ACS712 current sensor**: Om het verbruik te berekenen aan de hand van de gemeten stroom die het bordje binnenkomt

#### Materialen
- **Rockwol**: Substraat voor hydrocultuur
- **Potjes**: Voor het kweken van planten
- **Kokosvezel**: Alternatief groeimedium
- **Plantenvoeding**: Essentiële voedingsstoffen voor gezonde plantengroei
- **Bloempotjes**: Voor individuele planten in te zaaien
- **Hydrokorrels en watjes**: Om de plantjes in te zette nin de potjes
- **Witte verf**: Witte binnenkast zorgt voor optimale reflectie en lichtverdeling
- **Consumables**: Zoals schroeven, kabels, soldeermateriaal, 3D-prints, ...

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

