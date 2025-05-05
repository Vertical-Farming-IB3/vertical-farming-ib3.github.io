<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Plantenbak Project</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />
  <style>
    body { 
      scroll-behavior: smooth; 
      background-color: #f3f4f6;
    }
    .sidebar { 
      position: sticky; 
      top: 1rem; 
    }
    .toc a { 
      transition: all 0.3s ease; 
    }
    .toc a:hover { 
      color: #10b981; 
      transform: translateX(5px); 
    }
    .glow-image {
      position: relative;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      border-radius: 0.5rem;
    }
    .glow-image:hover {
      transform: scale(1.03);
      box-shadow: 0 0 20px rgba(16, 185, 129, 0.6);
    }
    .glow-image::after {
      content: '';
      position: absolute;
      top: -3px;
      left: -3px;
      right: -3px;
      bottom: -3px;
      border: 2px solid transparent;
      border-radius: 0.5rem;
      pointer-events: none;
    }
    .glow-image:hover::after {
      animation: glow 1.5s infinite ease-in-out;
    }
    @keyframes glow {
      0% { border-color: rgba(16, 185, 129, 0.3); }
      50% { border-color: rgba(16, 185, 129, 0.9); }
      100% { border-color: rgba(16, 185, 129, 0.3); }
    }
    a:not(.toc a) {
      transition: color 0.3s ease;
    }
    a:not(.toc a):hover {
      color: #10b981;
    }
    img {
      max-width: 100%;
      height: auto;
    }
  </style>
