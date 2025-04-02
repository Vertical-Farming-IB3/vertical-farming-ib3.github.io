---
icon: fas fa-seedling
title: Plantenbak
order: 1
---

> Under construction
{: .prompt-warning }

<style>
    .nav-tabs {
        display: flex;
        list-style: none;
        padding: 0;
        gap: 10px;
        margin-bottom: 20px;
    }

    .nav-tabs .nav-item {
        cursor: pointer;
        padding: 10px 15px;
        border: 1px solid #ccc;
        border-radius: 5px;
        background: #f8f9fa;
        transition: background 0.3s, color 0.3s;
    }

    .nav-tabs .nav-item.active {
        background: #007bff;
        color: white;
    }

    .section {
        padding-top: 20px;
    }

    .pcb-container {
        display: flex;
        justify-content: center;
        gap: 10px;
        align-items: center;
        text-align: center;
        margin-top: 20px;
    }

    .pcb-container img {
        width: 40%;
    }
</style>

<ul class="nav-tabs">
    <li class="nav-item active" onclick="scrollToSection('bedoeling', this)">De bedoeling</li>
    <li class="nav-item" onclick="scrollToSection('benodigdheden', this)">Benodigdheden</li>
    <li class="nav-item" onclick="scrollToSection('pcb', this)">PCB</li>
    <li class="nav-item" onclick="scrollToSection('planten', this)">Planten</li>
</ul>

<div class="section" id="bedoeling">
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

<div class="section" id="benodigdheden">
    <h2>Benodigdheden</h2>
    <p>Om onze slimme plantenbak te bouwen en te verbeteren, gebruiken we de volgende onderdelen en materialen:</p>

    <h3>Elektronische componenten</h3>
    <ul>
        <li><b>ESP-WROOM-32</b> – Microcontroller met Wi-Fi- en Bluetooth-functionaliteit</li>
        <li><b>Capacitive soil moisture sensor</b> – Meet het vochtgehalte van het substraat</li>
        <li><b>GY-SCD40 module</b> – Meet CO₂-concentratie</li>
        <li><b>NFC-reader PN532</b> – Voor interactie met NFC-tags</li>
        <li><b>NFC-tags</b> – Voor identificatie en automatisering per plantensoort</li>
        <li><b>PCB's</b> – Per bak één PCB</li>
        <li><b>BH1750 lichtsensor</b> – Meet de lichtintensiteit</li>
        <li><b>Ventilatoren (12V)</b> – Voor luchtcirculatie en koeling</li>
        <li><b>Relais SR5</b> – Om ventilatoren te schakelen</li>
        <li><b>MP1584</b> – DC-DC buck converter: 12V → 5V</li>
        <li><b>Dupont kabels</b> – Voor verbindingen met sensoren</li>
        <li><b>5V relais</b> – Om een ventiel te schakelen</li>
        <li><b>Power-monitoring bord</b> - Om het verbruik te meten</li>
    </ul>

    <h3>Materialen</h3>
    <ul>
        <li><b>Rockwol</b> – Substraat voor hydrocultuur</li>
        <li><b>Potjes</b> – Voor het kweken van planten</li>
        <li><b>Kokosvezel</b> – Alternatief groeimedium</li>
        <li><b>Plantenvoeding</b> – Essentiële voedingsstoffen voor gezonde plantengroei</li>
        <li><b>Bloempotjes</b> – Voor individuele planten in te zaaien</li>
        <li><b>Hydrokorrels</b> – Voor wateropslag en beluchting van de wortels</li>
        <li><b>Witte verf</b> - Witte binnenkast zorgt voor optimale reflectie en lichtverdeling</li>
    </ul>
</div>

<div class="section" id="pcb">
    <h2>PCB</h2>
    <div class="pcb-container">
        <img src="{{ site.baseurl }}/assets/img/pb_front.png" alt="PCB Front">
        <img src="{{ site.baseurl }}/assets/img/pb_back.png" alt="PCB Back">
    </div>
</div>

<div class="section" id="planten">
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

<script>
    function scrollToSection(id, element) {
        document.getElementById(id).scrollIntoView({ behavior: 'smooth' });

        // Update actieve tab
        document.querySelectorAll(".nav-item").forEach(tab => tab.classList.remove("active"));
        element.classList.add("active");
    }
</script>
