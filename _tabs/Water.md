---
# the default layout is 'page'
icon: fas fa-droplet
order: 2
---

> Under construction
{: .prompt-warning }

## Inhoud
<!--x
1. [Introductie](#introductie)
2. [Toevoer](#toevoer)
   - [Reservoirs](#reservoirs)
   - [Pompsysteem](#pompsysteem)
   - [Lades](#lades)
3. [Afvoer](#afvoer)
4. [Stuurlogica](#stuurlogica)
   - [PCB](#pcb)
   Software
   - [Pompaansturing](#pompaansturing)
   - [UV-C](#uv-c)
5. [Componenten en keuzes](#componenten-en-keuzes)
   - [Reservoirs](#reservoirs-1)
   - [Tubes](#tubes)
   - [Quick connectors tubes](#quick-connectors-tubes)
   - [Waterpomp](#waterpomp)
   Luchtpomp en luchtsteen
   Onderwaterpomp
   Ultrasoon
   UV-C 2?
   Hallefect
   Probes
    ...
   --> 
   <!-- Gewacht met opmaak tot layout meer definitief is, nog aanpassen -->

## Introductie
Om plantjes te laten groeien zijn water en voedingsstoffen onmisbaar. In ons project staan wij in voor het aanvoeren en afvoeren van deze voedingsoplossing met de juiste kwaliteit. Dit gebeurt via een slim watersysteem dat instaat voor het mengen, verdelen en recupereren van het water.

Het watersysteem bestaat uit twee hoofdonderdelen:
- Watertoevoer en -afvoer
- Stuurlogica (elektronica)

Water en voedingsstoffen worden samengebracht in een mengreservoir. Van daaruit wordt het mengsel naar de plantlades gepompt, waar de planten het water kunnen opnemen. Het resterende water wordt vervolgens teruggevoerd naar het mengreservoir, zodat het opnieuw gebruikt kan worden.

In de volgende secties bespreken we elk onderdeel van dit systeem in meer detail.

## Componenten lijst
Hier vind u de benodigde componenten voor het deel water.
Voor de PCB bestukking: 
- Weerstanden:
    - 3× R_0805 (1.20×1.40 mm)
- Condensatoren:
    - 2× C_0805 (1.18×1.45 mm)
    - 1× CP_Elec_6.3×3.9 mm
    - 1× CP_EIA-3528-12_Kemet
- Diodes & LED’s:
    - 1× DIOM5226
    - 2× LED_0805 (1.15×1.40 mm)
- IC’s en modules:
    - 1× ESP32-WROOM-32D (microcontroller)
    - 1× MP1584 (step-down converter)
    - 1× AHQSS105DM2FA0G
    - 1× TSSOP-10
    - 1× SOT-223
    - 1× SOIC-28W
    - 1× SOT-23
- Mechanische onderdelen: 
    - 1× MountingHole 3.2 mm
    - 1× SolderJumper
    - 1× TestPoint
- Knoppen en schakelaars:
    - 2× Wurth Tactile Switch SPST-NO
- Headerpinnen:
    - 5× PinHeader 1x04
    - 3× PinHeader 1x03
    - 4× PinHeader 1x02
    - 1× PinHeader 1x06
- Connectoren:
    - 6× TerminalBlock Phoenix 1x02 (horizontaal)
    - 4× BNC_Amphenol_B6252HB (horizontaal)
Toevoer: 
- 3x reservoir
- 4x waterpomp 
- 2x luchtpompen + luchtsteen + t-stuk
- 1x aquariumpomp
- 7m watersalng Ø8mm
- xm waterslang Ø3.5mm
- 8x klemringen
- xx quick connectors (ppf) 2 zijdig
- 5x quick connectros (ppf) dicht
Afvoer: 
- 1x pvc buis van Ø90 2m30 
- 1x pvc buis van Øx x m 
- 1x koppelstuk 45° Ø90
Controle: 
- 1x probe pH
- 1x probe NO3-
- 1x probe Ca2+
- 1x probe K+
- 1x referentie probe
- 3x ultrasonesensor 
- 1x UVC
- 1x eindeloopschakelaar
- 2x ADC-module

## PCB 
<img src="{{ '/assets/img/Watersysteem/PCB-Watersysteem.png' | relative_url }}" alt="Afbeelding van de PCB" width="400" />

De PCB van het watersysteem moet een hele reeks inputs en digitale outputs verzorgen:
- Inputs
    - Chemische probes (analoog): 3 probes + 1 referentieprobe d.m.v. externe 16 bits ADC (I^2C)
    - PH-probe (digitaal)
    - Ultrasone hoogtesensoren (digitaal): 3 sensoren
    - Eindeloopschakelaars (digitaal): 1 sensor (we voorzagen 3 aansluitingen)
    - Stroommeting (analoog): 1 onboard ADC input
- Outputs
    - Status leds: 2 leds   
    - Onboard led voor debuggen: 1 led
    - UV-C lamp: 230V relais
    - Mixer: 5V relais
    - Luchtpomp: 12V relais
    - Waterpompen: 4 x 12V relais

We maakten gebruik van een IO-expander (MCP23017) die aan te sturen is via I^2C. Het uitlezen van de analoge probes vereist een ADC met hoge resolutie. Hiervoor maken we gebruik van een 16-bits ADC (ADS1115). Deze wordt ook uitgelezen via I^2C.
Voor het bijhouden van het energieverbruik maken we gebruik van een Hall-effect stroomsensor, verder besproken in Power.q

Meer informatie over de pcb, zoals het schema en de pin-out vind u [hier](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/PCB/). Het volledige ontwerp van de PCB is terug te vinden op onze [GitHub-pagina](https://github.com/Vertical-Farming-IB3/Plan-T/tree/main/Water/PCB).

### Software
<!--YAML niet zoals de rest in software plaatsen?-->
We maken gebruik van Home Assistant in combinatie met ESPHome. Op onze PCB staat code die gegenereert wordt via ESPHome. We beschrijven deze code in een [yaml-bestand](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/PCB/watersysteem.yaml).

Dankzij de koppeling met Home Assistant kunnen we zeer makkelijk iedere component uitlezen en aansturen. Het aansturen van de componenten gebeurt aan de hand van 'automatisaties'. Deze worden uitgevoerd op een lokale server die alle systemen zo samenbrengt. Het uitlezen van de data gebeurt ook via deze server. Deze data wordt dan samengebracht op een dashboard die de gebruiker kan raadplegen.

<!--Nog uitleg nodig voor gebruik van Dashboard?-->

## Toevoer
<img src="{{ '/assets/img/Watersysteem/Plan_Watersysteem.png' | relative_url }}" alt="Schematische tekening van het watersysteem" width="600" />

De watertoevoer is zo opgebouwd dat we twee voorraadtanks hebben: één met zuiver water en één met water vermengd met voedingsstoffen. We hebben bewust gekozen om de voedingsstoffen vooraf te mengen met water in het voorraadreservoir, omdat ze in geconcentreerde vorm zeer gevoelig zijn voor bacterievorming <!-- algenvorming-->. De fabrikant raadt aan om slechts één dopje per 10 liter te gebruiken, wat aantoont hoe krachtig het concentraat is.

Beide voorraadtanks zijn uitgerust met een luchtpomp, om de waterkwaliteit stabiel te houden en ongewenste biologische groei te voorkomen.<!--Samonella en algengroei--> Elk reservoir heeft ook zijn eigen pomp om het water of de voedingsoplossing naar het mengreservoir te transporteren. In dit mengreservoir worden de vloeistoffen samengebracht en gemixt. Hier zal ook de waterkwaliteit worden opgevolgd.

Vanuit dit centrale punt wordt het water via twee pompen verdeeld naar de plantlades. Aangezien er twee pompen aanwezig zijn, kunnen op dit moment twee lades tegelijk van water worden voorzien.
### Reservoirs:  

<img src="{{ '/assets/img/Watersysteem/reservoir.png' | relative_url }}" alt="Afbeelding van reservoir" width="400" />

Het watersysteem maakt gebruik van drie reservoirs: één voor zuiver water, één voor water met voedingsstoffen, en een mengreservoir waar de twee worden samengebracht. Elk reservoir heeft zijn eigen functie en zorgt ervoor dat de planten altijd het juiste water en voedingstoffen krijgen.

- Waterreservoir: Dit is het reservoir dat zuiver water bevat, zonder voedingsstoffen.
- Voedingsstofreservoir: Hierin zitten de voedingsstoffen in combinatie met water. De combinatie is er gekomen wegens een te hoge concentratie van de voedingsstoffen.
- Mengreservoir: Dit is het centrale reservoir waar het water en de voedingsstoffen samenkomen. Hier wordt alles gemengd en gecontroleerd op de juiste samenstelling, zodat de planten precies krijgen wat ze nodig hebben.

Elk voorraadreservoir is uitgerust met een luchtpomp die zorgt voor een goede circulatie van het water. Dit voorkomt dat er bacteriën of algen groeien, wat schadelijk kan zijn voor het systeem. Het mengreservoir heeft een aquarium pomp als mixer omdat deze krachtiger is. Daarnaast heeft elk reservoir een ultrasone sensor die het waterniveau meet, zodat je altijd weet hoeveel water er nog beschikbaar is.

De verwerking van de reservoirs binnen ons project is zo ontworpen dat het eenvoudig in en uit kunen geschoven worden. Dit om reiniging en bijvullen zo eenvoudig mogelijk te houden.

Hier zijn nog even kort de voordelen en nadelen: 

- **Voordelen:**   
    - Budgetvriendelijk
    - Eenvoudige integratie
    - Makkelijk uitneembaar
    - Goed te reinigen materiaal
    - Groot volume
- **Nadeel:**
    - Niet afsluitbaar, wat kan zorgen voor vuil in de reservoires.

### Tubes
De [tubes](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/onderdelen/slangen/waterslang-voor-onderwaterpomp-verticaal-horizontaal-3-6v-transparant-1-meter){:target="_blank"} hebben een diameter van 8 mm en zijn bedoeld voor het transport tussen de verschillende resrevoirs en naar de plantenbak.

Dankzij hun flexibiliteit zijn ze eenvoudig te installeren, zelfs op moeilijk bereikbare plaatsen.

Elke slang is gekoppeld met klemringen en quick connectors, zodat ze snel kunnen worden aangesloten en losgemaakt voor onderhoud of aanpassingen.

De verwerking van de tubes binnen ons project is ontworpen met het oog op modulariteit. Slangen kunnen eenvoudig vervangen of aangepast worden zonder dat het hele systeem moet worden opengebroken.

Hier zijn nog even kort de voordelen en nadelen:
- **Voordelen:**     
    - Flexibel
    - Transparant, wat controle van waterflow mogelijk maakt  
    - Compatibel met kleine pompen
    - eenvoudig op maat te knippen
    - Lichtgewicht 
    - budgetvriendelijk
- **Nadelen:**     
    - Niet geschikt voor hoge druk, geen probleem in ons geval
    - Kan knikken bij scherpe bochten
    - Niet UV-bestendig

### Quick connectors tubes
<img src="{{ '/assets/img/Watersysteem/connect.png' | relative_url }}" alt="Afbeelding van de connectors" width="400" />

De [Push-to-Connect koppelingen](https://nl.aliexpress.com/item/1005005808872752.html?spm=a2g0o.productlist.main.7.3edaJcT6JcT6q5&algo_pvid=3a7059ff-e7ee-43a2-b5fc-a499e4ff6cb3&algo_exp_id=3a7059ff-e7ee-43a2-b5fc-a499e4ff6cb3-3&pdp_ext_f=%7B%22order%22%3A%22400%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%212.75%210.97%21%21%212.81%210.99%21%402103864c17398869650571235ecd39%2112000034430185033%21sea%21BE%210%21ABX&curPageLogUid=4qEj3wATijZm&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"} worden gebruikt om verschillende buizen of componenten snel en stevig met elkaar te verbinden zonder gebruik van klemmen of lijm.

- **Voordelen:** 
    - Snelle installatie
    - Hergebruikbaar
    - Sterke afdichting 
    - Compact
    - Makkelijke modulariteit
- **Nadelen:** 
    - Slijt van de sluiting kan zorgen voor lekken over tijd
    - Kan loskomen bij slechte plug in 
    - Heeft een relatief complexe handeling nodig, voor het verplaatsen van lades

### Waterpomp: 
1. Twee pompen brengen water en voedingsstoffen vanuit hun respectievelijke reservoirs naar het mengreservoir.
2. Vanuit het mengreservoir transporteren aparte pompen de gemengde vloeistof naar de lades. In de kast is er voldoende ruimte voor twee laden met planten varierend in hoogte, om deze reden maken we gebruik van twee pompen voor de toevoer. Aan elke pomp kunnen darmpjes op verschillende hoogtes worden aangesloten, waardoor we een modulair systeem hebben gecreëerd dat eenvoudig uitbreidbaar en aanpasbaar is. De watertoevoer kan met quick-connectors aan de lades van plantenbak verbonden worden.

<img src="{{ '/assets/img/Watersysteem/Pompen_Aansluiting.jpg' | relative_url }}" alt="Afbeelding van aansluiting pomp" width="400" style="border-radius: 15px;" />

<img src="{{ '/assets/img/Watersysteem/Waterpomp.png' | relative_url }}" alt="Afbeelding van de waterpomp" width="400" />

De [waterpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/waterpomp-12v){:target="_blank"} heeft een maximale spanning van 12VDC en gebruikt ~400mA (=> P=4,8W). De pomp heeft een maximale opvoerhoogte van 3m en aanzuighoogte van 1,5m. Deze is geschikt voor slangen met ongeveer 8 mm binnendiameter. 
<!-- Energieberekening in Power, of bij elke component zetten? Is er dan een tab power nodig of word dit verwerkt in ieders eigen tab--> 

- **Voordelen:**
    - Relatief krachtig voor kleine systemen
    - Lage spanningsvereiste (veilig in gebruik)
    - Compact ontwerp, makkelijk te integreren
    - Eenvoudig aan te sluiten op 8 mm slang
- **Nadelen:**
    - Niet geschikt voor continu gebruik (kan oververhitten)
    - Beperkte compatibiliteit met dikkere slangen
    - Verbruikt relatief veel stroom bij batterijvoeding
<!-- De opgelijste voor- en nadelen van alle componenten lijkt nogal algemeen, niet toegespitst op onze toepassing--> 

### Luchtpomp en luchtsteen
<img src="{{ '/assets/img/Watersysteem/Luchtpomp+luchtsteen.png' | relative_url }}" alt="Afbeelding van de luchtpomp en luchtsteen" width="400" />

Voor het water- en voedingsstofreservoir werd een combinatie van een [luchtpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/luchtpomp-pyp370-12z-12v){:target="_blank"} met een [luchtsteen](https://nl.aliexpress.com/item/1005007443597285.html?spm=a2g0o.productlist.main.3.4a1049a6vx7Vpx&algo_pvid=de01e062-ea6d-400d-88c9-a07874e6f9d2&algo_exp_id=de01e062-ea6d-400d-88c9-a07874e6f9d2-1&pdp_ext_f=%7B%22order%22%3A%22312%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%212.05%210.97%21%21%2115.22%217.19%21%402103919917398752453552720ea209%2112000040774308148%21sea%21BE%210%21ABX&curPageLogUid=gjOskVCvOZWp&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"} gekozen om lucht in het water te brengen. Dit verhoogt het zuurstofgehalte en voorkomt de groei van algen.
<!-- Meer zuurstof bevorderd algengroei, de beweging van het water voorkomt algengroei, staat wel zo in voor- en nadelen--> 

- **Voordelen:**
    - Fijne luchtbellen: betere zuurstofverdeling
    - Voorkomt algenvorming in stilstaand water
    - Stil en energiezuinig systeem             <!-- Ik vond het niet zeer stil, kan ook aan de acoustic of trillingen id kast liggen--> 
    - Geen directe elektrische belasting in het water (veilig)

- **Nadelen:**
    - Luchtsteen kan verstopt raken
    - Luchtpomp is niet waterdicht
    - Beperkt vermogen voor grotere systemen
    - Luchtsteen is breekbaar
    - Extra zuurstof kan de algengroei bevorderen

### Onderwaterpomp
<img src="{{ '/assets/img/Watersysteem/Onderwaterpomp.png' | relative_url }}" alt="Afbeelding van de onderwaterpomp" width="400" />

Voor het mengreservoir werd een [onderwaterpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/onderwaterpomp-horizontaal-3-6v){:target="_blank"} gekozen om een krachtigere, turbulentere menging van het water en voedingstof te verkrijgen. 

- **Voordelen:**
    - Krachtige pomp voor snelle en efficiënte menging
    - Betrouwbaar bij constant gebruik in water
    - Compact en eenvoudig te integreren in een systeem
    - Geschikt voor zowel horizontale als verticale installaties
    - Energiezuinig

- **Nadelen:**
    - Beperkte capaciteit bij grotere watervolumes
    - Niet geschikt voor continue luchtpomping
    - Kan oververhit raken als de vloeistof te laag is
    - Vereist regelmatig onderhoud om verstoppingen te voorkomen

## Afvoer
De afvoer van water gebeurt op basis van zwaartekracht. De lade staat licht gekanteld, zodat overtollig water terugstroomt naar het mengreservoir. Hierdoor is er geen extra pomp nodig voor de afvoer. Om de kast te beschermen tegen waterschade wordt gebruikgemaakt van een centrale pvc-buis. De pvc-buis is deels open gesneden en voorzien van afdekkingen om spatten op te vangen. Op deze manier behouden we een hoge mate van modulariteit in het systeem.

<!--Nog aanpassen na bespreking-->
Het afgevoerde water wordt niet zomaar geloosd. In het mengreservoir wordt dit restwater gefilterd en gesteriliseerd (door een UV-C lamp en een fijnmazig gaasfilter). Nadien kan dit water opnieuw gebruikt worden, eventueel met bijmenging van vers water of extra voedingsstoffen. Dit maakt het systeem duurzaam en circulair, met minimale water- en nutriëntenverspilling.

## Stuurlogica


### Pompaansturing
De watercirculatie wordt op regelmatige tijdsintervallen geactiveerd om algengroei tegen te gaan. Algengroei ontstaat door stilstaand voedingstofrijk water, andere invloeden zijn de hoeveelheid water en de aanwezigheid van schaduw of licht. Het waterpijl van de reservoirs word gemonitord en aangevuld wanneer dit te laag komt te staan. Hiervoor wordt gebruik gemaakt van een ultrasone sensor. Deze sensoren werden simpelweg gekalibreerd door een meting te doen wanneer het reservoir leeg en vol is.
De lades worden voorzien van water wanneer zij dit nodig hebben, aan de hand van routines in de HomeAssistant. 





### Hallefect stroomsensor 
De stroommeeting gebeurt aan de hand van een Hall current sensor. Deze onderbreekt de stroom en meet aan de hand van een meetstroom geinduceerd door het hall effect de totale stroom. <!--snel geschreven-->

hall-effect-cs
<img src="{{ '/assets/img/Watersysteem/hall-effect-cs.jpg' | relative_url }}" alt="Hall effect" width="400" />

## controle
### Ultrasoon sensor
<img src="{{ '/assets/img/Watersysteem/Ultrasoon.png' | relative_url }}" alt="Afbeelding van de onderwaterpomp" width="400" />

De [ultrasoon sensor](https://www.tinytronics.nl/nl/sensoren/afstand/ultrasonische-afstandssensor-rcwl-1604){:target="_blank"} wordt gebruikt om de hoogte van de vloeistof in het reservoir te meten door middel van geluidsgolven. 

- **Voordelen:** 
    - Nauwkeurige meting van vloeistofniveaus
    - Geen direct contact met het water (minder slijtage) 
    - Eenvoudig te integreren in een systeem
    - Geschikt voor gebruik in diverse omgevingen (kan in verschillende vloeistoffen worden gebruikt)
    - Weinig onderhoud nodig

- **Nadelen:**  <!-- Kan interfereren met oneven wateroppervlak ...--> 
    - Kan gevoelig zijn voor interferentie van obstakels in de omgeving
    - Vereist een geschikte verwerking van het signaal voor juiste interpretatie
    - Beperkte nauwkeurigheid bij hoge luchttemperaturen of luchtstromingen

<!-- Moesten we voor Mevr. Van der Perre ook geen alternatieve opties bekijken?--> 


### UV-C
<img src="{{ '/assets/img/Watersysteem/UV_C.png' | relative_url }}" alt="Afbeelding van de UV_C" width="400" />

De [UV-C sterilisator](https://nl.aliexpress.com/item/1005006110975582.html?spm=a2g0o.detail.pcDetailBottomMoreOtherSeller.56.1dc5lUxFlUxFQM&gps-id=pcDetailBottomMoreOtherSeller&scm=1007.40050.354490.0&scm_id=1007.40050.354490.0&scm-url=1007.40050.354490.0&pvid=dc0bb433-8fde-4045-9085-4eecaa485c2d&_t=gps-id%3ApcDetailBottomMoreOtherSeller%2Cscm-url%3A1007.40050.354490.0%2Cpvid%3Adc0bb433-8fde-4045-9085-4eecaa485c2d%2Ctpp_buckets%3A668%232846%238108%231977&pdp_ext_f=%7B%22order%22%3A%2218%22%2C%22eval%22%3A%221%22%2C%22sceneId%22%3A%2230050%22%7D&pdp_npi=4%40dis!EUR!33.06!15.88!!!260.96!125.35!%40211b813b17443072665026527eba8d!12000038728939852!rec!BE!!ABX&utparam-url=scene%3ApcDetailBottomMoreOtherSeller%7Cquery_from%3A){:target="_blank"} wordt gebruikt om het water te desinfecteren met behulp van ultraviolet licht. <!-- Herhaling?--> Het UV-C licht breekt DNA-structuren van micro-organismen zoals algen, bacteriën en schimmels af. Hierdoor kunnen ze niet meer vermenigvuldigen. 

- **Voordelen:**
    - Effectieve en chemievrije watersterilisatie
    - Verlaagt de kans op algen- en biofilmvorming
    - Compact ontwerp, makkelijk te integreren
    - Continu gebruik mogelijk zonder extra onderhoudsproducten
- **Nadelen:**
    - Werkt enkel in helder water (verminderd effect bij troebelheid)
    - Beperkte levensduur van de UV-lamp (~8000 uur)
    - Kan gevaarlijk zijn bij directe blootstelling aan mens of dier (goede afscherming vereist)

### Probes
Elke plant heeft dezelfde voedingsstoffen nodig, deze voedingsstoffen zijn opgedeeld in verschillende klassen en zijn gekoppeld aan verschillende concentraties. De primaire voedingsstoffen zijn: Stikstof (N), Fosfor (P) en Kalium (K). Secundaire voedingsstoffen zijn Calcium (Ca), Magnesium (Mg) en Zwavel (S). En hiernaast zijn er ook nog vele micronutriënten. Om de waterkwaliteit in de gaten te houden maken we gebruik van probes (elektroden). We kunnen echter niet voor elk van deze voedingsstoffen een elektrode voorzien, daarom beperken we ons tot een deelset. We kozen voor het gebruik van:

* [Nitraat probe](https://www.alibaba.com/product-detail/Nitrate-Ion-selective-Electrode-NO3-ISE_60817798149.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cjuoxNt){:target="_blank"}
* [Kalium probe](https://www.alibaba.com/product-detail/ISE-K-Potassium-Ion-Selective-Electrode_1600225607843.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}
* [Calcium probe](https://www.alibaba.com/product-detail/PCa-1-01-Calcium-Ion-Selective_60659669573.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}

De reden waarom we het calciumgehalte opmeten en niet het fosforgehalte is omdat een probe voor het meten van fosfaten veel duurder is in vergelijking met de andere probes. De calcium probe is geïntegreerd omdat we stevige planten willen kweken in ons vertical farm. Daarnaast verwerkten we nog twee andere probes:

* [PH probe](https://nl.aliexpress.com/item/1005006063176996.html?spm=a2g0o.productlist.main.115.307031c2JATBrr&algo_pvid=62d5342a-588c-4537-a674-e9afbfd1070f&algo_exp_id=62d5342a-588c-4537-a674-e9afbfd1070f-57&pdp_ext_f=%7B%22order%22%3A%22313%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis!EUR!6.03!4.82!!!6.34!5.07!%40210385a817430803088781346eafba!12000035561276406!sea!BE!0!ABX&curPageLogUid=X6BxvMVVvpLV&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"}
* [Referentie probe](https://www.alibaba.com/product-detail/232-01-Reference-Electrode-Glass-Shell_60668853882.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}

De referentie probe is essentieeel voor het uitlezen van de overige probes. De PH-sensor is geïntegreerd omdat verschillende planten houden van een verschillende bodem zuurtegraad. Er is beslist om geen temperatuurprobe te integreren, we werken namelijk met een installatie binnenshuis, we veronderstellend dat de temperatuur relatief constant blijft. Daarnaast word de temperatuur in de kast gemeten, we zien dit als voldoende maatstaaf om de watertemperatuur te bepalen.

Dit maakt dat in totaal 5 probes zijn geïntegreerd. Deze probes worden gecallibreerd voor ze gebruikt kunnen worden, daarvoor zijn nog enkele componenten nodig, deze zullen we hieronder bespreken. De probes worden uitgelezen aan de hand van ADC-convertoren. De proben zijn temperatuurgevoelig, dit wil zeggen dat bij een verschillende watertemperatuur de probes verschillende meetwaarden kunnen teruggeven bij eenzelfde concentratie. Onze Vertical Farm bevind zich echter in een setting binnenshuis, we gaan er hierbij vanuit dat de temperatuurschommeling in de kast minimaal is. Hiernaast word de temperatuur bijgehouden in de plantenbak, deze meetwaarde is voldoende referentie om de probes af te stellen op temperatuurswijzigingen. <!-- Nakijken!!! Dit hebben we nog niet geverifieerd.-->

#### Kallibratie
Deze probes moeten gecallibreerd worden voor het correct uitmeten van de voedingsstoffen in het mengreservoir. Om deze kallibratie te kunnen uitvoeren zijn er vloeistoffen nodig met een gekende concentratie van de te meten nutriënten. We maken drie verschillende concentraties van deze stoffen om een driepuntskalibratie uit te voeren, dit geeft een nauwkeurige meting, waarop we ons verder kunnen baseren. Eerst maken we hiervoor enkele stockoplossingen die we vervolgens kunnen verdunnen om de gewenste kallibratievloeistoffen te bekomen. 

**Stockoplossingen**
We maken een aantal stockoplossingen, deze stockoplossingen zijn versterkte concentraties van zoutoplossingen voor het kalibreren van de elektroden, we zullen deze stockoplossingen volgens de juiste verhouding verdunnen. De stockoplossingen bevatten elk een aantal gewenste ionen, deze ionen worden gemeten door de elektroden waardoor we met deze bekende concentraties de elektroden juist kunnen afstemmen voor latere metingen.

_Gewenste stockoplossingen_

| Ion              | Kalibratie zout | Gewenste zout concentratie | Gewenste Ionen concentratie stockoplossing | Totaal volume van de oplossing | Absolute hoeveelheid zout |
| ---------------- | --------------- | -------------------------- | ------------------------------------------ | ------------------------------ | ------------------------- |
|                  |                 | [g/l]                      | [g/l]                                      | [ml]                           | [g]                       |
| NO3<sup>\-</sup> | NaNO3           | 21,9300                    | 16                                         | 100                            | 2,1930                    |
| Ca<sup>2+</sup>  | Ca(NO3)24H2O    | 11,7845                    | 2                                          | 100                            | 1,1785                    |
| K<sup>+</sup>    | KOH             | 2,8699                     | 2                                          | 200                            | 0,5740                    |

Omdat deze hoeveelheden in de praktijk te nauwkeurig zijn om exact af te meten, berekenen we de werkelijke ionenconcentratie na bereiding. De keuze van de stockoplossingen is gebeurd op basis van de beschikbaarheid van de aanwezige zouten en praktische overwegingen ten opzichte van de bereiding van de stockoplossingen. We maakten van elke stockoplossing 100 – 200 ml. Dit is een goede hoeveelheid voor een voldoende nauwkeurigheid en geeft ons voldoende stockoplossing voor alle kallibratievloeistoffen.

_Eigenlijke stockoplossingen_

| Ion              | Kalibratie zout | MM      | Totaal volume van de oplossing | Absolute hoeveelheid zout | Zout concentratie | Ionen concentratie stockoplossing |
| ---------------- | --------------- | ------- | ------------------------------ | ------------------------- | ----------------- | --------------------------------- |
|                  |                 | [g/mol] | [ml]                           | [g]                       | [g/l]             | [g/l]                             |
| NO3<sup>\-</sup> | NaNO3           | 84,9947 | 100                            | 2,1900                    | 21,900            | 15,9800                           |
| Ca<sup>2+</sup>  | Ca(NO3)24H2O    | 40,0780 | 100                            | 1,1786                    | 11,786            | 2,0000                            |
| K<sup>+</sup>    | KOH             | 56,1100 | 200                            | 0,5829                    | 2,9145            | 2,0300                            |

**Kalibratievloeistoffen**
Voor het kalibreren van de elektroden maken we gebruik van een driepuntsmeting, hiervoor maken we drie verschillende concentraties van de stockoplossing; een lage, medium en hoge concentratie. We meten vervolgens voor deze drie concentraties de probes (=elektroden) uit, waarna we een lineaire benadering kunnen trekken door deze drie punten. Op deze rechte kunnen we vervolgens met goede precisie onze probes kalibreren. Dit is nauwkeuriger dan een kallibratie met 1 meetpunt.

|                  | Low    | Medium | High   |
| ---------------- | ------ | ------ | ------ |
|                  | [mg/l] | [mg/l] | [mg/l] |
| NO3<sup>\-</sup> | 800    | 1200   | 1600   |
| Ca<sup>2+</sup>  | 100    | 200    | 400    |
| K<sup>+</sup>    | 100    | 200    | 400    |

**Referentie vloeistof**
De elektroden hebben ook een referentie nodig, hiervoor wordt een referentie probe gevuld met een bekende vloeistof. Dit is 3M KCl gesatureerd met AgCl. Deze oplossing kunnen we aankopen en hoeven we niet zelf te maken.

**Voedingsstoffen** 
We hebben ervoor gekozen om geen eigen voedingsstoffen samen te stellen voor het voeden van de planten, in de plaats daarvan kozen we voor een commerciële oplossing. We hebben hiervoor plantenvoeding gekocht. Deze plantenvoeding heef een NK waarde van  2.5-4. Deze waarde verwijst naar de verhouding van stikstof en kalium in de voedingsstof. In ons geval bevat de voeding 2.5% Stikstof, dit bevordert de bladgroei en algemene groei van de plant en 4% Kalium, dit versterkt de weerstand van de plant, bevordert de wortelontwikkeling en de bloei/vruchtvorming. Er staat geen fosfor vermeld, dit wil zeggen dat de gekozen plantenvoeding weinig tot geen fosfor bevat. Voor een betere opbrengst van de kast is het dus een goeie optie in een later stadium te kijken voor hogere kwaliteit voedingsstoffen. In de gebruikershandleiding staan ook aanbevolen verhoudingen voor verschillende soorten planten namelijk: kruiden ¼ dop per 2l, groenten 1 dop per 5l. Dit is een interessante verhouding om mee te nemen voor de  tuning van de vertical farm en de mogelijke verschillende gewassen.

**Kallibratie**

Zodra de drie concentraties voor een sensor zijn gemaakt, vindt de 3-puntskalibratie plaats. De referentie-ISE en de stofspecifieke ISE worden achtereenvolgens in elk van de drie stofspecifieke concentraties geplaatst en de spanning wordt gemeten. 

| Ion  | Concentratie | Oplossing | Gemeten spanning |
| ---- | ------------ | --------- | ---------------- |
|      |              | [mg/l]    | [mV]             |
| NO₃⁻ | Low          | 799.0     | 18.0             |
| NO₃⁻ | Med          | 958.8     | 32.5             |
| NO₃⁻ | High         | 1598.0    | 46.5             |
| Ca²⁺ | Low          | 100.0     | 23.0             |
| Ca²⁺ | Med          | 200.0     | 28.0             |
| Ca²⁺ | High         | 400.0     | 33.0             |
| K⁺   | Low          | 101.5     | 91.0             |
| K⁺   | Med          | 203.0     | 106.0            |
| K⁺   | High         | 406.0     | 118.0            |
