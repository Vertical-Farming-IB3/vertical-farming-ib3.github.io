---
icon: fas fa-seedling
title: Plantenbak
order: 1
---

> Under construction
{: .prompt-warning }

Wij hadden voornamelijk twee taken: plantjes zaaien/verzorgen/planten en de PCB maken om de omgeving voor de plantjes te monitoren. Deze elektronica werd in samenwerking met team water in de bakken geïmplementeerd. Wij willen twee manieren van hydroponics testen in onze vertical farm: een bak met substraat (bv. rockwol) en een bak zonder substraat (plantjes in potjes rechtstreeks in water).

<ul class="nav nav-tabs" id="contentTab" role="tablist">
    <li class="nav-item">
        <a class="nav-link active" id="bedoeling-tab" data-toggle="tab" href="#bedoeling" role="tab">De bedoeling</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" id="benodigdheden-tab" data-toggle="tab" href="#benodigdheden" role="tab">Benodigdheden</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" id="pcb-tab" data-toggle="tab" href="#pcb" role="tab">PCB</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" id="planten-tab" data-toggle="tab" href="#planten" role="tab">Planten</a>
    </li>
</ul>

<div class="tab-content" id="contentTabContent">
    <div class="tab-pane fade show active" id="bedoeling" role="tabpanel">
        <h2>De bedoeling</h2>
        <p>Onze bordjes moeten deze functionaliteit hebben:</p>
        <ul>
            <li>Vochtigheidsniveau van het substraat uitlezen</li>
            <li>Lichtsensor om hoeveelheid licht te meten</li>
            <li>Temperatuur en CO₂-concentratie uitlezen</li>
            <li>Ventilatoren bestuurbaar met relais</li>
            <li>Ventiel bestuurbaar met relais</li>
            <li>NFC-tags per plantensoort</li>
            <li>Verbruik monitoren</li>
        </ul>
    </div>

    <div class="tab-pane fade" id="benodigdheden" role="tabpanel">
        <h2>Benodigdheden</h2>
        <h3>Elektronische componenten</h3>
        <ul>
            <li><strong>ESP-WROOM-32</strong> – Microcontroller met Wi-Fi- en Bluetooth-functionaliteit</li>
            <li><strong>Capacitive soil moisture sensor</strong> – Meet het vochtgehalte van het substraat</li>
            <li><strong>GY-SCD40 module</strong> – Meet CO₂-concentratie</li>
            <li><strong>NFC-reader PN532</strong> – Voor interactie met NFC-tags</li>
            <li><strong>NFC-tags</strong> – Voor identificatie en automatisering per plantensoort</li>
            <li><strong>PCB's</strong> – Per bak één PCB</li>
            <li><strong>BH1750 lichtsensor</strong> – Meet de lichtintensiteit</li>
            <li><strong>Ventilatoren (12V)</strong> – Voor luchtcirculatie en koeling</li>
            <li><strong>Relais SR5</strong> – Om ventilatoren te schakelen</li>
            <li><strong>MP1584</strong> – DC-DC buck converter: 12V → 5V</li>
            <li><strong>Dupont kabels</strong> – Voor verbindingen met sensoren</li>
            <li><strong>5V relais</strong> – Om een ventiel te schakelen</li>
            <li><strong>Power-monitoring bord</strong> – Om het verbruik te meten</li>
        </ul>
        <h3>Materialen</h3>
        <ul>
            <li><strong>Rockwol</strong> – Substraat voor hydrocultuur</li>
            <li><strong>Potjes</strong> – Voor het kweken van planten</li>
            <li><strong>Kokosvezel</strong> – Alternatief groeimedium</li>
            <li><strong>Plantenvoeding</strong> – Essentiële voedingsstoffen voor gezonde plantengroei</li>
            <li><strong>Bloempotjes</strong> – Voor individuele planten in te zaaien</li>
            <li><strong>Hydrokorrels</strong> – Voor wateropslag en beluchting van de wortels</li>
            <li><strong>Witte verf</strong> – Witte binnenkast zorgt voor optimale reflectie en lichtverdeling</li>
        </ul>
    </div>

    <div class="tab-pane fade" id="pcb" role="tabpanel">
        <h2>PCB</h2>
        <div style="display: flex; justify-content: center; gap: 4px; align-items: center; text-align: center;">
            <img src="{{ site.baseurl }}/assets/img/pb_front.png" alt="PCB Front" style="width: 40%;">
            <img src="{{ site.baseurl }}/assets/img/pb_back.png" alt="PCB Back" style="width: 40%;">
        </div>
    </div>

    <div class="tab-pane fade" id="planten" role="tabpanel">
        <h2>Planten</h2>
        <p>We kozen deze soorten:</p>
        <ul>
            <li>Koriander</li>
            <li>Basilicum</li>
            <li>Oregano</li>
            <li>Snijsla</li>
            <li>Munt</li>
        </ul>
        <p>Volgens ons zijn dit handige, veelzijdige gewassen om beschikbaar te hebben in de keuken. Ze zijn ook relatief makkelijk te groeien.</p>
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
