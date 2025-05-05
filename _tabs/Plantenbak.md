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
   - [Sensoren en actuatoren](#sensoren-en-actuatoren)
   - [Materialen](#materialen)
3. [Planten](#planten)
4. [PCB's](#pcbs)
5. [De lades](#de-lades)
   - [Bak 1: flood & drain](#bak-1-flood--drain)
   - [Bak 2: drip hydroponics in rockwol](#bak-2-drip-hydroponics-in-rockwol)
6. [Code](#code)

## De bedoeling
Onze slimme plantenbak is ontworpen om de groeiomstandigheden van planten optimaal te monitoren en automatisch te regelen. De PCB’s in elke lade hebben de volgende functionaliteiten:

- Uitlezen van het vochtgehalte van het substraat
- Meten van lichtintensiteit via een lichtsensor
- Uitlezen van temperatuur en CO₂-concentratie
- Aansturen van ventilatoren via relais
- Gebruik van NFC-tags om plantensoorten te herkennen
- Energieverbruik monitoren

## Benodigdheden
Om onze slimme plantenbak te bouwen en te verbeteren, gebruiken we de volgende onderdelen en materialen:

## Elektronische componenten

### ESP-WROOM-32
Deze microcontroller met Wi-Fi- en Bluetooth-functionaliteit is het brein van elke plantenbak. Alle metingen van de verbonden sensoren worden hier op verwerkt, terwijl andere componenten worden aangestuurd. Deze wordt via ESPHome geprogrammeerd.

![ESP-WROOM-32](assets/img/Plantenbak/esp.png)

---

### NFC-tags
Voor identificatie en automatisering per plantensoort. NFC werd verkozen boven RFID, vooral omdat deze over en kortere afstand communiceert. Onze kaarthouder zit namelijk dicht bij de NFC-reader. Het is ook handig dat de NFC-tags geprogrammeerd én gelezen kunnen worden met een smartphone.

---

### PCB
Per bak zit één PCB die alle componenten aanstuurt. Op elke PCB zijn alle GPIO-pinnen naar buiten gebracht, dus uitbreidingen zijn nog mogelijk. Deze PCB's zijn ontworpen met KiCAD en geprint door PCBWay. Meer hier over bij de sectie PCB's.

---

### 5V relais
Deze relais wordt gebruikt om de ventilatoren te schakelen. Deze relais werd gekozen omdat ze een lage inschakelspanning hebben en dus makkelijk aan te sturen zijn met de ESP-WROOM-32. De relais zijn ook voorzien van een LED-indicator, zodat je kan zien of ze aan of uit zijn.

![5V relais](assets/img/Plantenbak/5vrelais.png)

---

### MP1584
DC-DC buck converter: 12V → 5V. Dit component werd gekozen om een tussenstap te maken: nu is er op elke PCB 12V, 5V en 3.3V beschikbaar. Dit is handig voor de ESP-WROOM-32, die werkt op 3.3V, maar ook voor de relais en andere componenten die werken op 5V of 12V. De MP1584 is een buck converter die een hoge efficiëntie heeft en weinig warmte genereert. Dit is belangrijk omdat de plantenbak in een afgesloten kast staat, waar de temperatuur kan oplopen.

![MP1584](assets/img/Plantenbak/mp1584.png)

---

### Dupont kabels
Voor verbindingen tussen componenten en PCB's. Deze kabels zijn handig omdat ze makkelijk te gebruiken zijn en geen soldeerwerk vereisen. Ze zijn ook flexibel en kunnen makkelijk worden aangepast aan de situatie. Dit is belangrijk omdat de plantenbak in een afgesloten kast staat, waar de ruimte beperkt is. De kabels dragen ook bij aan de modulaire opbouw van de plantenbak, waardoor het makkelijker is om componenten te vervangen, aan te passen of toe te voegen.

![Dupont kabels](assets/img/Plantenbak/dupont.png)

---

## Sensoren en actuatoren

### Capacitive soil moisture sensor
Deze sensor meet het vochtgehalte van het substraat via een analoge pin van de ESP. Dit is een capacitive sensor, wat betekent dat hij werkt op basis van de verandering in capaciteit van de sensor wanneer deze in contact komt met water. Dit is beter dan een resistieve sensor, omdat deze minder gevoelig is voor corrosie en dus langer meegaat. De PCB van sensor heeft een handige, puntige vorm die het mogelijk maakt om de sensor in de rockwol te steken. Een bijkomend voordeel is dat deze sensor al beschikbaar was door IB3 van vorig jaar, dus we hebben ze hergebruikt. Dit hergebruik van componenten draagt bij aan de duurzaamheid van ons project ♻️.

![CSMS](assets/img/Plantenbak/csms.png)

---

### GY-SCD40 module
Dit component meet de CO₂-concentratie, de luchtvochtigheid en de temperatuur van de omgeving. Het is een digitale sensor die werkt via I²C. Dit betekent dat hij makkelijk kan worden aangesloten op de ESP-WROOM-32. De sensor heeft een hoge nauwkeurigheid en een snelle responstijd dankzij de photoacoustic-sensing technologie, wat belangrijk is voor de plantenbak. De sensor is ook voorzien van een ingebouwde verwarmingselement, wat helpt om condensatie te voorkomen en de nauwkeurigheid van de metingen te verbeteren. Een klein nadeel van de sensor is dat deze een korte stabilisatietijd heeft van enkele seconden. Ook deze sensors waren al beschikbaar door IB3 van vorig jaar, dus we hebben ze hergebruikt ♻️.

![GY-SCD40](assets/img/Plantenbak/gyscd40.png)

---

### NFC-reader PN532
Voor interactie met NFC-tags, om per bak te weten welke plant er in de kast zit. Dit is om de kast zo automatisch mogelijk te maken. Als een NFC-tag gelezen wordt, weet de kast welke plant er in de bak zit en kan de routine specifiek voor die plant ingesteld worden. Dit is handig omdat verschillende planten verschillende behoeften hebben qua licht, water en voeding. We kozen voor de PN532, omdat deze al beschikbaar was, want ons weer een nieuwe bestelling bespaarde ♻️.

![PN532](assets/img/Plantenbak/pn532.png)

---

### BH1750 lichtsensor
Meet de lichtintensiteit in de kast, om te detecteren of er te veel of te weinig licht is voor de plantengroei. We kozen voor deze sensor wegens de hoge nauwkeurigheid en vooral ook het grote meetbereik. Dit is belangrijk omdat de plantenbak in een afgesloten kast staat, waar de lichtintensiteit kan variëren van donker naar héél fel. Deze sensor wordt gebruikt om te controleren of de planten correct en voldoende (of te veel) belicht worden.

![BH1750](assets/img/Plantenbak/bh1750.png)

---

### Ventilatoren (12V)
Voor luchtcirculatie, maar ook vooral om plantjes met sterkere en dikkere stengels te kweken. Ook deze ventilatoren waren al beschikbaar van vorig jaar ♻️.

![Ventilatoren](assets/img/Plantenbak/fans.png)

---

### ACS712 current sensor
Om het verbruik te berekenen aan de hand van de gemeten stroom die het bordje binnenkomt. Dit is een hall-effect sensor die werkt op basis van de verandering in magnetisch veld wanneer er stroom door de draad gaat. Dit is een goede keuze omdat deze sensor al beschikbaar was, wat ons weer een nieuwe bestelling bespaarde ♻️. De sensor heeft een hoge nauwkeurigheid en een snelle responstijd, wat belangrijk is voor het meten van het energieverbruik van de plantenbak.

![ACS712](assets/img/Plantenbak/acs712.png)


## Materialen

### Regentonkraan
Dit kraantje wordt gebruikt om de afloop van de ebb-and-flow bak te regelen. Deze oplossing werd gekozen omdat de solenoid valve van IB3 van vorig jaar niet werkte. Dit kraantje is een goedkope oplossing omdat het makkelijk te installeren is en goed genoeg werkt.

![Regentonkraan](assets/img/Plantenbak/kraan.png)

---

### Rockwol
Wordt gebruikt als substraat voor de planten in de drip-bak. Dit is een goed alternatief voor aarde omdat het een goede waterretentie heeft en de wortels van de planten goed kan ondersteunen. Rockwol is ook een duurzaam materiaal omdat het gemaakt is van basaltsteen, wat een overvloedig natuurlijk materiaal is. Een nadeel is dat het niet biologisch afbreekbaar is en dat het kan irriteren bij aanraking. Voor ons prototype nu is dit geen probleem, maar in de toekomst zou hier een gebruiksvriendelijker alternatief voor moeten gevonden worden, zoals kokosvezel of iets zoals steekschuim.

![Rockwol](assets/img/Plantenbak/rockwol.png)

---

### Potjes
De plantjes kunnen hier in gehangen worden om ze te laten groeien. De open potjes zorgen ervoor dat het water langs de wortels kan lopen.

![Potjes](assets/img/Plantenbak/cups.png)

---

### Kokosvezel
Alternatief groeimedium voor de planten in de drip-bak. Dit is een goed alternatief voor aarde omdat het een goede waterretentie heeft en de wortels van de planten goed kan ondersteunen. Kokosvezel is ook een duurzaam materiaal omdat het gemaakt is van kokosnootschalen, wat een overvloedig natuurlijk materiaal is. Het is ook biologisch afbreekbaar en kan worden gebruikt als meststof voor andere planten. Dit zou een goed alternatief zijn voor rockwol, maar het is moeilijker om de plantjes in de potjes te zetten, omdat het materiaal veel losser is dan rockwol. Dit is dus een goed alternatief voor de toekomst, maar voor ons prototype nu is rockwol een betere keuze. We hebben dit materiaal wel gebruikt om zaadjes in te zaaien om deze dan in de kast te verplanten.

---

### Plantenvoeding
Essentiële voedingsstoffen voor gezonde plantengroei. Deze kunnen aangekocht worden in zowat elke tuin/huis/doe-het-zelf winkel. We kozen voor een vloeibare voeding omdat deze makkelijker te doseren is. Dit is volgens ons de goedkoopste en makkelijkste manier om de planten op een goede manier te voeden. Een andere optie was om zelf de chemische stoffen te kopen en deze zelf te mengen, maar dit is veel moeilijker, minder gebruiksvriendelijker en uiteindelijk ook duurder.

![Plantenvoeding](assets/img/Plantenbak/voedingsstof.png)

---

### Hydrokorrels en Watjes
Omdat de plantjes niet zomaar los in het water kunnen hangen, werden er hydrokorrels en watjes gebruikt. Deze houden de plantjes vast in de potjes.

![Hydrokorrels](assets/img/Plantenbak/hydrokorrel.png)

---

### Witte verf
Een witte binnenkast zorgt voor optimale reflectie en lichtverdeling in de kast. Dit is belangrijk omdat de plantenbak in een afgesloten kast staat, waar de lichtintensiteit kan variëren. De witte verf zorgt ervoor dat het licht beter wordt verdeeld en dat de planten beter belicht worden. Dit is belangrijk voor de groei van de planten.

---

### Consumables
Zoals schroeven, kabels, soldeermateriaal, 3D-prints, silicone, enzovoort. Dit zijn materialen die we nodig hebben om de plantenbak in elkaar te zetten en te monteren.

---

## Planten {#planten}
We kozen deze soorten:

- Koriander ★★★
- Basilicum ★★
- Oregano ★
- Snijsla ★★★
- Munt ★

Volgens ons zijn dit handige, veelzijdige gewassen om beschikbaar te hebben in de keuken. Ze zijn ook relatief makkelijk te groeien. Hoe meer sterren (★), hoe makkelijker en sneller ze groeien.
We zaaiden deze in aarde, om de kleine plantjes dan later te verplanten in onze vertical farm. Het is beter om in de kast met een klein plantje te beginnen, dan met een zaadje.

## PCB's {#pcbs}
Alle bestanden omtrent de PCB voor de plantenbakken bevinden zich in deze [GitHub](https://github.com/Vertical-Farming-IB3/Plan-T/tree/main/Plantenbak/PCB){:target="_blank"}. 

<iframe src="{{ '/assets/html/ibom_plantenbak.html' | relative_url }}" width="100%" height="600px" sytle="border:none;"></iframe>

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



## De lades {#de-lades}

Een plantenbak bestaat uit twee grote onderdelen: een houten lade en een plastic eurobak. De houten lade schuif in de kast, om voor modulariteit te zorgen. De eurobak is de bak waar de planten in groeien. Deze staat schuin in de houten lade, zodat het water afloopt in de regenpijp achteraan de kast. Er werd voor eurobakken gekozen omdat deze goedkoop zijn en makkelijk te bewerken.

We werken met twee technieken:
- *Drip hydroponics (drip-systeem):* Bij deze techniek wordt een voedingsoplossing langzaam en gecontroleerd druppelsgewijs over de wortels van de planten gedruppeld. Dit zorgt ervoor dat de planten altijd toegang hebben tot voldoende water en voedingsstoffen, zonder dat het wortelgedeelte constant in water staat.

- *Flood & Drain (ebb & flow):* De groeibak wordt periodiek tijdelijk overstroomd met de voedingsoplossing, waarna deze weer terugloopt naar het reservoir. Tijdens de "flood"-fase worden de wortels volledig ondergedompeld, en tijdens de "drain"-fase krijgen ze zuurstof. Dit afwisselend patroon stimuleert wortelgezondheid en efficiënte opname van nutriënten.
  
Dit laat toe om beide technieken te testen en onderling te vergelijken.

### Bak 1: flood & drain {#bak-1-flood--drain}
#### De opstelling:

Deze bak wordt dus volledig gevuld met water, zodat de wortels van de planten volledig zijn ondergedompeld. Ter beveiliging is er een overloop gemaakt, zodat de bak nooit kan overlopen. De afloop van het water wordt geregeld met een regentonkraan. De potjes met plantjes in rusten op een rooster, gemaakt uit restjes hout. Zo kunnen de plantjes makkelijk in één beweging uit de bak gehaald worden.

<img src="/assets/img/Plantenbak/bak_water.png" alt="bak met water">

### Bak 2: drip hydroponics in rockwol {#bak-2-drip-hydroponics-in-rockwol}
#### De opstelling:

Door deze buis loopt er een flexibel buisje waar gaatjes in werden geprikt en die op het einde een stop heeft. Het buisje loopt door de rockwol en maakt deze dus vochtig wanneer er water door gepompt worden. 

## Code
De code werd gemaakt via een [yaml](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Plantenbak/Software/Plantenbak.yaml){:target="_blank"} a.d.h.v. ESPHome.