</head>
<body>
  <div class="container mx-auto px-4 py-8 flex flex-col md:flex-row gap-8">
    <!-- Sidebar for Table of Contents -->
    <aside class="md:w-1/4 sidebar" data-aos="fade-right" data-aos-duration="800">
      <div class="bg-white p-6 rounded-lg shadow-lg">
        <h2 class="text-xl font-bold text-green-600 mb-4"><i class="fas fa-seedling mr-2"></i>Inhoud</h2>
        <ul class="toc space-y-2 text-sm">
          <li><a href="#de-bedoeling" class="text-gray-600 hover:text-green-500">De bedoeling</a></li>
          <li><a href="#benodigdheden" class="text-gray-600 hover:text-green-500">Benodigdheden</a>
            <ul class="pl-4 space-y-1">
              <li><a href="#elektronische-componenten" class="text-gray-500 hover:text-green-500">Elektronische componenten</a></li>
              <li><a href="#sensoren-en-actuatoren" class="text-gray-500 hover:text-green-500">Sensoren en actuatoren</a></li>
              <li><a href="#materialen" class="text-gray-500 hover:text-green-500">Materialen</a></li>
            </ul>
          </li>
          <li><a href="#planten" class="text-gray-600 hover:text-green-500">Planten</a></li>
          <li><a href="#pcbs" class="text-gray-600 hover:text-green-500">PCB's</a></li>
          <li><a href="#de-lades" class="text-gray-600 hover:text-green-500">De lades</a>
            <ul class="pl-4 space-y-1">
              <li><a href="#bak-1-flood--drain" class="text-gray-500 hover:text-green-500">Bak 1: Flood & Drain</a></li>
              <li><a href="#bak-2-drip-hydroponics-in-rockwol" class="text-gray-500 hover:text-green-500">Bak 2: Drip Hydroponics</a></li>
            </ul>
          </li>
          <li><a href="#code" class="text-gray-600 hover:text-green-500">Code</a></li>
        </ul>
      </div>
    </aside>
    <main class="md:w-3/4 bg-white p-8 rounded-lg shadow-lg">
      <header class="mb-8" data-aos="fade-up" data-aos-duration="800">
        <h1 class="text-4xl font-bold text-green-600 flex items-center">
          <i class="fas fa-seedling mr-3"></i>Plantenbak
        </h1>
        <p class="mt-2 text-yellow-600 bg-yellow-100 p-4 rounded-lg"><strong>Under construction</strong></p>
      </header>
      <section id="de-bedoeling" class="mb-12" data-aos="fade-up" data-aos-duration="800">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">De bedoeling</h2>
        <p class="text-gray-600 leading-relaxed">
          Onze slimme plantenbak is ontworpen om de groeiomstandigheden van planten optimaal te monitoren en automatisch te regelen. De PCB’s in elke lade hebben de volgende functionaliteiten:
        </p>
        <ul class="list-disc pl-6 mt-2 space-y-1 text-gray-600">
          <li>Uitlezen van het vochtgehalte van het substraat</li>
          <li>Meten van lichtintensiteit via een lichtsensor</li>
          <li>Uitlezen van temperatuur en CO₂-concentratie</li>
          <li>Aansturen van ventilatoren via relais</li>
          <li>Gebruik van NFC-tags om plantensoorten te herkennen</li>
          <li>Energieverbruik monitoren</li>
        </ul>
      </section>
      <section id="benodigdheden" class="mb-12" data-aos="fade-up" data-aos-duration="800">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">Benodigdheden</h2>
        <p class="text-gray-600 mb-4">Om onze slimme plantenbak te bouwen en te verbeteren, gebruiken we de volgende onderdelen en materialen:</p>
        <section id="elektronische-componenten" class="mb-8" data-aos="fade-up" data-aos-duration="800">
          <h3 class="text-xl font-semibold text-gray-700 mb-3">Elektronische componenten</h3>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="100">
            <h4 class="text-lg font-medium text-gray-800">ESP-WROOM-32</h4>
            <p class="text-gray-600">Deze microcontroller met Wi-Fi- en Bluetooth-functionaliteit is het brein van elke plantenbak...</p>
            <img src="assets/img/Plantenbak/esp.png" alt="ESP-WROOM-32" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="200">
            <h4 class="text-lg font-medium text-gray-800">NFC-tags</h4>
            <p class="text-gray-600">Voor identificatie en automatisering per plantensoort...</p>
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="300">
            <h4 class="text-lg font-medium text-gray-800">PCB</h4>
            <p class="text-gray-600">Per bak zit één PCB die alle componenten aanstuurt...</p>
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="400">
            <h4 class="text-lg font-medium text-gray-800">5V relais</h4>
            <p class="text-gray-600">Deze relais wordt gebruikt om de ventilatoren te schakelen...</p>
            <img src="assets/img/Plantenbak/5vrelais.png" alt="5V relais" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="500">
            <h4 class="text-lg font-medium text-gray-800">MP1584</h4>
            <p class="text-gray-600">DC-DC buck converter: 12V → 5V...</p>
            <img src="assets/img/Plantenbak/mp1584.png" alt="MP1584" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="600">
            <h4 class="text-lg font-medium text-gray-800">Dupont kabels</h4>
            <p class="text-gray-600">Voor verbindingen tussen componenten en PCB's...</p>
            <img src="assets/img/Plantenbak/dupont.png" alt="Dupont kabels" class="mt-2 w-full max-w-md glow-image">
          </div>
        </section>
        <section id="sensoren-en-actuatoren" class="mb-8" data-aos="fade-up" data-aos-duration="800">
          <h3 class="text-xl font-semibold text-gray-700 mb-3">Sensoren en actuatoren</h3>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="100">
            <h4 class="text-lg font-medium text-gray-800">Capacitive soil moisture sensor</h4>
            <p class="text-gray-600">Deze sensor meet het vochtgehalte van het substraat...</p>
            <img src="assets/img/Plantenbak/csms.png" alt="CSMS" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="200">
            <h4 class="text-lg font-medium text-gray-800">GY-SCD40 module</h4>
            <p class="text-gray-600">Dit component meet de CO₂-concentratie, luchtvochtigheid en temperatuur...</p>
            <img src="assets/img/Plantenbak/gyscd40.png" alt="GY-SCD40" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="300">
            <h4 class="text-lg font-medium text-gray-800">NFC-reader PN532</h4>
            <p class="text-gray-600">Voor interactie met NFC-tags...</p>
            <img src="assets/img/Plantenbak/pn532.png" alt="PN532" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="400">
            <h4 class="text-lg font-medium text-gray-800">BH1750 lichtsensor</h4>
            <p class="text-gray-600">Meet de lichtintensiteit in de kast...</p>
            <img src="assets/img/Plantenbak/bh1750.png" alt="BH1750" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="500">
            <h4 class="text-lg font-medium text-gray-800">Ventilatoren (12V)</h4>
            <p class="text-gray-600">Voor luchtcirculatie...</p>
            <img src="assets/img/Plantenbak/fans.png" alt="Ventilatoren" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="600">
            <h4 class="text-lg font-medium text-gray-800">ACS712 current sensor</h4>
            <p class="text-gray-600">Om het verbruik te berekenen...</p>
            <img src="assets/img/Plantenbak/acs712.png" alt="ACS712" class="mt-2 w-full max-w-md glow-image">
          </div>
        </section>
        <section id="materialen" class="mb-8" data-aos="fade-up" data-aos-duration="800">
          <h3 class="text-xl font-semibold text-gray-700 mb-3">Materialen</h3>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="100">
            <h4 class="text-lg font-medium text-gray-800">Regentonkraan</h4>
            <p class="text-gray-600">Dit kraantje wordt gebruikt om de afloop te regelen...</p>
            <img src="assets/img/Plantenbak/kraan.png" alt="Regentonkraan" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="200">
            <h4 class="text-lg font-medium text-gray-800">Rockwol</h4>
            <p class="text-gray-600">Wordt gebruikt als substraat voor de planten...</p>
            <img src="assets/img/Plantenbak/rockwol.png" alt="Rockwol" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="300">
            <h4 class="text-lg font-medium text-gray-800">Potjes</h4>
            <p class="text-gray-600">De plantjes kunnen hierin gehangen worden...</p>
            <img src="assets/img/Plantenbak/cups.png" alt="Potjes" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="400">
            <h4 class="text-lg font-medium text-gray-800">Kokosvezel</h4>
            <p class="text-gray-600">Alternatief groeimedium voor de planten...</p>
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="500">
            <h4 class="text-lg font-medium text-gray-800">Plantenvoeding</h4>
            <p class="text-gray-600">Essentiële voedingsstoffen voor gezonde plantengroei...</p>
            <img src="assets/img/Plantenbak/voedingsstof.png" alt="Plantenvoeding" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="600">
            <standards-compliant code that can be compiled from a GitHub Pages site, ensuring compatibility with static hosting.

