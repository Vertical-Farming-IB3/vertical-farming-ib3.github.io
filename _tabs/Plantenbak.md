---
icon: fas fa-seedling
title: Plantenbak
order: 1
---

## Inhoud 
1. [Introductie](#introductie)
2. [Componentenlijst](#componentenlijst)
3. [Stuurlogica](#stuurlogica)
4. [Lades](#lades)
   - [Bak 1: flood & drain](#bak-1-flood--drain)
   - [Bak 2: drip hydroponics in kokosvezel](#bak-2-drip-hydroponics-in-kokosvezel)
5. [Sensoren en actuatoren](#sensoren-en-actuatoren)
   - [Soil moisture sensor](#capacitive-soil-moisture-sensor)
   - [Lichtsensor](#bh1750-lichtsensor)
   - [Luchtsensor](#gy-scd40-module)
   - [Plantensoort herkenning](#nfc-reader-pn532)
   - [Energieverbruik monitoren](#acs712-current-sensor)
   - [Ventilatie](#ventilatie)
6. [Materialen](#materialen)
   - [Eurobak](#eurobak)
   - [Regentonkraan](#regentonkraan)
   - [Witte verf](#witte-verf)
   - [Kokosvezel](#kokosvezel)
   - [Plantenvoeding](#plantenvoeding)
   - [Potjes met hydrokorrels en sponsjes](#potjes-met-hydrokorrels-en-sponsjes)
   - [Consumables](#consumables)
7. [Planten](#planten)

---

## Introductie {#introductie}
Als deel van de vertical farm is de plantenbak ontworpen om de groeiomstandigheden van planten optimaal te monitoren. Met deze info kunnen de andere regelsystemen, licht en water, zich aanpassen aan de noden van de planten. Om dit te realiseren zijn volgende sensoren en functies aanwezig.

In de volgende secties bespreken we alle onderdelen van dit systeem in meer detail.

---

## Componentenlijst {#componentenlijst}
Hier vindt u de benodigde componenten voor het Project: voor dit onderdeel kan u kijken bij Team Plantenbak.

📄 [Bestellijst (Excel)](https://vertical-farming-ib3.github.io/assets/files/BOM.xlsx){:target="_blank"}

---

## Stuurlogica {#stuurlogica}
Hier volgt een opsomming van alle in- en outputs van de PCB:
- Inputs
    - (Analoog) [Soil moisture sensor](#capacitive-soil-moisture-sensor) 
    - (Digitaal) [Lichtsensor](#bh1750-lichtsensor)
    - (Digitaal) [Luchtsensor](#gy-scd40-module)
    - (Digitaal) [Plantensoort herkenning](#nfc-reader-pn532)
    - (Analoog) [Energieverbruik monitoren](#acs712-current-sensor)
- Outputs
    - Onboard led voor debuggen
    - [Ventilatie](#ventilatie): 5V relais

Per bak zit één PCB die alle componenten aanstuurt, met als 'brein' een ESP32. Op elke PCB zijn alle GPIO-pinnen naar buiten gebracht, zodat uitbreidingen mogelijk zijn. Deze PCB's zijn ontworpen met KiCAD en geprint door PCBWay. Meer hierover bij de sectie PCB's.

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

Meer informatie over de PCB, zoals het schema en de pin-out vindt u [hier](https://github.com/Vertical-Farming-IB3/Plan-T/tree/main/Plantenbak/PCB){:target="_blank"}.

**Software** 

We maken gebruik van Home Assistant in combinatie met ESPHome. Op onze microcontroller staat code die gegenereerd wordt via ESPHome. We beschrijven deze code in een [yaml-bestand](https://github.com/Vertical-Farming-IB3/Plan-T/tree/main/Plantenbak/Software/Plantenbak.yaml){:target="_blank"}. Dankzij de koppeling met Home Assistant kunnen we zeer makkelijk iedere component uitlezen en aansturen. Het aansturen van de componenten gebeurt aan de hand van 'automatisaties'. De automatisaties en het uitlezen van de data gebeurt via een lokale server die alle systemen samenbrengt. Deze data wordt dan samengebracht op een dashboard die de gebruiker kan raadplegen.

---

## Lades {#lades}
Een plantenbak bestaat voornamelijk uit twee onderdelen: een houten lade en een plastic eurobak. De houten lade schuift in de kast, om voor modulariteit te zorgen. De eurobak is de bak waar de planten in groeien. Deze is met een helling in de houten lade bevestigd zodat het water afloopt in de regenpijp achteraan de kast. Er werd voor eurobakken gekozen omdat deze goedkoop en makkelijk te bewerken zijn. In elke lade werd ook een 3D-print bevestigd om de PCB en componenten af te sluiten van de eurobakken. Deze kan [hier](https://github.com/Vertical-Farming-IB3/Plan-T/tree/main/Plantenbak/3D-modellen){:target="_blank"} gevonden worden.

Om de planten te kweken werken we met twee technieken:

•	Flood & Drain (ebb & flow): Hierbij wordt de groeibak periodiek tijdelijk overstroomd met de voedingsoplossing, waarna deze weer terugloopt naar het reservoir. Tijdens de “flood”-fase worden de wortels volledig ondergedompeld, en tijdens de “drain”-fase krijgen ze zuurstof. Dit afwisselend patroon stimuleert wortelgezondheid en efficiënte opname van nutriënten.

•	Drip hydroponics (drip-systeem): Hierbij wordt een voedingsoplossing langzaam en gecontroleerd druppelsgewijs over de wortels van de planten gedruppeld. Dit zorgt ervoor dat de planten altijd toegang hebben tot voldoende water en voedingsstoffen zonder dat er verspilling is.

Doordat we meerdere plantenbakken hebben kunnen we beide technieken testen en onderling vergelijken.

---

### Bak 1: flood & drain {#bak-1-flood--drain}
#### De opstelling:
Deze bak wordt volledig met water gevuld, zodat de wortels van de planten continu ondergedompeld blijven. Ter beveiliging is een overloopsysteem geïntegreerd, dit verhindert dat het waterniveau de rand overschrijdt. De waterafvoer wordt geregeld via een kraan, die een gecontroleerde afloop mogelijk maakt. De plantpotjes worden ondersteund door een rooster, gemaakt uit resthout, waardoor ze eenvoudig in één beweging uit de bak kunnen worden verwijderd. Deze bak heeft bovenaan een quick connector voor watertoevoer, die bevestigd werd met een snelbinder. Er moeten in de eurobak twee gaten gemaakt worden: een voor de overloop en een voor de afloop naar het kraantje. Voor de overloop kan een kort stukje pvc-buis of een 3D-print gebruikt worden. De overloop en de regentonkraan werden vastgemaakt en waterdicht gemaakt met lijm-/afdichtingskit. Er werd over beide gaten een netje gelijmd, zodat er enkel water weg kan.

<img src="/assets/img/Plantenbak/bak_eb_flow.png" alt="bak eb flow">

---

### Bak 2: drip hydroponics in kokosvezel {#bak-2-drip-hydroponics-in-kokosvezel}
#### De opstelling:
Doorheen deze plantenbak is een flexibel buisje aangebracht dat aan het uiteinde is afgesloten en op regelmatige afstand voorzien is van gaatjes. Dit buisje loopt door het substraat en zorgt voor een gelijkmatige bevochtiging wanneer er water doorheen gepompt wordt. Deze bak heeft ook boven een quick connector die bevestigd werd met een snelbinder. Hier moet maar één gat geboord worden voor de afloop. Daarin werd dan een pvc-buisje in bevestigd met een wartelmoer, en ook hier werd het terug verstevigd en waterdicht gemaakt met lijm-/bevestigingskit. Ook werd bij de uitloop een netje en een metalen raster geplaatst, om zo enkel water door te laten naar de afvoergoot.

<img src="/assets/img/Plantenbak/drip_bak.png" alt="drip bak">

---

## Sensoren en actuatoren {#sensoren-en-actuatoren}
Voor het kiezen van de sensoren onderzochten we enkele alternatieven. Ons opzoekwerk kan u hier terugvinden: 📄 [Research](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Plantenbak/research.md){:target="_blank"}

### Soil moisture sensor {#capacitive-soil-moisture-sensor}
Deze sensor meet het vochtgehalte van het substraat via een analoge pin van de ESP. Dit is een capacitieve sensor, wat betekent dat hij werkt op basis van de verandering in capaciteit van de sensor wanneer deze in contact komt met water. Dit is beter dan een resistieve sensor, omdat deze minder gevoelig is voor corrosie en dus langer meegaat. De PCB van sensor heeft een handige, puntige vorm die het mogelijk maakt om de sensor in de kokosvezel te steken. Een bijkomend voordeel is dat deze sensor al beschikbaar was door IB3 van vorig jaar, dus we hebben ze hergebruikt. Dit hergebruik van componenten draagt bij aan de duurzaamheid van ons project ♻️.

![CSMS](assets/img/Plantenbak/csms.png)

---

### Lichtsensor {#bh1750-lichtsensor}
Meet de lichtintensiteit in de kast, om te detecteren of er te veel of te weinig licht is voor de plantengroei. We kozen voor deze sensor wegens de hoge nauwkeurigheid en vooral ook het grote meetbereik. Dit is belangrijk omdat de plantenbak in een afgesloten kast staat, waar de lichtintensiteit kan variëren van donker naar héél fel. Deze sensor wordt gebruikt om te controleren of de planten correct en voldoende (of te veel) belicht worden.

![BH1750](assets/img/Plantenbak/bh1750.png)

---

### Luchtsensor {#gy-scd40-module}
Dit component meet de CO₂-concentratie, de luchtvochtigheid en de temperatuur van de omgeving. Het is een digitale sensor die werkt via I²C. Dit betekent dat hij makkelijk kan worden aangesloten op de ESP-WROOM-32. De sensor heeft een hoge nauwkeurigheid en een snelle responstijd dankzij de photoacoustic-sensing technologie, wat belangrijk is voor de plantenbak. De sensor is ook voorzien van een ingebouwde verwarmingselement, wat helpt om condensatie te voorkomen en de nauwkeurigheid van de metingen te verbeteren. Een klein nadeel van de sensor is dat deze een korte stabilisatietijd heeft van enkele seconden. Ook deze sensors waren al beschikbaar door IB3 van vorig jaar, dus we hebben ze hergebruikt ♻️.

![GY-SCD40](assets/img/Plantenbak/gyscd40.png)

---

### Plantensoort herkenning {#nfc-reader-pn532}
Dit gebeurt door interactie met NFC-tags, om per bak te weten welke plant er in de kast zit. Dit is om de kast zo automatisch mogelijk te maken. Als een NFC-tag gelezen wordt, weet de kast welke plant er in de bak zit en kan de routine specifiek voor die plant ingesteld worden. Dit is handig omdat verschillende planten verschillende behoeften hebben qua licht, water en voeding. We kozen voor de PN532, omdat deze al beschikbaar was, want ons weer een nieuwe bestelling bespaarde ♻️.

![PN532](assets/img/Plantenbak/pn532.png)

---

### Energieverbruik monitoren {#acs712-current-sensor}
Deze sensor is nodig om het verbruik te berekenen aan de hand van de gemeten stroom die het bordje binnenkomt. Dit is een hall-effect sensor die werkt op basis van de verandering in magnetisch veld wanneer er stroom door de draad gaat. Dit is een goede keuze omdat deze sensor al beschikbaar was, wat ons weer een nieuwe bestelling bespaarde ♻️. De sensor heeft een hoge nauwkeurigheid en een snelle responstijd, wat belangrijk is voor het meten van het energieverbruik van de plantenbak.

![ACS712](assets/img/Plantenbak/acs712.png)

---

### Ventilatie {#ventilatie}
Ventilatie is nodig voor luchtcirculatie, maar ook vooral om plantjes met sterkere en dikkere stengels te kweken. Ook deze ventilatoren waren al beschikbaar van vorig jaar ♻️.

![Ventilatoren](assets/img/Plantenbak/fans.png)

---

## Materialen {#materialen}
### Eurobak {#eurobak}
Deze bakken zijn goedkoop, waterdicht en makkelijk te bewerken. Het principe van een bak-in-een-bak (een eurobak in een lade) draagt bij tot de modulariteit.

---

### Regentonkraan {#regentonkraan}
Dit kraantje wordt gebruikt om de afloop van de ebb-and-flow bak te regelen. Deze oplossing werd gekozen omdat de solenoid valve van IB3 van vorig jaar niet werkte. Dit kraantje is een goedkope oplossing omdat het makkelijk te installeren is en goed genoeg werkt.

![Regentonkraan](assets/img/Plantenbak/kraan.png)

---

### Witte verf {#witte-verf}
Een witte binnenkast zorgt voor optimale reflectie en lichtverdeling in de kast. Dit is belangrijk omdat de plantenbak in een afgesloten kast staat, waar de lichtintensiteit kan variëren. De witte verf zorgt ervoor dat het licht beter wordt verdeeld en dat de planten beter belicht worden. Dit is belangrijk voor de groei van de planten.

---

### Kokosvezel {#kokosvezel}
Een goed biologisch groeimedium voor de planten in de drip-bak. Dit is een goed alternatief voor aarde omdat het een goede waterretentie heeft en de wortels van de planten goed kan ondersteunen. Kokosvezel is ook een duurzaam materiaal omdat het gemaakt is van kokosnootschalen, wat een overvloedig natuurlijk materiaal is. Het is ook biologisch afbreekbaar en kan worden gebruikt als meststof voor andere planten. Dit is een goed alternatief voor rockwol, omdat we daar last hadden van irritatie, te veel waterabsorptie en het was te vast voor de wortels om zich te kunnen nestelen. Kokosvezel was daarom een goede middenweg tussen aarde en rockwol.

![Kokosvezel](assets/img/Plantenbak/kokosvezel.png)

---

### Plantenvoeding {#plantenvoeding}
Essentiële voedingsstoffen voor gezonde plantengroei. Deze kunnen aangekocht worden in zowat elke tuin/huis/doe-het-zelf winkel. We kozen voor een vloeibare voeding omdat deze makkelijker te doseren is. Dit is volgens ons de goedkoopste en makkelijkste manier om de planten op een goede manier te voeden. Een andere optie was om zelf de chemische stoffen te kopen en deze zelf te mengen, maar dit is veel moeilijker, minder gebruiksvriendelijker en uiteindelijk ook duurder.

![Plantenvoeding](assets/img/Plantenbak/voedingsstof.png)

---

### Potjes met hydrokorrels en sponsjes {#potjes-met-hydrokorrels-en-sponsjes}
De plantjes kunnen hier in gehangen worden om ze te laten groeien. De open potjes zorgen ervoor dat het water langs de wortels kan lopen.

![Potjes](assets/img/Plantenbak/cups.png)

Omdat de plantjes niet zomaar los in het water kunnen hangen, werden er hydrokorrels en sponsjes gebruikt. Deze houden de plantjes vast in de potjes.

![Hydrokorrels](assets/img/Plantenbak/hydrokorrel.png)

---

### Consumables {#consumables}
Zoals schroeven, kabels, soldeermateriaal, 3D-prints, silicone, enzovoort. Dit zijn materialen die we nodig hebben om de plantenbak in elkaar te zetten en te monteren.

---

## Planten {#planten}
We kozen deze soorten:

- Koriander 
- Basilicum 
- Oregano 
- Snijsla 
- Munt
- Bieslook
- Peterselie

<table>
  <thead>
    <tr>
      <th>Plant</th>
      <th>Voordelen</th>
      <th>Nadelen</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Koriander <img src="/assets/img/Plantenbak/koriander.png" alt="Koriander" style="float:right; width:40px;"></td>
      <td>Snelle groei</td>
      <td>Wordt dun en lang: onstabiel<br>Gevoelig aan verplanten</td>
    </tr>
    <tr>
      <td>Basilicum <img src="/assets/img/Plantenbak/basil.png" alt="Basilicum" style="float:right; width:40px;"></td>
      <td>Groeit makkelijk<br>Stabiele plant</td>
      <td>Kan snel verwelken</td>
    </tr>
    <tr>
      <td>Oregano <img src="/assets/img/Plantenbak/oregano.png" alt="Oregano" style="float:right; width:40px;"></td>
      <td>Stabiele plant<br>Goed verplantbaar</td>
      <td>Langzame groei</td>
    </tr>
    <tr>
      <td>Snijsla <img src="/assets/img/Plantenbak/snijsla.png" alt="Snijsla" style="float:right; width:40px;"></td>
      <td>Erg snelle groei<br>Veel oogst per plant</td>
      <td>Gevoelig voor rot<br>Erg gevoelig aan verplanten</td>
    </tr>
    <tr>
      <td>Munt <img src="/assets/img/Plantenbak/munt.png" alt="Munt" style="float:right; width:40px;"></td>
      <td>Groeit goed eens ontkiemd<br>Sterke plant</td>
      <td>Woekert makkelijk<br>Ontkiemen duurt relatief lang</td>
    </tr>
    <tr>
      <td>Bieslook <img src="/assets/img/Plantenbak/bieslook.png" alt="Bieslook" style="float:right; width:40px;"></td>
      <td>Makkelijk te verplanten</td>
      <td>Langzame kieming</td>
    </tr>
    <tr>
      <td>Peterselie <img src="/assets/img/Plantenbak/peterselie.png" alt="Peterselie" style="float:right; width:40px;"></td>
      <td>Kan lang blijven groeien</td>
      <td>Traag kiemproces<br>Wordt lang en dun</td>
    </tr>
  </tbody>
</table>
