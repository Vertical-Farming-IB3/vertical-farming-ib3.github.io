---
# the default layout is 'page'
icon: fas fa-droplet
order: 2
---

<!-- Nieuwe indeling -->


> Under construction
{: .prompt-warning }

## Inhoud
1. [Introductie](#introductie)
2. [Toevoer](#toevoer)
   - [Reservoirs](#reservoirs)
   - [Pompsysteem](#pompsysteem)
   - [Lades](#lades)
3. [Afvoer](#afvoer)
   - [Zwaartekrachtgestuurd](#zwaartekrachtgestuurd)
   - [Hergebruik van water](#hergebruik-van-water)
4. Stuurlogica
   - [PCB](#pcb)
   - [Pompaansturing](#pompaansturing)
   - [UV-C](#uv-c)
5. [Componenten en keuzes](#componenten-en-keuzes)
   - [Reservoirs](#reservoirs-1)
   - [Tubes](#tubes)
   - [Quick connectors tubes](#quick-connectors-tubes)
   - [Waterpomp](#waterpomp)

## Introductie
Het watersysteem bestaat uit twee hoofdonderdelen:
- Watertoevoer en afvoer
- Stuurlogica (elektronica)

### Schematische voorstelling (vooraanzicht)
<img src="{{ '/assets/img/Watersysteem/Plan_Watersysteem.png' | relative_url }}" alt="Schematische tekening van het watersysteem" width="600" />

## Toevoer
### Reservoirs:  
Het systeem bevat drie reservoirs:
- Waterreservoir
- Voedingsstofreservoir
- Mengreservoir

Dit zijn de bloembakken van vorig project. Deze waren ruim genoeg en konden eenvoudig geïntegreerd worden binnen ons ontwerp. 

De drie reservoirs zijn uitneembaar, wat het reinigen en bijvullen eenvoudig maakt. Elk reservoir is uitgerust met een ultrasone sensor voor het nauwkeurig meten van het vloeistofniveau. Om algengroei te voorkomen, wordt het water in de reservoirs continu gecirculeerd met behulp van luchtpompen en luchtstenen.
Meer informatie over de gebruikte componenten vindt u terug bij [componenten en keuzes](#componenten-en-keuzes).

Het mengreservoir mengt het water met de voedingsstoffen. Een aquariumpomp zorgt hier voor het mengen en circuleren van de vloeistof. Daarnaast is het mengreservoir voorzien van een UV-C lamp, als extra maatregel tegen micro-organismen en biologische verontreiniging.

### Pompsysteem: 
1. Twee pompen brengen water en voedingsstoffen vanuit hun respectievelijke reservoirs naar het mengreservoir.
2. Vanuit het mengreservoir transporteert een aparte pomp de gemengde vloeistof naar de lades. Omdat we gekozen hebben om met twee lades te werken, gebruiken we twee pompen voor de toevoer. Aan elke pomp kunnen  darmpjes op verschillende hoogtes worden aangesloten, waardoor we een modulair systeem hebben gecreëerd dat eenvoudig uitbreidbaar en aanpasbaar is.

<img src="{{ '/assets/img/Watersysteem/Pompen_Aansluiting.jpg' | relative_url }}" alt="Afbeelding van aansluiting pomp" width="400" />

### Lades
Het systeem ondersteunt twee irrigatiemethoden. Meer details hierover vind je op de Plantenbak-pagina, in de sectie '[De twee lades
](https://vertical-farming-ib3.github.io/Plantenbak/#De-twee-lades)'.  

## Afvoer
### Zwaartekrachtgestuurd
De afvoer van water gebeurt op basis van zwaartekracht. De lade is voorzien van een valse bodem en staat licht gekanteld, zodat overtollig water via een pvc-buis terugstroomt naar het mengreservoir. Hierdoor is er geen extra pomp nodig voor de afvoer. De pvc-buis is deels open gesneden en voorzien van afdekkingen om spatten op te vangen. Op deze manier behouden we een hoge mate van modulariteit in het systeem.

### Hergebruik van water
<!--Nog aanpassen na bespreking-->
Het afgevoerde water wordt niet zomaar geloosd. In het mengreservoir wordt dit restwater opnieuw gefilterd en gesteriliseerd (door de UVC-lamp en eventueel een fijnmazig gaasfilter). Nadien kan dit water opnieuw gebruikt worden, eventueel met bijmenging van vers water of extra voedingsstoffen indien nodig.

Dit maakt het systeem duurzaam en circulair, met minimale water- en nutriëntenverspilling.

## Stuurlogica
### PCB 
<img src="{{ '/assets/img/Watersysteem/PCB-Watersysteem' | relative_url }}" alt="Afbeelding van de PCB" width="400" />
<!--Link naar github.-->
### Pompaansturing
<!-- Ultrasoon, probes, pompen -->
Onderwaterpomp wordt pas gestuurd als het vloeistofniveau voldoende hoog is, zodat we vermijden dat de pomp lucht pompt. Hoogte gemeten met ultrasoon. 
### UV-C
<!-- Nakijken met bestelling-->


## Componenten en keuzes
### Reservoirs
<img src="{{ '/assets/img/Watersysteem/reservoir.png' | relative_url }}" alt="Afbeelding van reservoir" width="400" />

De resevoirs zijn bedoeld als opslag van zuiver water, voedingsstoffen, en restwater.

- **Voordelen:**   
    - Budgetvriendelijk
    - goede integratie
    - makkelijk te reinigen
- **Nadeel:**
    - Niet afsluitbaar

### Tubes
De [tubes](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/onderdelen/slangen/waterslang-voor-onderwaterpomp-verticaal-horizontaal-3-6v-transparant-1-meter){:target="_blank"} hebben een diameter van 8 mm en zijn bedoeld voor de transport van water. 
 
- **Voordelen:**    
    - Flexibel
    - Transparant
    - Compatibel met kleine pompen
    - Lichtgewicht en makkelijk op maat te knippen.
- **Nadelen:**     
    - Niet geschikt voor hoge druk
    - Kan knikken bij scherpe bochten
    - Niet UV-bestendig

### quick connectors tubes
<img src="{{ '/assets/img/Watersysteem/connect.png' | relative_url }}" alt="Afbeelding van de connectors" width="400" />

De [Push-to-Connect koppelingen](https://nl.aliexpress.com/item/1005005808872752.html?spm=a2g0o.productlist.main.7.3edaJcT6JcT6q5&algo_pvid=3a7059ff-e7ee-43a2-b5fc-a499e4ff6cb3&algo_exp_id=3a7059ff-e7ee-43a2-b5fc-a499e4ff6cb3-3&pdp_ext_f=%7B%22order%22%3A%22400%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%212.75%210.97%21%21%212.81%210.99%21%402103864c17398869650571235ecd39%2112000034430185033%21sea%21BE%210%21ABX&curPageLogUid=4qEj3wATijZm&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"} worden gebruikt om verschillende buizen of componenten snel en stevig met elkaar te verbinden zonder gebruik van klemmen of lijm.

- **Voordelen:**
    - Snelle installatie
    - Hergebruikbaar
    - Sterke afdichting 
    - Compact
- **Nadelen:**
    - Minder geschikt bij hoge druk 
    - Kan loskomen bij slechte plug in 
    - Enkel 8mm → 8mm

### Waterpomp
<img src="{{ '/assets/img/Watersysteem/Waterpomp.png' | relative_url }}" alt="Afbeelding van de waterpomp" width="400" />

De [waterpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/waterpomp-12v){:target="_blank"} heeft een maximale spanning van 12VDC en gebruikt ~400mA (=> P=4,8W). De pomp heeft een maximale opvoerhoogte van 3m en aanzuighoogte van 1,5m. Deze is geschikt voor slangen met ongeveer 8 mm binnendiameter. 

- **Voordelen:**
    - Relatief krachtig voor kleine systemen
    - Lage spanningsvereiste (veilig in gebruik)
    - Compact ontwerp, makkelijk te integreren
    - Eenvoudig aan te sluiten op 8 mm slang
- **Nadelen:**
    - Niet geschikt voor continu gebruik (kan oververhitten)
    - Beperkte compatibiliteit met dikkere slangen
    - Verbruikt relatief veel stroom bij batterijvoeding

### Luchtpomp en luchtsteen
<img src="{{ '/assets/img/Watersysteem/Luchtpomp+luchtsteen.png' | relative_url }}" alt="Afbeelding van de luchtpomp en luchtsteen" width="400" />


Voor het water- en voedingsstofreservoir werd een combinatie van een [luchtpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/luchtpomp-pyp370-12z-12v){:target="_blank"} met een [luchtsteen](https://nl.aliexpress.com/item/1005007443597285.html?spm=a2g0o.productlist.main.3.4a1049a6vx7Vpx&algo_pvid=de01e062-ea6d-400d-88c9-a07874e6f9d2&algo_exp_id=de01e062-ea6d-400d-88c9-a07874e6f9d2-1&pdp_ext_f=%7B%22order%22%3A%22312%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%212.05%210.97%21%21%2115.22%217.19%21%402103919917398752453552720ea209%2112000040774308148%21sea%21BE%210%21ABX&curPageLogUid=gjOskVCvOZWp&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"}  gekozen om lucht in het water te brengen. Dit verhoogt het zuurstofgehalte en voorkomt de groei van algen.

- **Voordelen:**
    - Fijne luchtbellen: betere zuurstofverdeling
    - Voorkomt algenvorming in stilstaand water
    - Stil en energiezuinig systeem
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

### Ultrasoon sensor
<img src="{{ '/assets/img/Watersysteem/Ultrasoon.png' | relative_url }}" alt="Afbeelding van de onderwaterpomp" width="400" />

De [ultrasoon sensor](https://www.tinytronics.nl/nl/sensoren/afstand/ultrasonische-afstandssensor-rcwl-1604){:target="_blank"} wordt gebruikt om de hoogte van de vloeistof in het reservoir te meten door middel van geluidsgolven. 

- **Voordelen:** 
    - Nauwkeurige meting van vloeistofniveaus
    - Geen direct contact met het water (minder slijtage) 
    - Eenvoudig te integreren in een systeem
    - Geschikt voor gebruik in diverse omgevingen (kan in verschillende vloeistoffen worden gebruikt)
    - Weinig onderhoud nodig

- **Nadelen:**
    - Kan gevoelig zijn voor interferentie van obstakels in de omgeving
    - Vereist een geschikte verwerking van het signaal voor juiste interpretatie
    - Beperkte nauwkeurigheid bij hoge luchttemperaturen of luchtstromingen

### UV-C
<img src="{{ '/assets/img/Watersysteem/UV_C.png' | relative_url }}" alt="Afbeelding van de UV_C" width="400" />

De [UVC-sterilisator](https://nl.aliexpress.com/item/1005006110975582.html?spm=a2g0o.detail.pcDetailBottomMoreOtherSeller.56.1dc5lUxFlUxFQM&gps-id=pcDetailBottomMoreOtherSeller&scm=1007.40050.354490.0&scm_id=1007.40050.354490.0&scm-url=1007.40050.354490.0&pvid=dc0bb433-8fde-4045-9085-4eecaa485c2d&_t=gps-id%3ApcDetailBottomMoreOtherSeller%2Cscm-url%3A1007.40050.354490.0%2Cpvid%3Adc0bb433-8fde-4045-9085-4eecaa485c2d%2Ctpp_buckets%3A668%232846%238108%231977&pdp_ext_f=%7B%22order%22%3A%2218%22%2C%22eval%22%3A%221%22%2C%22sceneId%22%3A%2230050%22%7D&pdp_npi=4%40dis!EUR!33.06!15.88!!!260.96!125.35!%40211b813b17443072665026527eba8d!12000038728939852!rec!BE!!ABX&utparam-url=scene%3ApcDetailBottomMoreOtherSeller%7Cquery_from%3A){:target="_blank"} wordt gebruikt om het water te desinfecteren met behulp van ultraviolet licht. Het UV-C licht breekt DNA-structuren van micro-organismen zoals algen, bacteriën en schimmels af. Hierdoor kunnen ze niet meer vermenigvuldigen. 

- **Voordelen:**
    - Effectieve en chemievrije watersterilisatie
    - Verlaagt de kans op algen- en biofilmvorming
    - Compact ontwerp, makkelijk te integreren
    - Continu gebruik mogelijk zonder extra onderhoudsproducten
- **Nadelen:**
    - Werkt enkel in helder water (verminderd effect bij troebelheid)
    - Beperkte levensduur van de UV-lamp (~8000 uur)
    - Kan gevaarlijk zijn bij directe blootstelling aan mens of dier (goede afscherming vereist)

### Hallefect stroomsensor 
<!--Kjell-->

### Probes
Elke plant heeft dezelfde voedingsstoffen nodig, deze voedingsstoffen zijn opgedeeld in verschillende klassen en zijn gekoppeld aan verschillende concentraties. De primaire voedingsstoffen zijn: Stikstof (N), Fosfor (P) en Kalium (K). Secundaire voedingsstoffen zijn Calcium (Ca), Magnesium (Mg) en Zwavel (S). En hiernaast zijn er ook nog vele micronutriënten.

Om de waterkwaliteit in de gaten te houden maken we gebruik van probes (elektroden). We kunnen echter niet voor elk van deze voedingsstoffen een elektrode voorzien, daarom beperken we ons tot een deelset. We kozen voor het gebruik van:

* [Nitraat probe](https://www.alibaba.com/product-detail/Nitrate-Ion-selective-Electrode-NO3-ISE_60817798149.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cjuoxNt){:target="_blank"}
* [Kalium probe](https://www.alibaba.com/product-detail/ISE-K-Potassium-Ion-Selective-Electrode_1600225607843.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}
* [Calcium probe](https://www.alibaba.com/product-detail/PCa-1-01-Calcium-Ion-Selective_60659669573.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}

De reden waarom we het calciumgehalte opmeten en niet het fosforgehalte is omdat een probe voor het meten van fosfaten veel duurder is in vergelijking met de andere probes. <!-- er staat ook geen p waarde op ons fles, maar dat is nu louter toeval en maakt P niet onbelangrijk --> De calcium probe is geïntegreerd omdat we stevige planten willen kweken in ons vertical farm. <!-- ... --> Daarnaast verwerkten we nog twee andere probes:

* [PH probe](https://nl.aliexpress.com/item/1005006063176996.html?spm=a2g0o.productlist.main.115.307031c2JATBrr&algo_pvid=62d5342a-588c-4537-a674-e9afbfd1070f&algo_exp_id=62d5342a-588c-4537-a674-e9afbfd1070f-57&pdp_ext_f=%7B%22order%22%3A%22313%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis!EUR!6.03!4.82!!!6.34!5.07!%40210385a817430803088781346eafba!12000035561276406!sea!BE!0!ABX&curPageLogUid=X6BxvMVVvpLV&utparam-url=scene%3Asearch%7Cquery_from%3A){:target="_blank"}
* [Referentie probe](https://www.alibaba.com/product-detail/232-01-Reference-Electrode-Glass-Shell_60668853882.html?spm=a2756.order-detail-ta-ta-b.0.0.58caf19cLXQOM1){:target="_blank"}

De referentie probe is essentieeel voor het uitlezen van de overige probes. De PH-sensor is geïntegreerd omdat verschillende planten houden van een verschillende bodem zuurtegraad. Er is beslist om geen temperatuurprobe te integreren, we werken namelijk met een installatie binnenshuis, we veronderstellend dat de temperatuur relatief constant blijft. Daarnaast word de temperatuur in de kast gemeten, we zien dit als voldoende maatstaaf om de watertemperatuur te bepalen.

Dit maakt dat in totaal 5 probes zijn geïntegreerd. Deze probes worden gecallibreerd voor ze gebruikt kunnen worden, daarvoor zijn nog enkele componenten nodig, deze zullen we hieronder bespreken. De probes worden uitgelezen aan de hand van ADC-convertoren. <!-- , deze zijn gerecycled uit het vorige project.--> <!-- Dit klopt dan niet, gebeurd dit op print, de gerecycleerde ADC is voor vermogenmeting -->

<!--
#### Kallibratie
Deze probes moeten gecallibreerd worden voor het correct uitmeten van de voedingsstoffen in het mengreservoir.
-->

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

De elektroden hebben ook een referentie nodig, hiervoor wordt een referentie probe gevuld met een bekende vloeistof. Dit is 3M KCl gesatureerd met AgCl. Deze oplossing kunnen  we echter aankopen en hoeven we niet zelf te maken.

**Voedingsstoffen** <!-- hier of op verwijzing hieronder? Vet of titel? #### Voedingsstof  -->

We hebben ervoor gekozen om geen eigen voedingsstoffen samen te stellen voor het voeden van de planten, in de plaats daarvan kozen we voor een commerciële oplossing. We hebben hiervoor plantenvoeding gekocht. Deze plantenvoeding heef een NK waarde van  2.5-4. Deze waarde verwijst naar de verhouding van stikstof en kalium in de voedingsstof. In ons geval bevat de voeding 2.5% Stikstof, dit bevordert de bladgroei en algemene groei van de plant en 4% Kalium, dit versterkt de weerstand van de plant, bevordert de wortelontwikkeling en de bloei/vruchtvorming. Er staat geen fosfor vermeld, dit wil zeggen dat de gekozen plantenvoeding weinig tot geen fosfor bevat. Voor een betere opbrengst van de kast is het dus een goeie optie in een later stadium te kijken voor hogere kwaliteit voedingsstoffen. In de gebruikershandleiding staan ook aanbevolen verhoudingen voor verschillende soorten planten namelijk: kruiden ¼ dop per 2l, groenten 1 dop per 5l. Dit is een interessante verhouding om mee te nemen voor de  tuning van de vertical farm en de mogelijke verschillende gewassen.

**Kallibratie**

Zodra de drie concentraties voor een sensor zijn gemaakt, vindt de 3-puntskalibratie plaats. De referentie-ISE en de stofspecifieke ISE worden achtereenvolgens in elk van de drie stofspecifieke concentraties geplaatst en de spanning wordt gemeten. 

<!-- Kallibratie nog opnieuw doen en aanpassen-->

| Ion  |      | Oplossing | Gemeten spanning |
| ---- | ---- | --------- | ---------------- |
|      |      | [mg/l]    | [mV]             |
| NO₃⁻ | Low  | 799       | 27               |
| NO₃⁻ | Med  | 959       | 13               |
| NO₃⁻ | High | 1598      | 27               |
| Ca²⁺ | Low  | 100       | 32               |
| Ca²⁺ | Med  | 200       | 38               |
| Ca²⁺ | High | 400       | 44               |
| K⁺   | Low  | 102       | 83               |
| K⁺   | Med  | 203       | 93               |
| K⁺   | High | 406       | 102              |

<!-- De temperatuur is niet opgenomen, we gaan uit van kamertemperatuur. De medium concentratie nitraat is hier 960 mg/l in plaats van 1200 mg/l. -->


<!-- Toevoer en afvoer first draft, integreren met bestaand -->
<!-- Werken Charlotte en ik nu de site af en Kjell en Sander de code? Navragen... -->
### Connecties
### ....



<!-- Nakijken oude indeling indien nodig, zie vorige commits. :-) -->
<!-- Mss wel interresant om eens te bekijken, maar nieuw ziet er goed uit. -->