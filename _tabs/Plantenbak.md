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
4. [De twee lades](#de-twee-lades)
   - [Bak 1: flood & drain](#bak-1-flood--drain)
   - [Bak 2: drip hydroponics in rockwol](#bak-2-drip-hydroponics-in-rockwol)


## De bedoeling
Onze bordjes moeten deze functionaliteit hebben:

- Vochtigheidsniveau van het substraat uitlezen
- Lichtsensor om hoeveelheid licht te meten
- Temperatuur en CO₂-concentratie uitlezen
- Ventilatoren bestuurbaar met relais
- Ventiel bestuurbaar met relais
- NFC-tags per plantensoort
- Verbruik monitoren

## Benodigdheden
Om onze slimme plantenbak te bouwen en te verbeteren, gebruiken we de volgende onderdelen en materialen:

### Elektronische componenten
- **ESP-WROOM-32** – Microcontroller met Wi-Fi- en Bluetooth-functionaliteit
- **Capacitive soil moisture sensor** – Meet het vochtgehalte van het substraat
- **GY-SCD40 module** – Meet CO₂-concentratie
- **NFC-reader PN532** – Voor interactie met NFC-tags
- **NFC-tags** – Voor identificatie en automatisering per plantensoort
- **PCB's** – Per bak één PCB
- **BH1750 lichtsensor** – Meet de lichtintensiteit
- **Ventilatoren (12V)** – Voor luchtcirculatie en koeling
- **Relais SR5** – Om ventilatoren te schakelen
- **MP1584** – DC-DC buck converter: 12V → 5V
- **Dupont kabels** – Voor verbindingen met sensoren
- **5V relais** – Om een ventiel te schakelen
- **Power-monitoring bord** - Om het verbruik te meten

### Materialen
- **Rockwol** – Substraat voor hydrocultuur
- **Potjes** – Voor het kweken van planten
- **Kokosvezel** – Alternatief groeimedium
- **Plantenvoeding** – Essentiële voedingsstoffen voor gezonde plantengroei
- **Bloempotjes** – Voor individuele planten in te zaaien
- **Hydrokorrels** – Voor wateropslag en beluchting van de wortels
- **Witte verf** - Witte binnenkast zorgt voor optimale reflectie en lichtverdeling

## Planten
We kozen deze soorten:

- Koriander ★★★
- Basilicum ★
- Oregano ★★
- Snijsla ★★★
- Munt

Volgens ons zijn dit handige, veelzijdige gewassen om beschikbaar te hebben in de keuken. Ze zijn ook relatief makkelijk te groeien. Hoe meer sterren, hoe makkelijker te groeien.

## De twee lades
We werken met twee technieken:
- *Drip hydroponics (drip-systeem):* Bij deze techniek wordt een voedingsoplossing langzaam en gecontroleerd druppelsgewijs over de wortels van de planten gedruppeld. Dit zorgt ervoor dat de planten altijd toegang hebben tot voldoende water en voedingsstoffen, zonder dat het wortelgedeelte constant in water staat.

- *Flood & Drain (ebb & flow):* De groeibak wordt periodiek tijdelijk overstroomd met de voedingsoplossing, waarna deze weer terugloopt naar het reservoir. Tijdens de "flood"-fase worden de wortels volledig ondergedompeld, en tijdens de "drain"-fase krijgen ze zuurstof. Dit afwisselend patroon stimuleert wortelgezondheid en efficiënte opname van nutriënten.
Dit laat toe om beide technieken te testen en onderling te vergelijken.

### Bak 1: flood & drain
#### De opstelling:

<img src="/assets/img/Plantenbak/bak_water.png" alt="bak met water">

<div style="display: flex; justify-content: center; align-items: stretch; width: 100%; gap: 10px;">
  <div style="flex: 1; display: flex; justify-content: center;">
    <img src="{{ site.baseurl }}/assets/img/Plantenbak/pb2_front.png" alt="PCB Front" style="height: 300px; width: auto; object-fit: contain;">
  </div>
  <div style="flex: 1; display: flex; justify-content: center;">
    <img src="{{ site.baseurl }}/assets/img/Plantenbak/pb_back.png" alt="PCB Back" style="height: 250px; width: auto; object-fit: contain;">
  </div>
</div>

### Bak 2: drip hydroponics in rockwol
#### De opstelling:

<div style="display: flex; justify-content: center; align-items: stretch; width: 100%; gap: 10px;">
  <div style="flex: 1; display: flex; justify-content: center;">
    <img src="{{ site.baseurl }}/assets/img/Plantenbak/pb2_front.png" alt="PCB Front" style="height: 300px; width: auto; object-fit: contain;">
  </div>
  <div style="flex: 1; display: flex; justify-content: center;">
    <img src="{{ site.baseurl }}/assets/img/Plantenbak/pb_back.png" alt="PCB Back" style="height: 250px; width: auto; object-fit: contain;">
  </div>
</div>
