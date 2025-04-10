---
# the default layout is 'page'
icon: fas fa-droplet
order: 2
---


> Under construction
{: .prompt-warning }

## Plan
<img src="../assets/img/Watersysteem/Plan_Watersysteem.png" alt="Schematische tekening van het watersysteem" width="800"/>

Het systeem bestaat uit onderstaande componenten, aan elkaar gekoppeld:

### Reservoirs:  
Het systeem bevat 1 waterreservoir, 1 voedingsstofreservoir en 1 mengreservoir. Het gerecycleerde water (=water dat terug uit de plantenlades komt) wordt teruggebracht in het watersysteem.  
Het water- en voedingsstofreservoir kunnen aangevuld worden door een klep te openen aan de kast. Elk reservoir bevat een ultrasone sensor om de hoogte van de vloeistof op te meten.  
De luchtstenen (aangevoerd door luchtpompen) in het water- en voedingsstofreservoir circuleren de vloeistof om de groei van algen tegen te houden. In het mengreservoir wordt een aquariumpomp gebruikt om de vloeistoffen te mengen en ook de groei van algen tegen te gaan. In het mengreservoir zit ook een UVC-lamp, als extra maatregel tegen contaminanten (micro-organismen en biologische stoffen).

### Pompen en Pompsysteem:  
Er zijn 2 pompen aanwezig om het water en de voedingsstoffen naar het mengreservoir te brengen. Er is per lade een pomp voorzien om de gemengde vloeistof te transporteren naar de bijhorende lade.

# Componenten/onderdelen

### Reservoirs:  
<img src="../assets/img/Watersysteem/reservoir.JPEG" alt="Reservoir" width="400">  
De bloembakken van vorig project worden hergebruikt als reservoirs. Deze zijn ruim genoeg en kunnen makkelijk geïntegreerd worden in het ontwerp.

## Sensoren en Actuatoren

### Waterpomp:  
<img src="../assets/img/Watersysteem/Waterpomp.jpg" alt="Waterpomp" width="400">  
De [waterpomp](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/motoren/pompen/waterpomp-12v){:target="_blank"} heeft een maximale spanning van 12VDC en gebruikt ~400mA (=> P=4,8W). De pomp heeft een maximale opvoerhoogte van 3m en aanzuighoogte van 1,5m. Deze is geschikt voor slangen met ongeveer 6mm binnendiameter.

### Mixer:
<img src="../assets/img/Watersysteem/luchtpomp.jpg" alt="Luchtpomp" width="400">  
Voor het water- en voedingsstofreservoir werd een luchtpomp met luchtsteen gekozen voor de circulatie van het water. Dit wordt gedaan om de groei van algen te voorkomen.

Voor het mengreservoir werd een aquariumpomp gekozen. Dit zorgt voor een sterkere en turbulentere stroom van vloeistof die het water mengt. Deze pomp sturen we aan op basis van de hoogte in het reservoir (om te voorkomen dat de pomp lucht pompt, wat slecht is voor vloeistofpompen)


<!-- Toevoer en afvoer first draft -->
<!-- Werken Charlotte en ik nu de site af en Kjell en Sander de code? Navragen... -->
# Intro
Het deel water van de vertical farm omvat twee grote delen:
    - Irregatie en waterafvoer
    - Pompen en stuurlogica
In dit deel word dieper ingegaan op de hardware gefocust rond water toe- en afvoer, en het water zelf. De watertoevoer is nauw verbonden aan de pomplogica, voor de waterafvoer is gebruik gemaakt van zwaartekracht. Er zijn meerdere concepten doorlopen, uiteindelijk is gekozen voor een kastsysteem waarbij water afloopt naar een centraal reservoir, waar het restwater gefilterd <!-- UV-C + gaas? --> en hergebruikt kan worden. In dit mengvat kan ook schoon water en voedingsstoffen toegevoegd worden om een optimale waterconditie te creëren voor de planten. Voor de watertoevoer is geopteerd om met twee verschillende methodes te werken namelijk drip hydroponics/ NFT en een flood and drain. <!-- nakijken, volgens mij andere benamingen op toledo --> 
Op deze manier konden we de twee methoden vergelijken, het systeem is volledig modulair, dus naar de toekomst toe kan de tweede lade ook omgebouwd worden naar de best werkende methode.

<!-- 
    Persoonlijke nota 
    Mss voor verbeteringen naar de toekomst, is natuurlijk wel stuk complexer

Momenteel word gewerkt met een systeem waarin tegelijk twee lades gevoed kunnen worden, deze twee lades worden gevoed vanuit hetzelfde mengvat, verschillende planten kunnen echter voordeel halen uit verschillende concentraties voedingsstoffen, dit maakt het interresant om het mengvat eventueel op te splitsen in twee delen. Er is echter gekozen voor een 1 vat systeem om een meting uit te kunnen voeren met de hoogtesensor, probes, UV-C ...
-->

<!-- nog iets? Komt van alles op, maar vergeet het soms ook, wat is de scope van de website? -->

## Componenten
### Algemeen
[8 mm tubing](https://www.tinytronics.nl/nl/mechanica-en-actuatoren/onderdelen/slangen/waterslang-voor-onderwaterpomp-verticaal-horizontaal-3-6v-transparant-1-meter)
[push-in fittings](https://nl.aliexpress.com/item/1005005808872752.html?spm=a2g0o.productlist.main.7.3edaJcT6JcT6q5&algo_pvid=3a7059ff-e7ee-43a2-b5fc-a499e4ff6cb3&algo_exp_id=3a7059ff-e7ee-43a2-b5fc-a499e4ff6cb3-3&pdp_ext_f=%7B%22order%22%3A%22400%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%212.75%210.97%21%21%212.81%210.99%21%402103864c17398869650571235ecd39%2112000034430185033%21sea%21BE%210%21ABX&curPageLogUid=4qEj3wATijZm&utparam-url=scene%3Asearch%7Cquery_from%3A)
[push-in caps](#)
[Regenpijp](https://www.gamma.be/nl/assortiment/martens-buis-sanitair-glad-grijs-3-m-x-90-mm-x-1-8-mm/p/B463443?base_click=true)

<!--
    Bakken nakijken met team plantenbak
    Hoeveel details hier (main componenten?)
-->
### Systeem 1
Ventiel
### Systeem 2
8mm Druppelirrigatie 

## Voedingsstoffen
<!-- Waar moet dit komen te staan, kan hier uitleggen maar gaat beter staan bij probes, staan nog niet uitgelegd in bovenstaande stuk.-->

<!-- 
    Hoe doet iedereen die algemene dingen, verwerkt iedereen zijn stukje, komt daar nog een tab voor, ...?
    Idem met energie etc... 
-->
## Dashboard?