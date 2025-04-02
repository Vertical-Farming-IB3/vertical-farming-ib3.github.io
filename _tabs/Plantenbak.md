---
icon: fas fa-seedling
title: Plantenbak
order: 1
---

> Under construction
{: .prompt-warning }

Wij hadden voornamelijk twee taken: plantjes zaaien/verzorgen/planten en de PCB maken om de omgeving voor de plantjes te monitoren. Deze elektronica werd in samenwerking met team water in de bakken geïmplementeerd. Wij willen twee manieren van hydroponics testen in onze vertical farm: een bak met substraat (bv. rockwol) en een bak zonder substraat (plantjes in potjes rechtstreeks in water).

## De bedoeling
Onze bordjes moeten deze functionaliteit hebben
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
- **MP1584** – DC-DC buck converter: 12V -> 5V
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

## PCB
<div style="display: flex; justify-content: center; gap: 4px; align-items: center; text-align: center;">
    <img src="{{ site.baseurl }}/assets/img/pb_front.png" alt="PCB Front" style="width: 40%;">
    <img src="{{ site.baseurl }}/assets/img/pb_back.png" alt="PCB Back" style="width: 40%;">
</div>

<div>
    <ul class="nav nav-tabs" id="myTab" role="tablist">
        <li class="nav-item">
            <a class="nav-link active" id="tab1-tab" data-toggle="tab" href="#tab1" role="tab">Tab 1</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" id="tab2-tab" data-toggle="tab" href="#tab2" role="tab">Tab 2</a>
        </li>
    </ul>
    <div class="tab-content" id="myTabContent">
        <div class="tab-pane fade show active" id="tab1" role="tabpanel">
            <p>Inhoud voor Tab 1</p>
        </div>
        <div class="tab-pane fade" id="tab2" role="tabpanel">
            <p>Inhoud voor Tab 2</p>
        </div>
    </div>
</div>

<script>
    document.addEventListener("DOMContentLoaded", function () {
        var tabs = document.querySelectorAll("[data-toggle='tab']");
        tabs.forEach(tab => {
            tab.addEventListener("click", function (event) {
                event.preventDefault();
                document.querySelector(".nav-link.active").classList.remove("active");
                document.querySelector(".tab-pane.show.active").classList.remove("show", "active");
                this.classList.add("active");
                document.querySelector(this.getAttribute("href")).classList.add("show", "active");
            });
        });
    });
</script>

## Planten
We kozen deze soorten:
- Koriander
- Basilicum
- Oregano
- Snijsla
- Munt

Volgens ons zijn dit handige, veelzijdige gewassen om beschikbaar te hebben in de keuken. Ze zijn ook relatief makkelijk te groeien.