<xaiArtifact artifact_id="37385dce-b99b-4695-ad73-16f086dc5307" artifact_version_id="2ee14859-1edc-40de-a627-af4bc78c2244" title="index.html" contentType="text/html">
<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Plantenbak Project</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />
  <style>
    body { 
      scroll-behavior: smooth; 
      background-color: #f3f4f6;
    }
    .sidebar { 
      position: sticky; 
      top: 1rem; 
    }
    .toc a { 
      transition: all 0.3s ease; 
    }
    .toc a:hover { 
      color: #10b981; 
      transform: translateX(5px); 
    }
    .glow-image {
      position: relative;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      border-radius: 0.5rem;
    }
    .glow-image:hover {
      transform: scale(1.03);
      box-shadow: 0 0 20px rgba(16, 185, 129, 0.6);
    }
    .glow-image::after {
      content: '';
      position: absolute;
      top: -3px;
      left: -3px;
      right: -3px;
      bottom: -3px;
      border: 2px solid transparent;
      border-radius: 0.5rem;
      pointer-events: none;
    }
    .glow-image:hover::after {
      animation: glow 1.5s infinite ease-in-out;
    }
    @keyframes glow {
      0% { border-color: rgba(16, 185, 129, 0.3); }
      50% { border-color: rgba(16, 185, 129, 0.9); }
      100% { border-color: rgba(16, 185, 129, 0.3); }
    }
    a:not(.toc a) {
      transition: color 0.3s ease;
    }
    a:not(.toc a):hover {
      color: #10b981;
    }
    img {
      max-width: 100%;
      height: auto;
    }
  </style>
