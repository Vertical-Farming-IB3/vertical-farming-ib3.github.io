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
        position: sticky;
        top: 0;
        background: white;
        z-index: 100;
        padding: 10px 0;
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

    .tab-section {
        padding-top: 20px;
        scroll-margin-top: 80px; /* Adjust based on your header height */
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
    <li class="nav-item" data-target="section-bedoeling">De bedoeling</li>
    <li class="nav-item" data-target="section-benodigdheden">Benodigdheden</li>
    <li class="nav-item" data-target="section-pcb">PCB</li>
    <li class="nav-item" data-target="section-planten">Planten</li>
</ul>

<div id="section-bedoeling" class="tab-section">
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

<div id="section-benodigdheden" class="tab-section">
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

<div id="section-pcb" class="tab-section">
    <h2>PCB</h2>
    <div class="pcb-container">
        <img src="{{ site.baseurl }}/assets/img/pb_front.png" alt="PCB Front">
        <img src="{{ site.baseurl }}/assets/img/pb_back.png" alt="PCB Back">
    </div>
</div>

<div id="section-planten" class="tab-section">
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
document.addEventListener('DOMContentLoaded', function() {
    // Function to update active tab based on scroll position
    function updateActiveTab() {
        const sections = document.querySelectorAll('.tab-section');
        const navItems = document.querySelectorAll('.nav-item');
        
        let currentSection = '';
        
        sections.forEach(section => {
            const sectionTop = section.offsetTop;
            const sectionHeight = section.clientHeight;
            if (window.scrollY >= (sectionTop - 100)) {
                currentSection = section.id;
            }
        });
        
        navItems.forEach(item => {
            item.classList.remove('active');
            if (item.getAttribute('data-target') === currentSection) {
                item.classList.add('active');
            }
        });
    }
    
    // Add click event to all tab items
    document.querySelectorAll('.nav-tabs .nav-item').forEach(function(tab) {
        tab.addEventListener('click', function() {
            const targetId = this.getAttribute('data-target');
            const targetSection = document.getElementById(targetId);
            
            if (targetSection) {
                window.scrollTo({
                    top: targetSection.offsetTop - 80,
                    behavior: 'smooth'
                });
            }
        });
    });
    
    // Update active tab on scroll
    window.addEventListener('scroll', updateActiveTab);
    
    // Set initial active tab
    updateActiveTab();
});
</script>
