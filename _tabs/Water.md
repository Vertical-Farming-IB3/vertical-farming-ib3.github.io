---
icon: fas fa-droplet
order: 2
---

## Inhoud

1. [Introductie](#introductie)
2. [Componentenlijst](#componentenlijst)
3. [Stuurlogica](#stuurlogica)
4. [Controle](#controle)
    - [Ultrasoonsensor](#ultrasoonsensor)
    - [UV-C](#uv-c)
    - [Eindloopschakelaar](#eindloopschakelaar)
    - [Probes](#probes)
5. [Toevoer](#toevoer)
    - [Reservoirs](#reservoirs)
    - [Tubes](#tubes)
    - [Quick connectors tubes](#quick-connectors-tubes)
    - [Pompaansturing](#pompaansturing)
        - [Waterpomp](#waterpomp)
        - [Luchtpomp en luchtsteen](#luchtpomp-en-luchtsteen)
        - [Onderwaterpomp](#onderwaterpomp)
6. [Afvoer](#afvoer)

## Introductie
Om plantjes te laten groeien zijn water en voedingsstoffen onmisbaar. Met Team water staan wij in voor het aanvoeren en afvoeren van deze voedingsoplossing met de juiste kwaliteit. Dit gebeurt via een slim watersysteem dat instaat voor het mengen, verdelen en recupereren van het water.

In de volgende secties bespreken we elk onderdeel van dit systeem in meer detail.

## Componentenlijst

Hier vindt u de benodigde componenten voor het Project, voor dit onderdeel kan u kijken bij sectie Team Water binnen de bestellijst.

📄 [Bestellijst (Excel)](https://vertical-farming-ib3.github.io/assets/files/BOM.xlsx)

## Stuurlogica

<img src="{{ '/assets/img/Watersysteem/PCB-Watersysteem.png' | relative_url }}" alt="Afbeelding van de PCB" width="400" />

<img src="{{ '/assets/img/Watersysteem/Connecties_PCB_Watersysteem.png' | relative_url }}" alt="Afbeelding van de PCB met connecties" width="1000" />

Het Printed Circuit Board (PCB) van het watersysteem moet een hele reeks inputs en digitale outputs verzorgen:
- Inputs
    - (Analoog)  Chemische probes: 3 probes + 1 referentieprobe d.m.v. externe 16 bit ADC (I<sup>2</sup>C)
    - (Analoog) PH-probe (met BNC-Controller)
    - (Digitaal) Ultrasone hoogtesensoren: 3 sensoren
    - (Digitaal) Eindeloopschakelaars: 1 sensor (we voorzagen 3 aansluitingen)
    - (Analoog)  Stroommeting: 1 onboard ADC-input
- Outputs
    - Status leds: 2 leds (1 package)
    - Onboard led voor debuggen: 1 led
    - UV-C lamp: 230V relais
    - Mixer: 5V relais
    - Luchtpomp: 12V relais
    - Waterpompen: 4 x 12V relais

We maakten gebruik van een IO-expander (MCP23017) die aan te sturen is via I<sup>2</sup>C. Het uitlezen van de analoge probes vereist een ADC met hoge resolutie. Hiervoor maken we gebruik van een 16-bit ADC (ADS1115), ook uitgelezen via I<sup>2</sup>C. Het bijhouden van het energieverbruik gebeurt met een Hall-effect stroomsensor, verder besproken in Power.

<iframe src="{{ '/assets/html/ibom_watersysteem.html' | relative_url }}" width="100%" height="600px" sytle="border:none;"></iframe>

Meer informatie over de PCB, zoals het schema en de pin-out vindt u [hier](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/PCB/){:target="_blank"}.

**Software** 

We maken gebruik van Home Assistant in combinatie met ESPHome. Op onze microcontroller staat code die gegenereerd wordt via ESPHome. We beschrijven deze code in een [YAML-bestand](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/PCB/watersysteem.yaml). Dankzij de koppeling met Home Assistant kunnen we zeer makkelijk iedere component uitlezen en aansturen. Het aansturen van de componenten gebeurt aan de hand van 'automatisaties'. De automatisaties en het uitlezen van de data gebeurt via een lokale server die alle systemen samenbrengt. Deze data wordt dan samengebracht op een dashboard die de gebruiker kan raadplegen.

## Controle
### Ultrasoonsensor
<img src="{{ '/assets/img/Watersysteem/Ultrasoon.png' | relative_url }}" alt="Afbeelding van de onderwaterpomp" width="400" />

De [ultrasoonsensor](https://www.tinytronics.nl/nl/sensoren/afstand/ultrasonische-afstandssensor-rcwl-1604){:target="_blank"} wordt gebruikt om de hoogte van het waterniveau in een reservoir te meten. Dit doet hij met behulp van geluidsgolven: de sensor zendt een ultrasone geluidspuls uit en meet de tijdsduur tot het signaal, na weerkaatsing door het wateroppervlak, terug wordt opgevangen. Op deze manier wordt de afstand tot het water berekend — zonder dat er fysiek contact nodig is.

We hebben voor deze sensor gekozen na verschillende overwegingen:
- Contactloos meten: dit voorkomt slijtage en problemen met het vuil worden van de sensor in het water.
- Analoge meting: dit maakt het mogelijk om de hoogte van het waterniveau te meten en niet alleen 'vol' of 'leeg'.
- Geschikt voor water en voedingsstoffen: hij werkt ook betrouwbaar als er voedingsstoffen in het water zijn opgelost.
- Voedingsspanning van 3.3V<sub>DC</sub> tot 5V<sub>DC</sub>: dit past binnen het bereik van ons systeem.
- Meetbereik van 2 tot 400 cm met een nauwkeurigheid van ongeveer 3 mm.
- Goede prijs-kwaliteitverhouding: de sensor is nauwkeurig en betaalbaar.

📄 [Research waterniveau](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/Research.md#waterniveau-sensor){:target="_blank"}

Dankzij deze eigenschappen bleek de ultrasone sensor een geschikte keuze voor onze toepassing.

In het kort lijsten we nog even de voor- en nadelen op:
- **Voordelen:** 
    - Nauwkeurige meting van vloeistofniveaus
    - Geen direct contact met het water (minder slijtage en onderhoud) 
    - Eenvoudig te integreren in het systeem
    - Geschikt voor gebruik in diverse omgevingen (kan in verschillende vloeistoffen worden gebruikt)
    - Weinig onderhoud nodig

- **Nadelen:** 
    - Kan interfereren met oneven wateroppervlak
    - Kan gevoelig zijn voor interferentie van obstakels in de omgeving
    - Vereist een geschikte verwerking van het signaal voor juiste interpretatie
    - Beperkte nauwkeurigheid bij hoge luchttemperaturen of luchtstromingen

### UV-C
<img src="{{ '/assets/img/Watersysteem/UV_C.png' | relative_url }}" alt="Afbeelding van de UV_C" width="400" />

De [UV-C sterilisator](https://nl.aliexpress.com/item/1005006110975582.html?spm=a2g0o.detail.pcDetailBottomMoreOtherSeller.56.1dc5lUxFlUxFQM&gps-id=pcDetailBottomMoreOtherSeller&scm=1007.40050.354490.0&scm_id=1007.40050.354490.0&scm-url=1007.40050.354490.0&pvid=dc0bb433-8fde-4045-9085-4eecaa485c2d&_t=gps-id%3ApcDetailBottomMoreOtherSeller%2Cscm-url%3A1007.40050.354490.0%2Cpvid%3Adc0bb433-8fde-4045-9085-4eecaa485c2d%2Ctpp_buckets%3A668%232846%238108%231977&pdp_ext_f=%7B%22order%22%3A%2218%22%2C%22eval%22%3A%221%22%2C%22sceneId%22%3A%2230050%22%7D&pdp_npi=4%40dis!EUR!33.06!15.88!!!260.96!125.35!%40211b813b17443072665026527eba8d!12000038728939852!rec!BE!!ABX&utparam-url=scene%3ApcDetailBottomMoreOtherSeller%7Cquery_from%3A){:target="_blank"} bevindt zich in het mengreservoir. In dit reservoir wordt het terugstromende water uit het systeem ontsmet, voordat het opnieuw naar de planten wordt gepompt. Op die manier blijft het water schoon en vrij van schadelijke micro-organismen.

De UV-C sterilisator werkt met ultraviolet licht van het type C (UV-C). Dit licht heeft een zeer korte golflengte en is krachtig genoeg om het DNA van micro-organismen zoals bacteriën, schimmels en algen te beschadigen. Door deze schade kunnen ze zich niet meer vermenigvuldigen, waardoor ze onschadelijk worden. In een gesloten systeem zoals bij een vertical farm is dit erg belangrijk. Zonder UV-C zouden bacteriën of algen zich via het gerecupereerde water makkelijk kunnen verspreiden, wat schadelijk kan zijn voor de planten.

Let wel op: UV-C verwijdert geen vuildeeltjes of zichtbare vervuiling uit het water. Het maakt het water wel microbiologisch schoon.

- **Voordelen:**
    - Effectieve en chemievrije watersterilisatie
    - Verlaagt de kans op algen- en biofilmvorming
    - Compact ontwerp, makkelijk te integreren
    - Continu gebruik mogelijk zonder extra onderhoudsproducten
- **Nadelen:**
    - Werkt enkel in helder water (verminderd effect bij troebelheid)
    - Beperkte levensduur van de UV-lamp (~8000 uur)
    - Kan gevaarlijk zijn bij directe blootstelling aan mens of dier (goede afscherming vereist)

Ook voor dit systeem zijn meerdere opties bekeken, 1 daarvan is een systeem waarbij het water pas werd ontsmet vlak voordat het naar de plantjes stroomde. Dit zou echter de groei van algen in het reservoir zelf niet voorkomen, omdat het water daar dan nog niet behandeld was. 

De huidige UV-C lamp is gekozen om zijn voldoende vermogen om het nutrientrijke water te ontsmetten, en omdat ze compact genoeg is om in het waterreservoir te plaatsen. Op deze manier kan het water in de mengbak zonder veel extra componenten blootgesteld worden aan het UV-C licht.

📄 [Research ontsmetting](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/Research.md#ontsmetten-van-mixreservoir){:target="_blank"}

### Eindloopschakelaar
<img src="{{ '/assets/img/Watersysteem/Eindloop.png' | relative_url }}" alt="Eindloop" width="400" />

Er is een [eindloopschakelaar](https://www.hobbyelectronica.nl/product/3d-printer-endstop-mechanisch-ramps-1-4/){:target="_blank"} geïmplementeerd om te detecteren of de deur van de Vertical farm open of dicht is. Op deze manier kan de UV-C en sterk licht bijvoorbeeld uitgeschakeld worden bij het openen van de deur, dit voorkomt mogelijk ongemak. Een andere applicatie is het uitschakelen van de pompen, zodat als een la wordt uitgetrokken er geen water in de kast wordt gepompt.

### Probes
Elke plant heeft dezelfde voedingsstoffen nodig (in verschillende hoeveelheden), deze voedingsstoffen zijn opgedeeld in verschillende klassen en zijn gekoppeld aan verschillende concentraties. De primaire voedingsstoffen zijn: Stikstof (N), Fosfor (P) en Kalium (K). Secundaire voedingsstoffen zijn Calcium (Ca), Magnesium (Mg) en Zwavel (S). Hiernaast zijn er ook nog vele micronutriënten. Om de waterkwaliteit in de gaten te houden maken we gebruik van probes (elektroden). We kunnen echter niet voor elk van deze voedingsstoffen een elektrode voorzien, daarom beperken we ons tot een deelset. We kozen voor het gebruik van:

* [Nitraatprobe](https://www.alibaba.com/product-detail/Nitrate-Ion-selective-Electrode-NO3-ISE_60817798149.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cjuoxNt){:target="_blank"}
* [Kaliumprobe](https://www.alibaba.com/product-detail/ISE-K-Potassium-Ion-Selective-Electrode_1600225607843.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}
* [Calciumprobe](https://www.alibaba.com/product-detail/PCa-1-01-Calcium-Ion-Selective_60659669573.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}

<img src="{{ '/assets/img/Watersysteem/Nutrientenprobe.png' | relative_url }}" alt="Nutrientenprobe" width="400" />

De reden waarom we het calciumgehalte opmeten en niet het fosfaatgehalte is omdat een probe voor het meten van fosfaten veel duurder is in vergelijking met de andere probes. De calciumprobe is geïntegreerd omdat we stevige planten willen kweken in onze vertical farm. Daarnaast verwerkten we nog twee andere probes:

* [PH-probe](https://nl.aliexpress.com/item/1005006063176996.html?spm=a2g0o.productlist.main.115.307031c2JATBrr&algo_pvid=62d5342a-588c-4537-a674-e9afbfd1070f&algo_exp_id=62d5342a-588c-4537-a674-e9afbfd1070f-57&pdp_ext_f=%7B%22order%22%3A%22313%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis!EUR!6.03!4.82!!!6.34!5.07!%40210385a817430803088781346eafba!12000035561276406!sea!BE!0!ABX&curPageLogUid=X6BxvMVVvpLV&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"}
* [Referentieprobe](https://www.alibaba.com/product-detail/232-01-Reference-Electrode-Glass-Shell_60668853882.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}

<p><img src="{{ '/assets/img/Watersysteem/PH-probe.png' | relative_url }}" alt="PH-probe" width="400" /></p>
<p><img src="{{ '/assets/img/Watersysteem/RefProbe.png' | relative_url }}" alt="Referentieprobe" width="400" /></p>

Dit maakt dat in totaal 5 probes zijn geïntegreerd. De PH-sensor is geïntegreerd omdat verschillende planten houden van een verschillende zuurtegraad van de 'bodem'. De referentieprobe is essentieel voor het uitlezen van de overige probes, belangrijk hierbij is dat ze gevuld is met de juiste referentievloeistof. De overige probes worden gekalibreerd voor ze gebruikt kunnen worden, daarvoor zijn nog enkele componenten nodig, deze zullen we hieronder bespreken. De probes worden uitgelezen aan de hand van ADC-convertoren. De probes zijn temperatuurgevoelig, dit wil zeggen dat bij een verschillende watertemperatuur de probes verschillende meetwaarden kunnen teruggeven bij eenzelfde concentratie. Onze Vertical Farm bevindt zich echter in een omgeving binnenshuis, we gaan er hierbij vanuit dat de temperatuurschommeling in de kast minimaal is. Hiernaast wordt de temperatuur bijgehouden in de plantenbak, deze meetwaarde is voldoende referentie om de probes af te stellen op temperatuurswijzigingen. <!-- Nakijken!!! Dit hebben we nog niet geverifieerd.-->

- **Voordelen:**
    - Digitale uitlezing van de aanwezige voedingsstoffen
    - Vereist minder input van de user
    - Uitwisselbaar, indien in de toekomst bijvoorbeeld een fosfaatprobe geïntegreerd wordt
- **Nadelen:**
    - Vereist regelmatige kalibratie
    - Duurder (in vergelijking met manuele testen)
    - Temperatuursafhankelijk

📄 [Kalibratie Probes](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/Chemische_probes.md){:target="_blank"}

## Toevoer
<img src="{{ '/assets/img/Watersysteem/Plan_Watersysteem.png' | relative_url }}" alt="Schematische tekening van het watersysteem" width="600" />

De watertoevoer is zo opgebouwd dat we twee voorraadtanks hebben: één met zuiver water en één met water vermengd met voedingsstoffen. We hebben bewust gekozen om de voedingsstoffen vooraf te mengen met water in het voorraadreservoir, omdat ze in geconcentreerde vorm zeer gevoelig zijn voor bacterievorming <!-- algenvorming-->. De fabrikant raadt aan om slechts één dopje per 8 liter te gebruiken, wat aantoont hoe krachtig het concentraat is.

Beide voorraadtanks zijn uitgerust met een luchtpomp, om de waterkwaliteit stabiel te houden en ongewenste biologische groei te voorkomen.<!--Samonella en algengroei--> Elk reservoir heeft ook zijn eigen pomp om het water of de voedingsoplossing naar het mengreservoir te transporteren. In dit mengreservoir worden de vloeistoffen samengebracht en gemixt. Hier zal ook de waterkwaliteit worden opgevolgd.

Vanuit dit centrale punt wordt het water via twee pompen verdeeld naar de plantlades. Aangezien er twee pompen aanwezig zijn, kunnen op dit moment twee lades tegelijk van water worden voorzien

### Reservoirs 
<img src="{{ '/assets/img/Watersysteem/reservoir.png' | relative_url }}" alt="Afbeelding van reservoir" width="400" />

Het watersysteem maakt gebruik van drie reservoirs van 8l. Elk reservoir heeft zijn eigen functie en zorgt ervoor dat de planten altijd de juiste voeding krijgen:

- Waterreservoir: Dit is het reservoir dat zuiver water bevat zonder voedingsstoffen.
- Voedingsstofreservoir: Hierin zitten de voedingsstoffen verdund in water. De voedingsstoffen worden al op voorhand verdund omdat deze anders een te hoge concentratie bevatten.
- Mengreservoir: Dit is het centrale reservoir waar het water en de voedingsstoffen samenkomen. Hier wordt alles gemengd en gecontroleerd op de juiste samenstelling, zodat de planten precies krijgen wat ze nodig hebben.

Elk voorraadreservoir is uitgerust met een luchtpomp die zorgt voor een goede circulatie van het water. Het mengreservoir heeft een aquarium pomp als mixer omdat deze krachtiger is. Daarnaast heeft elk reservoir een ultrasone sensor die het waterniveau meet, zodat je altijd weet hoeveel water er nog beschikbaar is. Elk reservoir heeft ook zijn eigen pomp om het water of de voedingsoplossing naar het mengreservoir te transporteren. Hier zal ook de waterkwaliteit worden opgevolgd. Vanuit dit centrale punt wordt het water via twee pompen verdeeld naar de plantlades. 

De verwerking van de reservoirs binnen ons project is zo ontworpen dat de ze vlot uitneembaar zijn. Dit om reiniging en bijvullen zo eenvoudig mogelijk te houden.

Hier bespreken we nog even kort de voor- en nadelen: 

- **Voordelen:**   
    - Budgetvriendelijk
    - Eenvoudige integratie
    - Makkelijk uitneembaar
    - Goed te reinigen materiaal
    - Voldoende groot volume
- **Nadeel:**
    - Niet afsluitbaar, wat kan zorgen voor vuil en andere verontreinigingen in de reservoires

### Tubes
De [tubes](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/onderdelen/slangen/waterslang-voor-onderwaterpomp-verticaal-horizontaal-3-6v-transparant-1-meter){:target="_blank"} hebben een buitendiameter van 8 mm en een binnendiameter van 6mm. Ze worden gebruikt voor het transport van vloeistoffen tussen de reservoirs en van het mengreservoir naar de plantenbakken. Dankzij hun flexibiliteit zijn ze eenvoudig te installeren, zelfs op moeilijk bereikbare plaatsen. Elke tube is gekoppeld met klemringen en/of quick connectors, zodat ze snel kunnen worden aangesloten en losgemaakt voor onderhoud of aanpassingen. De verwerking van de tubes binnen ons project is ontworpen met oog op modulariteit. Ze kunnen eenvoudig vervangen of aangepast worden zonder dat het hele systeem moet worden herzien.

Hier nog even kort de voor- en nadelen:
- **Voordelen:**     
    - Flexibel
    - Transparant, wat controle van waterflow mogelijk maakt  
    - Compatibel met onze pompen
    - Eenvoudig op maat te knippen
    - Lichtgewicht 
    - Budgetvriendelijk
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
    - Slijtage van de sluiting kan zorgen voor lekken over tijd
    - Kan loskomen bij slechte connectie 
    - Complexe handeling nodig bij het verplaatsen van lades

Naast de dubbele connectoren zijn er ook [Push-to-Connect koppelingen](https://nl.aliexpress.com/item/1005008183056175.html?spm=a2g0o.productlist.main.29.571d5MkA5MkAHS&algo_pvid=d2139a20-3428-4ac8-897a-c42b41f50638&algo_exp_id=d2139a20-3428-4ac8-897a-c42b41f50638-14&pdp_ext_f=%7B%22order%22%3A%22-1%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%210.12%210.10%21%21%210.91%210.77%21%40211b813f17416814965187952ec789%2112000044143372525%21sea%21BE%210%21ABX&curPageLogUid=UcEPGSpsQuQL&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"} om de buizen af te sluiten, deze worden gebruikt om waterdruk op te bouwen bij de drip irregation, en om leidingen af te sluiten wanneer niet in gebruik. Dit voorkomt lekken en het belanden van vuil in open leidingen. Dezelfde voor- en nadelen zijn geldig als bij de dubbele connector.

### Pompaansturing
De watercirculatie wordt op regelmatige tijdsintervallen geactiveerd om algengroei tegen te gaan. Om de pompen te beschermen, wordt het waterpeil van de reservoirs gemonitord en aangevuld wanneer dit te laag komt te staan. Zo zit er ook een veiligheid ingebouwd die voorkomt dat de pompen activeren wanneer het waterniveau te laag is. De lades worden voorzien van water wanneer zij dit nodig hebben, aan de hand van routines in de [Home Assistant](https://vertical-farming-ib3.github.io/Home-Assistant/){:target="_blank"}. 

#### Waterpomp: 
1. Twee pompen brengen water en voedingsstoffen vanuit hun respectievelijke reservoirs naar het mengreservoir.
2. Vanuit het mengreservoir transporteren aparte pompen de gemengde vloeistof naar de lades. In de kast is er voldoende ruimte voor twee laden met planten (variërend in hoogte). Om deze reden maken we gebruik van twee pompen voor de toevoer. Aan elke pomp kunnen darmpjes op verschillende hoogtes worden aangesloten, waardoor we een modulair systeem hebben gecreëerd dat eenvoudig uitbreidbaar en aanpasbaar is. De watertoevoer kan gemakkelijk met quick-connectors aan de lades van plantenbak verbonden worden.

<img src="{{ '/assets/img/Watersysteem/Pompen_Aansluiting.jpg' | relative_url }}" alt="Afbeelding van aansluiting pomp" width="400" style="border-radius: 15px;" />

<img src="{{ '/assets/img/Watersysteem/Waterpomp.png' | relative_url }}" alt="Afbeelding van de waterpomp" width="400" />

Er is gekozen voor deze specifieke pompen omdat ze de beste optie leken voor deze toepassing. Ze zijn sterk en snel genoeg voor onze applicatie met 3m opvoerhoogte; 1,5m aanzuighoogte en  een debiet van 1,8l/min. Ook werken ze op 12V en trekken ze een vermogen in overeenstemming met de specs, de keuze van de voedingsspanning wordt verder besproken in Power. De pompjes zijn relatief goedkoop in vergelijking met alternatieven en andere sites. Bijkomend zijn ze compact en compatibel met andere design keuzes.

#### Luchtpomp en luchtsteen
<img src="{{ '/assets/img/Watersysteem/Luchtpomp+luchtsteen.png' | relative_url }}" alt="Afbeelding van de luchtpomp en luchtsteen" width="400" />

Voor het water- en voedingsstofreservoir vindt een combinatie van een [luchtpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/luchtpomp-pyp370-12z-12v){:target="_blank"} met een [luchtsteen](https://nl.aliexpress.com/item/1005007443597285.html?spm=a2g0o.productlist.main.3.4a1049a6vx7Vpx&algo_pvid=de01e062-ea6d-400d-88c9-a07874e6f9d2&algo_exp_id=de01e062-ea6d-400d-88c9-a07874e6f9d2-1&pdp_ext_f=%7B%22order%22%3A%22312%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%212.05%210.97%21%21%2115.22%217.19%21%402103919917398752453552720ea209%2112000040774308148%21sea%21BE%210%21ABX&curPageLogUid=gjOskVCvOZWp&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"} plaats om lucht in het water te brengen. Toevoegen van zuurstof aan het water verhoogt de opname van nutriënten, verbetert de wortelontwikkeling en vermindert stress in de plant. Meer zuurstof bevordert echter algengroei, de beweging van het water veroorzaakt door de luchtpomp voorkomt ook algengroei. De groei van algen ontstaat namelijk door verschillende factoren zoals: te weinig stroming, hoge hoeveelheid voedingsstoffen in het water, hoge temperatuur en hoge hoeveelheid licht.

- **Voordelen:**
    - Fijne luchtbellen: betere zuurstofverdeling
    - Voorkomt algenvorming in stilstaand water
    - Energiezuinig systeem
    - Geen directe elektrische belasting in het water (veilig)

- **Nadelen:**
    - Luchtsteen kan verstopt raken
    - Luchtpomp is niet waterdicht
    - Luchtsteen is breekbaar
    - Extra zuurstof kan de algengroei bevorderen 

#### Onderwaterpomp
<img src="{{ '/assets/img/Watersysteem/Onderwaterpomp.png' | relative_url }}" alt="Afbeelding van de onderwaterpomp" width="400" />

Voor het mengreservoir werd een [onderwaterpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/onderwaterpomp-horizontaal-3-6v){:target="_blank"} gekozen om een krachtige, turbulente menging van het water en voedingstoffen te verkrijgen. 

- **Voordelen:**
    - Krachtige pomp voor snelle en efficiënte menging
    - Betrouwbaar bij constant gebruik in water
    - Compact en eenvoudig te integreren in een systeem, geschikt voor zowel horizontale als verticale installatie
    - Energiezuinig

- **Nadelen:**
    - Beperkte capaciteit bij grotere watervolumes (schaalbaarheid)
    - Mag geen lucht aanzuigen, er moet dus een minimumniveau ingesteld worden dat hoger is dan normaal
    - Vereist regelmatig onderhoud om verstoppingen te voorkomen

📄 [Research mixen](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/Research.md#mixer){:target="_blank"}

## Afvoer

<img src="{{ '/assets/img/Watersysteem/Afvoer.png' | relative_url }}" alt="Afvoer" width="400" style="border-radius: 15px;" />

De afvoer van water gebeurt op basis van de zwaartekracht. De lade staat licht gekanteld, zodat overtollig water terugstroomt naar het mengreservoir. Hierdoor is er geen extra pomp nodig voor de afvoer. Om de kast te beschermen tegen waterschade wordt gebruikgemaakt van een centrale pvc-buis. De pvc-buis is deels open gesneden en voorzien van afdekkingen om spatten op te vangen. In deze opening kunnen de plantenbakken dan via een buisje gecontroleerd leeglopen. Als de lade uitgetrokken word willen we niet dat dit water door de kast loopt, om dit probleem op te lossen hebben we ook een module ontworpen met een gootje die onder de lade geschoven kan worden. Bij het uitrekken van de lade zal het water dan via dit gootje in de PVC-pijp belanden. Op deze manier behouden we een hoge mate van modulariteit in het systeem.

<img src="{{ '/assets/img/Watersysteem/Afvoergootje.png' | relative_url }}" alt="Afvoer" width="400" style="border-radius: 15px;" />

Het afgevoerde water wordt niet zomaar geloosd. In het mengreservoir wordt dit restwater gefilterd en gesteriliseerd (door een UV-C lamp en een fijnmazig filter). Nadien kan dit water opnieuw gebruikt worden, eventueel met bijmenging van vers water of extra voedingsstoffen. Dit maakt het systeem duurzaam en circulair, met minimale water- en nutriëntenverspilling.