</head>
<body>
  <div class="container mx-auto px-4 py-8 flex flex-col md:flex-row gap-8">
    <!-- Sidebar for Table of Contents -->
    <aside class="md:w-1/4 sidebar" data-aos="fade-right" data-aos-duration="800">
      <div class="bg-white p-6 rounded-lg shadow-lg">
        <h2 class="text-xl font-bold text-green-600 mb-4"><i class="fas fa-seedling mr-2"></i>Inhoud</h2>
        <ul class="toc space-y-2 text-sm">
          <li><a href="#de-bedoeling" class="text-gray-600 hover:text-green-500">De bedoeling</a></li>
          <li><a href="#benodigdheden" class="text-gray-600 hover:text-green-500">Benodigdheden</a>
            <ul class="pl-4 space-y-1">
              <li><a href="#elektronische-componenten" class="text-gray-500 hover:text-green-500">Elektronische componenten</a></li>
              <li><a href="#sensoren-en-actuatoren" class="text-gray-500 hover:text-green-500">Sensoren en actuatoren</a></li>
              <li><a href="#materialen" class="text-gray-500 hover:text-green-500">Materialen</a></li>
            </ul>
          </li>
          <li><a href="#planten" class="text-gray-600 hover:text-green-500">Planten</a></li>
          <li><a href="#pcbs" class="text-gray-600 hover:text-green-500">PCB's</a></li>
          <li><a href="#de-lades" class="text-gray-600 hover:text-green-500">De lades</a>
            <ul class="pl-4 space-y-1">
              <li><a href="#bak-1-flood--drain" class="text-gray-500 hover:text-green-500">Bak 1: Flood & Drain</a></li>
              <li><a href="#bak-2-drip-hydroponics-in-rockwol" class="text-gray-500 hover:text-green-500">Bak 2: Drip Hydroponics</a></li>
            </ul>
          </li>
          <li><a href="#code" class="text-gray-600 hover:text-green-500">Code</a></li>
        </ul>
      </div>
    </aside>
    <main class="md:w-3/4 bg-white p-8 rounded-lg shadow-lg">
      <header class="mb-8" data-aos="fade-up" data-aos-duration="800">
        <h1 class="text-4xl font-bold text-green-600 flex items-center">
          <i class="fas fa-seedling mr-3"></i>Plantenbak
        </h1>
        <p class="mt-2 text-yellow-600 bg-yellow-100 p-4 rounded-lg"><strong>Under construction</strong></p>
      </header>
      <section id="de-bedoeling" class="mb-12" data-aos="fade-up" data-aos-duration="800">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">De bedoeling</h2>
        <p class="text-gray-600 leading-relaxed">
          Onze slimme plantenbak is ontworpen om de groeiomstandigheden van planten optimaal te monitoren en automatisch te regelen. De PCB’s in elke lade hebben de volgende functionaliteiten:
        </p>
        <ul class="list-disc pl-6 mt-2 space-y-1 text-gray-600">
          <li>Uitlezen van het vochtgehalte van het substraat</li>
          <li>Meten van lichtintensiteit via een lichtsensor</li>
          <li>Uitlezen van temperatuur en CO₂-concentratie</li>
          <li>Aansturen van ventilatoren via relais</li>
          <li>Gebruik van NFC-tags om plantensoorten te herkennen</li>
          <li>Energieverbruik monitoren</li>
        </ul>
      </section>
      <section id="benodigdheden" class="mb-12" data-aos="fade-up" data-aos-duration="800">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">Benodigdheden</h2>
        <p class="text-gray-600 mb-4">Om onze slimme plantenbak te bouwen en te verbeteren, gebruiken we de volgende onderdelen en materialen:</p>
        <section id="elektronische-componenten" class="mb-8" data-aos="fade-up" data-aos-duration="800">
          <h3 class="text-xl font-semibold text-gray-700 mb-3">Elektronische componenten</h3>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="100">
            <h4 class="text-lg font-medium text-gray-800">ESP-WROOM-32</h4>
            <p class="text-gray-600">Deze microcontroller met Wi-Fi- en Bluetooth-functionaliteit is het brein van elke plantenbak...</p>
            <img src="assets/img/Plantenbak/esp.png" alt="ESP-WROOM-32" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="200">
            <h4 class="text-lg font-medium text-gray-800">NFC-tags</h4>
            <p class="text-gray-600">Voor identificatie en automatisering per plantensoort...</p>
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="300">
            <h4 class="text-lg font-medium text-gray-800">PCB</h4>
            <p class="text-gray-600">Per bak zit één PCB die alle componenten aanstuurt...</p>
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="400">
            <h4 class="text-lg font-medium text-gray-800">5V relais</h4>
            <p class="text-gray-600">Deze relais wordt gebruikt om de ventilatoren te schakelen...</p>
            <img src="assets/img/Plantenbak/5vrelais.png" alt="5V relais" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="500">
            <h4 class="text-lg font-medium text-gray-800">MP1584</h4>
            <p class="text-gray-600">DC-DC buck converter: 12V → 5V...</p>
            <img src="assets/img/Plantenbak/mp1584.png" alt="MP1584" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="600">
            <h4 class="text-lg font-medium text-gray-800">Dupont kabels</h4>
            <p class="text-gray-600">Voor verbindingen tussen componenten en PCB's...</p>
            <img src="assets/img/Plantenbak/dupont.png" alt="Dupont kabels" class="mt-2 w-full max-w-md glow-image">
          </div>
        </section>
        <section id="sensoren-en-actuatoren" class="mb-8" data-aos="fade-up" data-aos-duration="800">
          <h3 class="text-xl font-semibold text-gray-700 mb-3">Sensoren en actuatoren</h3>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="100">
            <h4 class="text-lg font-medium text-gray-800">Capacitive soil moisture sensor</h4>
            <p class="text-gray-600">Deze sensor meet het vochtgehalte van het substraat...</p>
            <img src="assets/img/Plantenbak/csms.png" alt="CSMS" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="200">
            <h4 class="text-lg font-medium text-gray-800">GY-SCD40 module</h4>
            <p class="text-gray-600">Dit component meet de CO₂-concentratie, luchtvochtigheid en temperatuur...</p>
            <img src="assets/img/Plantenbak/gyscd40.png" alt="GY-SCD40" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="300">
            <h4 class="text-lg font-medium text-gray-800">NFC-reader PN532</h4>
            <p class="text-gray-600">Voor interactie met NFC-tags...</p>
            <img src="assets/img/Plantenbak/pn532.png" alt="PN532" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="400">
            <h4 class="text-lg font-medium text-gray-800">BH1750 lichtsensor</h4>
            <p class="text-gray-600">Meet de lichtintensiteit in de kast...</p>
            <img src="assets/img/Plantenbak/bh1750.png" alt="BH1750" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="500">
            <h4 class="text-lg font-medium text-gray-800">Ventilatoren (12V)</h4>
            <p class="text-gray-600">Voor luchtcirculatie...</p>
            <img src="assets/img/Plantenbak/fans.png" alt="Ventilatoren" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="600">
            <h4 class="text-lg font-medium text-gray-800">ACS712 current sensor</h4>
            <p class="text-gray-600">Om het verbruik te berekenen...</p>
            <img src="assets/img/Plantenbak/acs712.png" alt="ACS712" class="mt-2 w-full max-w-md glow-image">
          </div>
        </section>
        <section id="materialen" class="mb-8" data-aos="fade-up" data-aos-duration="800">
          <h3 class="text-xl font-semibold text-gray-700 mb-3">Materialen</h3>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="100">
            <h4 class="text-lg font-medium text-gray-800">Regentonkraan</h4>
            <p class="text-gray-600">Dit kraantje wordt gebruikt om de afloop te regelen...</p>
            <img src="assets/img/Plantenbak/kraan.png" alt="Regentonkraan" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="200">
            <h4 class="text-lg font-medium text-gray-800">Rockwol</h4>
            <p class="text-gray-600">Wordt gebruikt als substraat voor de planten...</p>
            <img src="assets/img/Plantenbak/rockwol.png" alt="Rockwol" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="300">
            <h4 class="text-lg font-medium text-gray-800">Potjes</h4>
            <p class="text-gray-600">De plantjes kunnen hierin gehangen worden...</p>
            <img src="assets/img/Plantenbak/cups.png" alt="Potjes" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="400">
            <h4 class="text-lg font-medium text-gray-800">Kokosvezel</h4>
            <p class="text-gray-600">Alternatief groeimedium voor de planten...</p>
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="500">
            <h4 class="text-lg font-medium text-gray-800">Plantenvoeding</h4>
            <p class="text-gray-600">Essentiële voedingsstoffen voor gezonde plantengroei...</p>
            <img src="assets/img/Plantenbak/voedingsstof.png" alt="Plantenvoeding" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="600">
            <h4 class="text-lg font-medium text-gray-800">Hydrokorrels en Watjes</h4>
            <p class="text-gray-600">Om de plantjes vast te houden in de potjes...</p>
            <img src="assets/img/Plantenbak/hydrokorrel.png" alt="Hydrokorrels" class="mt-2 w-full max-w-md glow-image">
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="700">
            <h4 class="text-lg font-medium text-gray-800">Witte verf</h4>
            <p class="text-gray-600">Een witte binnenkast zorgt voor optimale reflectie...</p>
          </div>
          <div class="mb-6" data-aos="fade-up" data-aos-delay="800">
            <h4 class="text-lg font-medium text-gray-800">Consumables</h4>
            <p class="text-gray-600">Zoals schroeven, kabels, soldeermateriaal...</p>
          </div>
        </section>
      </section>
      <section id="planten" class="mb-12" data-aos="fade-up" data-aos-duration="800">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">Planten</h2>
        <p class="text-gray-600 mb-4">We kozen deze soorten:</p>
        <ul class="list-disc pl-6 space-y-1 text-gray-600">
          <li>Koriander ★★★</li>
          <li>Basilicum ★★</li>
          <li>Oregano ★</li>
          <li>Snijsla ★★★</li>
          <li>Munt ★</li>
        </ul>
        <p class="text-gray-600 mt-2">Volgens ons zijn dit handige, veelzijdige gewassen...</p>
      </section>
      <section id="pcbs" class="mb-12" data-aos="fade-up" data-aos-duration="800">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">PCB's</h2>
        <p class="text-gray-600 mb-4">Alle bestanden omtrent de PCB voor de plantenbakken bevinden zich in deze <a href="https://github.com/Vertical-Farming-IB3/Plan-T/tree/main/Plantenbak/PCB" target="_blank" class="text-green-600 hover:underline">GitHub</a>.</p>
        <iframe src="assets/html/ibom_plantenbak.html" class="w-full h-[600px] border-none rounded-lg shadow-md mb-4" data-aos="fade-up" data-aos-delay="100"></iframe>
        <div class="flex justify-center mb-4" data-aos="fade-up" data-aos-delay="200">
          <img src="assets/img/Plantenbak/pb2_front.png" alt="PCB Front" class="w-full max-w-4xl glow-image">
        </div>
        <div class="flex justify-center gap-4" data-aos="fade-up" data-aos-delay="300">
          <img src="assets/img/Plantenbak/pb_back.png" alt="PCB Back" class="h-64 glow-image">
          <img src="assets/img/Plantenbak/relais_pinout.png" alt="Relais Pinout" class="h-64 glow-image">
        </div>
      </section>
      <section id="de-lades" class="mb-12" data-aos="fade-up" data-aos-duration="800">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">De lades</h2>
        <p class="text-gray-600 mb-4">Een plantenbak bestaat uit twee grote onderdelen...</p>
        <p class="text-gray-600 mb-2">We werken met twee technieken:</p>
        <ul class="list-disc pl-6 space-y-1 text-gray-600">
          <li><strong>Drip hydroponics:</strong> Bij deze techniek wordt een voedingsoplossing langzaam en gecontroleerd druppelsgewijs over de wortels gedruppeld...</li>
          <li><strong>Flood & Drain:</strong> De groeibak wordt periodiek tijdelijk overstroomd...</li>
        </ul>
        <section id="bak-1-flood--drain" class="mt-8" data-aos="fade-up" data-aos-duration="800">
          <h3 class="text-xl font-semibold text-gray-700 mb-3">Bak 1: Flood & Drain</h3>
          <h4 class="text-lg font-medium text-gray-800">De opstelling:</h4>
          <p class="text-gray-600">Deze bak wordt volledig gevuld met water...</p>
          <img src="assets/img/Plantenbak/bak_water.png" alt="Bak met water" class="mt-2 w-full max-w-md glow-image">
        </section>
        <section id="bak-2-drip-hydroponics-in-rockwol" class="mt-8" data-aos="fade-up" data-aos-duration="800">
          <h3 class="text-xl font-semibold text-gray-700 mb-3">Bak 2: Drip Hydroponics in Rockwol</h3>
          <h4 class="text-lg font-medium text-gray-800">De opstelling:</h4>
          <p class="text-gray-600">Door deze buis loopt een flexibel buisje...</p>
        </section>
      </section>
      <section id="code" class="mb-12" data-aos="fade-up" data-aos-duration="800">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">Code</h2>
        <p class="text-gray-600">De code werd gemaakt via een <a href="https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Plantenbak/Software/Plantenbak.yaml" target="_blank" class="text-green-600 hover:underline">yaml</a> a.d.h.v. ESPHome.</p>
      </section>
    </main>
  </div>
  <script src="https://unpkg.com/aos@next/dist/aos.js"></script>
  <script>
    AOS.init();
  </script>
</body>
</html>
