---
icon: fas fa-droplet
order: 2
---

> Under construction
{: .prompt-warning }

## Inhoud

1. [Introductie](#introductie)
2. [Toevoer](#toevoer)
    - [Reservoirs](#reservoirs)
    - [Tubes](#tubes)
    - [Quick connectors](#quick-connectors)
    - [Waterpompen](#waterpompen)
3. [Afvoer](#afvoer)
4. [Water managment Systems](#water-managment-systems)
    - [PCB](#pcb)
    - [Hallefect stroomsensor](#hallefect-stroomsensor)
    - [Ultrasoon sensor](#ultrasoon-sensor)
    - [Luchtpomp en luchtsteen](#luchtpomp-en-luchtsteen)
    - [Onderwaterpomp](#onderwaterpomp)
    - [UV-C](#uv-c)
    - [Probes](#probes)

## Introductie

Water wordt samengebracht met voedingsstoffen in een mengreservoir. Na het mengen wordt het water naar de lades gepompt waar het door de plantjes kan opgenomen worden. Hierna keert het restwater terug naar het mixvat om gerecupereert te worden.

Het watersysteem bestaat uit twee hoofdonderdelen:
- Watertoevoer en afvoer
- Stuurlogica (elektronica)

We bespreken deze onderdelen verder in detail in volgende secties.

<img 
  src="{{ '/assets/img/Watersysteem/Plan_Watersysteem.png' | relative_url }}" 
  alt="Schematische tekening van het watersysteem" 
  width="600" 
  style="border-radius: 12px;"
/>

## Toevoer
### Reservoirs:  

<img src="{{ '/assets/img/Watersysteem/reservoir.png' | relative_url }}" alt="Afbeelding van reservoir" width="400" />

Het systeem bevat drie reservoirs, voor:
- Water
- Voedingsstoffen
- Mengen

Dit zijn de bloembakken gebruikt in het project van vorig project. Deze waren ruim genoeg, voor de gewenste hoeveelheid wateropslag (~3 x 11l), en konden eenvoudig geïntegreerd worden binnen ons ontwerp. 

- **Voordelen:**   
    - Budgetvriendelijk
    - Goede integratie, uitneembaar
    - Makkelijk te reinigen
- **Nadeel:**
    - Niet afsluitbaar 

De drie reservoirs zijn uitneembaar, wat het reinigen en bijvullen eenvoudig maakt. Elk reservoir is uitgerust met een ultrasone sensor voor het nauwkeurig meten van het vloeistofniveau. Om algengroei te voorkomen, wordt het water in de reservoirs continu gecirculeerd met behulp van luchtpompen en luchtstenen.

In het mengreservoir komt het water samen met de voedingsstoffen, een aquariumpomp zorgt hier voor het mengen en circuleren tot voedingstofrijk water. Daarnaast is dit reservoir voorzien van een UV-C lamp, als extra maatregel tegen micro-organismen en biologische verontreiniging, en bevat het de nodige chemische probes voor een optimale verhouding van voedingsstoffen.

### Tubes
De [tubes](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/onderdelen/slangen/waterslang-voor-onderwaterpomp-verticaal-horizontaal-3-6v-transparant-1-meter){:target="_blank"} hebben een diameter van 8 mm en zijn bedoeld voor het transport van water. 
 
- **Voordelen:**
    - Flexibel
    - Transparant, we kunnen de waterflow en mogelijke verstoppingen nakijken  
    - Lichtgewicht en makkelijk op maat te knippen
    - Voldoende watertoevoer in combinatie met de gekozen pompen
- **Nadelen:**     
    - Kan knikken of beschadigen bij scherpe bochten en randen
    - Niet UV-bestendig

De tubes zijn gekozen met meerdere doelen in gedachten, hiervoor was versatiliteit belangrijk, er is dan ook gekozen voor een flexibele kabel. De tube verbind de reservoirs laden en pompen.

### Quick connectors
<img src="{{ '/assets/img/Watersysteem/connect.png' | relative_url }}" alt="Afbeelding van de connectors" width="400" />

De [Push-to-Connect koppelingen](https://nl.aliexpress.com/item/1005005808872752.html?spm=a2g0o.productlist.main.7.3edaJcT6JcT6q5&algo_pvid=3a7059ff-e7ee-43a2-b5fc-a499e4ff6cb3&algo_exp_id=3a7059ff-e7ee-43a2-b5fc-a499e4ff6cb3-3&pdp_ext_f=%7B%22order%22%3A%22400%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%212.75%210.97%21%21%212.81%210.99%21%402103864c17398869650571235ecd39%2112000034430185033%21sea%21BE%210%21ABX&curPageLogUid=4qEj3wATijZm&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"} worden gebruikt om verschillende tubes of componenten snel en stevig met elkaar te verbinden zonder, de mogelijkheid tot het losmaken van deze verbindingen bied extra flexibiliteit. De Push-to-connect koppelingen zijn enorm interesant omdat ze veel veranderingen toelaten.

- **Voordelen:** 
    - Snelle installatie
    - Sterke afdichting
    - Compact
    => Makkelijke modulariteit
- **Nadelen:** 
    - Slijt van de sluiting en tube kan zorgen voor lekken over tijd
    - Kan loskomen bij slechte plug in 
    - Heeft een relatief complexe handeling nodig, voor het verplaatsen van lades

### Waterpompen

<img src="{{ '/assets/img/Watersysteem/Waterpomp.png' | relative_url }}" alt="Afbeelding van de waterpomp" width="400" />

De [waterpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/waterpomp-12v){:target="_blank"} heeft een maximale spanning van 12VDC en gebruikt ~400mA (=> P=4,8W). De pomp heeft een maximale opvoerhoogte van 3m en aanzuighoogte van 1,5m. Deze is geschikt voor slangen met ongeveer 8 mm binnendiameter. 
<!-- Energieberekening in Power, of bij elke component zetten? Is er dan een tab power nodig of word dit verwerkt in ieders eigen tab--> 

- **Voordelen:**
    - Krachtig genoeg voor onze toepassing
    - Lage spanningsvereiste (veilig in gebruik)
    - Compact ontwerp, makkelijk te integreren
- **Nadelen:**
    - Niet geschikt voor continu gebruik (kan oververhitten)

<img src="{{ '/assets/img/Watersysteem/Pompen_Aansluiting.jpg' | relative_url }}" alt="Afbeelding van aansluiting pomp" width="400" style="border-radius: 15px;" />

1. Twee pompen brengen water en voedingsstoffen vanuit hun respectievelijke reservoirs naar het mengreservoir.
2. Vanuit het mengreservoir transporteren aparte pompen de gemengde vloeistof naar de lades. In de kast is er voldoende ruimte voor twee laden met planten varierend in hoogte, om deze reden maken we gebruik van twee pompen voor de toevoer. Aan elke pomp kunnen darmpjes op verschillende hoogtes worden aangesloten, waardoor we een modulair systeem hebben gecreëerd dat eenvoudig uitbreidbaar en aanpasbaar is. De watertoevoer kan met quick-connectors aan de lades van team Plantenbak verbonden worden.

## Afvoer
De afvoer van water gebeurt op basis van zwaartekracht. De lade staat licht gekanteld, zodat overtollig water terugstroomt naar het mengreservoir. Hierdoor is er geen extra pomp nodig voor de afvoer. Om de kast te beschermen tegen waterschade wordt gebruikgemaakt van een centrale pvc-buis. De pvc-buis is deels open gesneden en voorzien van afdekkingen om spatten op te vangen. Op deze manier behouden we een hoge mate van modulariteit in het systeem.

Het afgevoerde water wordt niet zomaar geloosd. In het mengreservoir wordt dit restwater gefilterd en gesteriliseerd (door een UV-C lamp en een fijnmazig gaasfilter). Nadien kan dit water opnieuw gebruikt worden, eventueel met bijmenging van vers water of extra voedingsstoffen. Dit maakt het systeem duurzaam en circulair, met minimale water- en nutriëntenverspilling.

## Water managment Systems
### PCB 
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

**Software** 

<!--YAML niet zoals de rest in software plaatsen?-->
We maken gebruik van Home Assistant in combinatie met ESPHome. Op onze PCB staat code die gegenereert wordt via ESPHome. We beschrijven deze code in een [yaml-bestand](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/PCB/watersysteem.yaml).

Dankzij de koppeling met Home Assistant kunnen we zeer makkelijk iedere component uitlezen en aansturen. Het aansturen van de componenten gebeurt aan de hand van 'automatisaties'. Deze worden uitgevoerd op een lokale server die alle systemen zo samenbrengt. Het uitlezen van de data gebeurt ook via deze server. Deze data wordt dan samengebracht op een dashboard die de gebruiker kan raadplegen.

<!--Nog uitleg nodig voor gebruik van Dashboard?-->

### Hallefect stroomsensor 

<img src="{{ '/assets/img/Watersysteem/hall-effect-cs.jpg' | relative_url }}" alt="Hall effect" width="400" />

De stroommeeting gebeurt aan de hand van een Hall current sensor. Deze onderbreekt de stroom en meet aan de hand van een meetstroom geinduceerd door het hall effect de totale stroom. <!--snel geschreven-->

- **Voordelen:**
    - Output eenvoudig in te lezen op een microcontroller
- **Nadelen:**
    - Kan beinvloed worden door temperatuur en andere em-uitstraling

### Ultrasoon sensor
<img src="{{ '/assets/img/Watersysteem/Ultrasoon.png' | relative_url }}" alt="Afbeelding van de onderwaterpomp" width="400" />

De [ultrasoon sensor](https://www.tinytronics.nl/nl/sensoren/afstand/ultrasonische-afstandssensor-rcwl-1604){:target="_blank"} wordt gebruikt om de hoogte van de vloeistof in het reservoir te meten door middel van geluidsgolven. 

- **Voordelen:** 
    - Nauwkeurige meting van vloeistofniveaus
    - Geen direct contact met het water (minder slijtage en onderhoud) 
    - Eenvoudig te integreren in het systeem

- **Nadelen:** 
    - Kan interfereren met oneven wateroppervlak
    - Kan gevoelig zijn voor interferentie van obstakels in de omgeving
    - Vereist een geschikte verwerking van het signaal voor juiste interpretatie
    - Beperkte nauwkeurigheid bij hoge luchttemperaturen of luchtstromingen <!--Minder van toepassing voor ons, denk ik-->

<!-- Moesten we voor Mevr. Van der Perre ook geen alternatieve opties bekijken?--> 
Alternatieve opties zijn: Zie doc Charlotte

### Luchtpomp en luchtsteen
<img src="{{ '/assets/img/Watersysteem/Luchtpomp+luchtsteen.png' | relative_url }}" alt="Afbeelding van de luchtpomp en luchtsteen" width="400" />

Voor het water- en voedingsstofreservoir vind een combinatie van een [luchtpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/luchtpomp-pyp370-12z-12v){:target="_blank"} met een [luchtsteen](https://nl.aliexpress.com/item/1005007443597285.html?spm=a2g0o.productlist.main.3.4a1049a6vx7Vpx&algo_pvid=de01e062-ea6d-400d-88c9-a07874e6f9d2&algo_exp_id=de01e062-ea6d-400d-88c9-a07874e6f9d2-1&pdp_ext_f=%7B%22order%22%3A%22312%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%212.05%210.97%21%21%2115.22%217.19%21%402103919917398752453552720ea209%2112000040774308148%21sea%21BE%210%21ABX&curPageLogUid=gjOskVCvOZWp&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"} plaats om lucht in het water te brengen. Dit verhoogt het zuurstofgehalte en voorkomt de groei van algen.
Toevoegen van zuurstof aan het water verhoogt de opname van nutriënten, verbetert de wortelontwikkeling en verlaagt stress in de plant. Meer zuurstof bevorderd echter algengroei, maar de beweging van het water veroorzaakt door de luchtpomp voorkomt ook algengroei.

- **Voordelen:**
    - Fijne luchtbellen: betere zuurstofverdeling
    - Voorkomt algenvorming in stilstaand water
    - Energiezuinig systeem    <!-- Stil?--> 
    - Geen directe elektrische belasting in het water (veilig)

- **Nadelen:**
    - Luchtsteen kan verstopt raken
    - Luchtpomp is niet waterdicht
    - Luchtsteen is breekbaar
    - Extra zuurstof kan de algengroei bevorderen

De watercirculatie wordt op regelmatige tijdsintervallen geactiveerd om algengroei tegen te gaan. Algengroei ontstaat door stilstaand voedingstofrijk water, andere invloeden zijn de hoeveelheid water en de aanwezigheid van schaduw of licht. Het waterpijl van de reservoirs word gemonitord en aangevuld wanneer dit te laag komt te staan. Hiervoor wordt gebruik gemaakt van een ultrasone sensor. Deze sensoren werden simpelweg gekalibreerd door een meting te doen wanneer het reservoir leeg en vol is.
De lades worden voorzien van water wanneer zij dit nodig hebben, aan de hand van routines in de HomeAssistant. 

### Onderwaterpomp
<img src="{{ '/assets/img/Watersysteem/Onderwaterpomp.png' | relative_url }}" alt="Afbeelding van de onderwaterpomp" width="400" />

Voor het mengreservoir werd een [onderwaterpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/onderwaterpomp-horizontaal-3-6v){:target="_blank"} gekozen om een krachtigere, turbulentere menging van het water en voedingstof te verkrijgen. 

- **Voordelen:**
    - Krachtige pomp voor snelle en efficiënte menging
    - Betrouwbaar bij constant gebruik in water
    - Compact en eenvoudig te integreren in een systeem, geschikt voor zowel horizontale als verticale installatie
    - Energiezuinig

- **Nadelen:**
    - Beperkte capaciteit bij grotere watervolumes (scalability)
    - Niet geschikt voor continue luchtpomping
    - Kan oververhit raken als de vloeistof te laag is
    - Vereist regelmatig onderhoud om verstoppingen te voorkomen <!-- Ook een gaasje toevoegen?--> 

### UV-C
<img src="{{ '/assets/img/Watersysteem/UV_C.png' | relative_url }}" alt="Afbeelding van de UV_C" width="400" />

De [UV-C sterilisator](https://nl.aliexpress.com/item/1005006110975582.html?spm=a2g0o.detail.pcDetailBottomMoreOtherSeller.56.1dc5lUxFlUxFQM&gps-id=pcDetailBottomMoreOtherSeller&scm=1007.40050.354490.0&scm_id=1007.40050.354490.0&scm-url=1007.40050.354490.0&pvid=dc0bb433-8fde-4045-9085-4eecaa485c2d&_t=gps-id%3ApcDetailBottomMoreOtherSeller%2Cscm-url%3A1007.40050.354490.0%2Cpvid%3Adc0bb433-8fde-4045-9085-4eecaa485c2d%2Ctpp_buckets%3A668%232846%238108%231977&pdp_ext_f=%7B%22order%22%3A%2218%22%2C%22eval%22%3A%221%22%2C%22sceneId%22%3A%2230050%22%7D&pdp_npi=4%40dis!EUR!33.06!15.88!!!260.96!125.35!%40211b813b17443072665026527eba8d!12000038728939852!rec!BE!!ABX&utparam-url=scene%3ApcDetailBottomMoreOtherSeller%7Cquery_from%3A){:target="_blank"} wordt gebruikt om het water te desinfecteren met behulp van ultraviolet licht. Het UV-C licht breekt DNA-structuren van micro-organismen zoals algen, bacteriën en schimmels af. Hierdoor kunnen ze niet meer vermenigvuldigen. 

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

- **Voordelen:**
    - Digitale uitlezing van de aanwezige voedingsstoffen
    - Vereist minder input van de user
    - Uitwisselbaar, indien in de toekomst bijvoorbeeld een fosfaatprobe geintegreerd word.
- **Nadelen:**
    - Vereist regelmatige kalibratie
    - Duurder (in vergelijking met manuele testen)
    - Temperatuurafhankelijk

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