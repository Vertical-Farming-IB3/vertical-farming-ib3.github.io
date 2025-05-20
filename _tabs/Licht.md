---
icon: fas fa-lightbulb
order: 3
---

## Inhoud
1. [Introductie](#introductie)
2. [led-selectie](#led-selectie)
3. [Spectrum en kleurverhouding](#spectrum-en-kleurverhouding)
    - [Blauw licht (450-460 nm)](#blauw-licht)
    - [Rood licht (560-670 nm)](#rood-licht)
    - [Far-red licht (720-740 nm)](#far-red-licht)
    - [Photosynthetic Photon Flux Density (PPFD)](#photosynthetic-photon-flux-density-ppfd)
        * [Sla en basilicum](#sla-en-basilicum)
        * [Koriander](#koriander)
        * [PPFD-berekening](#ppfd-berekening)
4. [Elektrisch Dimensioneren](#elektrisch-dimensioneren)
5. [Aangeraden Instelling](#aangeraden-instelling) 
6. [Afstand en uniformiteit](#afstand-en-uniformiteit)
7. [Fotoperiode](#fotoperiode)
8. [Thermische berekeningen led-PCB](#thermische-berekeningen-led-pcb)
9. [Ontwerp](#ontwerp)
10. [Uitvoering](#uitvoering)
11. [Afgewerkt product](#afgewerkt-product)
11. [Bronnen](#bronnen)

## Introductie

Bij Team Licht werken we aan led-verlichtingssystemen die speciaal zijn afgestemd voor de vertical farm. Ons huidige project richt zich op de teelt van snijsla en groene kruiden zoals basilicum, koriander en munt. De nadruk ligt op een efficiënte systeem met voldoende Photosynthetic Photon Flux Density (PPFD), afgestemd op bladgroenten. 

## led-selectie

Om de juiste leds te bepalen hebben we ons gebaseerd op het uitgebreid onderzoek van vorig en de expertise van het team van Labo Licht. We hebben voor leds gekozen met een uniforme lichtverdeling voor optimale groei van de planten in de vertical farm. Zo zijn we uitgekomen bij de volgende Cree leds: 

| Type       | Kleur       | Golflengte (nm) | PPF (µmol/s⁻¹) | View Angle (°) |
|------------|-------------|------------------|----------------|----------------|
| JE2835ARY  | Royal Blue  | 450–460          | 1.01           | 124            |
| JE2835AHR  | Photo Red   | 650–670          | 0.72           | 121            |
| JE2835AFR  | Far-Red     | 720–740          | 0.72           | 121            |

## Spectrum en kleurverhouding

De keuze van lichtkleuren is cruciaal voor het sturen van de fotosynthese, bladontwikkeling en
morfologie. Dit project gebruikt drie spectraalkleuren:

### Blauw licht (450–460 nm) {#blauw-licht}

Bevordert bladontwikkeling, fotomorfogenese, pigmentvorming en compactheid van de plant.
Het helpt overmatige strekking voorkomen door de plant laag te houden en de stengels stevig te maken.

### Rood licht (650–670 nm) {#rood-licht}

Stimuleert fotosynthese en draagt sterk bij aan biomassavorming. Rood licht is bijzonder efficiënt in de activering van chlorofyl.

### Far-Red licht (720–740 nm) {#far-red-licht}

Hoewel far-red licht buiten het fotosynthetisch actieve spectrum (PAR) valt, draagt het bij aan
het Emerson-effect, waarbij de combinatie van rood en far-red licht leidt tot een verhoogde
fotosynthetische efficiëntie [1]. In dit ontwerp wordt far-red licht daarom in beperkte mate
toegepast. Aangezien de focus ligt op bladgroei en niet op de reproductieve fase (zoals bloei of
zaadvorming), is het nodig om te veel Far-Red licht te vermijden. Een te hoog percentage van Far-Red 
licht zal het process van voortijdig schieten bevorderen, wat ongewenst is bij de teelt
van bladgewassen. De planten kunnen er ook zwak van worden om ze te snel in de hoogte zullen groeien en de stengels hierdoor te smal worden.

### Photosynthetic Photon Flux Density (PPFD)

PPFD, uitgedrukt in µmol m⁻² s⁻¹, meet het aantal fotosynthetisch actieve lichtfotonen dat een
plantoppervlak bereikt. Dit is essentieel in vertical farming, waar kunstlicht de enige bron van
energie is voor fotosynthese.

#### Sla en basilicum

- PPFD van 250 µmol m⁻² s⁻¹ is optimaal voor biomassa, kwaliteit en energiegebruik.
- 200 µmol m⁻² s⁻¹ volstaat bij hoge plantdichtheid (680 planten/m2).
- PPFD spectra verdeling: R:60% FR:20% BL:20% (Dit zijn **NIET** de waardes om in te stellen via HomeAssistant, zie verder)
  
#### Koriander

- PPFD van 250–300 µmol m⁻² s⁻¹ bevordert biomassatoename en antioxidantproductie.
- Optimale prestaties bij verhoogde worteltemperatuur en CO2.
- PPFD spectra verdeling: R:60% FR:20% BL:20% (Dit zijn **NIET** de waardes om in te stellen via HomeAssistant, zie verder)

Aanbevolen richtlijn: Voor bladgewassen is 200–250 µmol m⁻² s⁻¹ geschikt, afhankelijk vanruimtegebruik en teeltstrategie. Voor de verdeling van deze PPFD raden we volgend startpunt aan R:60% FR:20% BL:20% (dit komt **NIET** overeen met de procentuele waardes van de sliders op het Home Assistant dashboard! Zie "Aangeraden Instelling" voor meer info)

#### PPFD-berekening

Voor een en lade van 0.1 m² met 12 blauwe, 20 rode en 16 far-red leds geldt:

PPFD<sub>totaal</sub> = (12 × 1.01) + (20 × 0.72) + (16 × 0.76)  
= 12.12 + 14.4 + 12.16 = 38.68 µmol/s  

PPFD = 38.68 / 0.1 = 386.8 µmol/m²/s

## Elektrisch Dimensioneren

De volgende tabel toont de elektrische karakteristieken van de individuele leds.

| **led Specifications (CreeLed)** | **Far-Red (FR)** | **Red (R)** | **Blue (B)** |
|----------------------------------|------------------|-------------|--------------|
| **Wavelength (nm)**              | 720–740          | 650–670     | 455          |
| **Current (mA)**                 | 140              | 140         | 140          |
| **Voltage (V)**                  | 2.2              | 2.15        | 2.96         |
| **Consumption (W)**              | 0.308            | 0.301       | 0.414        |

Omdat de driver tot 24V kan voorzien kunnen we 2 led-PCB's in serie plaatsen. De serie verbinding van FR, R en B leds worden dus doorverbonden en het aantal LEDs en spanning wordt hierdoor verdubbeld. Om aan voldoende PPFD output te voldoen, hebben we gekozen om 2 van deze serie connecties per lade te plaatsen. Hieronder zie je een illustratie van de opstelling.

<img src="{{ '/assets/img/Licht/dimensionering.png' | relative_url }}" alt="dimensionering led-pcb's" width="400" />

**De specificaties die één led-Driver moet voorzien (dus twee LED-PCB's in serie)** zijn hieronder gegeven, per licht spectra. Alsook de specificatie van één lade (van 2 series van elk 2 PCB's, dus 4 PCB's in totaal)

|         | FR    | R     | B      | Per serie| Per Lade|
|------------------|-------|-------|--------|-------------|-----------|
| **Aantal leds** |  8    |  10   |   6    | _           | _         |
| **Voltage (V)**  | 17.6  | 21.5  | 17.76  | —           | —         |
| **Current (mA)** | 140   | 140   | 140    | 420         | 840       |
| **Consumption (W)** | 2.5 | 3     |  2.5   | 8           | 16        |

- Ratio R:B = 20 divided by 12 ≈ 1.67
- Ratio R:FR = 20 divided by 16 = 1.25

In de volgende tabel staan de PPF/PPFD outputs van elk lichtspectra **voor één lade**.

|         | FR    | R     | B      | Totaal|
|------------------|-------|-------|--------|-------------|
| **PPF (umol s⁻¹)** | 13.4 | 15.2     | 12.2   | 40.8        |
| **PPFD, 0.1m², 80% (µmol m⁻² s⁻¹)** | 120 |   136   |  110  |  366   |

De waarde in bovenstaande tabel zijn berekend uitgaande van bepaalde voorwaarden die moeilijk vast te stellen zijn, de resultaten zullen dus niet helemaal de werkelijkheid zijn, ze dienen om een idee te geven over de output.

## Aangeraden Instelling
Via de Home Assistant Dashboard kan je per lade het lichtspectra instellen aan de hand van sliders.

Voor goede plantgroei raden we volgende waardes aan om in te stellen:
- Rood: 100%
- Diep Rood: 40%
- Blauw: 40%

Dit zorgt voor (ongeveer) volgende PPF outputs per spectra:
- Rood: 136 µmol m⁻² s⁻¹
- Diep Rood: 47 µmol m⁻² s⁻¹
- Blauw: 44 µmol m⁻² s⁻¹

Dit is een goed startpunt, hieruit kan dan beslist worden om meer of minder diep-rood of blauw toe te voegen afhankelijk van hoe de plantegroei vordert. Als de planten te veel in de hoogte toenemen en slappe stengels hebben, verhoog dan het blauwe licht en/of verlaag het diep-rode licht. Het rode licht kan best altijd op 100% staan voor maximale fotosynthese.

## Afstand en uniformiteit

De leds worden op 25–30 cm boven het gewas geplaatst. Dankzij de brede uitstralingshoek
(121–124°) ontstaat een egale belichting. De kast is voorzien van een witte coating die fungeert
als reflectieve achtergrond en zo schaduwvorming vermindert.

## Fotoperiode

Een cyclus van 16 uur licht en 8 uur donker (16L/8D) is toegepast, wat bewezen effectief is voor
bladgroenten.

## Thermische berekeningen led-PCB

Uit de berekeningen blijkt dat de totale thermische weerstand zonder koeling vrij hoog is, wat resulteert in
 een junctietemperatuur van net boven de 70°C. Dit is wel onder de maximaal toegelaten waarde van 125°C
 die weergegeven wordt in de datasheet, maar om de betrouwbaarheid en levensduur van de led te verbeteren
 is extra koeling aangewezen. Door toevoeging van een koelplaat wordt de junctietemperatuur verlaagd tot
 ongeveer 46°C, wat zorgt voor een veilige marge. Zo zal de led aanzienlijk langer kunnen functioneren zonder
 door te branden.

📄 [Thermische berekeningen (PDF)](https://vertical-farming-ib3.github.io/assets/files/Licht/thermische_berekeningen-1.pdf)


## Ontwerp

Voor het ontwerp van de led-PCB is bewust gekozen voor een compact formaat. Door kleinere printplaten te gebruiken, kan de lichtspreiding beter worden beheerst en afgestemd op de omstandigheden. Elke led-PCB bevat:
- 3 blauwe leds
- 5 rode leds
- 4 far-red leds

De afvoering van de warmte heeft veel aandacht gekregen, vooral omdat dit vorig jaar een groot probleem was. We hebben we de leds in serie met elkaar verbonden aan de hand van brede copper pours aangezien een groot deel van de warmte door de anode en cathode gedissipeerd wordt. Deze copper pours zijn identiek aan de bottom layer van de PCB geplaatst zonder silk screen, deze zijn dan met Via's verbonden met de top layer. De bottom layer en zijn copper pours wordt zo ontworpen dat er één heatsink over geplaatst zal worden. Bij het testen zien we dat de leds heel goed gekoeld worden, wat een grote verbetering is met de led-PCB's van vorig jaar.

<img src="{{ '/assets/img/Licht/LEDPCB3D.png' | relative_url }}" alt="PCB-ontwerp van de led-PCB" width="600" />

Voor het aansturen van de leds is een aparte driver-PCB ontworpen. Per lade is één driver-PCB nodig, waarop maximaal zes led-PCB’s kunnen worden aangesloten. Dit biedt flexibiliteit: er kan eenvoudig wit licht worden toegevoegd of het lichtniveau verhoogd worden door extra led-PCB’s te installeren.

De driver-PCB bevat drie drivers en een ESP32-microcontroller voor de aansturing. De voedingsspanning bedraagt 24V, waarbij een LDO-regelaar wordt gebruikt om de ESP32 van 3,3V te voorzien.

<img src="{{ '/assets/img/Licht/DriverPCBSide.png' | relative_url }}" alt="PCB-ontwerp van de Driver-PCB" width="600" />

Voor de verbinding tussen de led-PCB’s en de driver-PCB’s wordt gebruikgemaakt van terminal blocks, wat zorgt voor een eenvoudige en robuuste aansluiting.

## Uitvoering

De verlichting wordt toegepast in lades van 45,7 cm x 38 cm (0.174 m²). Elke lade bevat uiteindelijk 4 PCB’s met:
- 3 blauwe leds
- 5 rode leds
- 4 far-red leds
  
Totaal per lade: 12 blauwe, 20 rode, 16 far-reds.

<div style="display: flex; justify-content: center; gap: 1px; align-items: center; text-align: center;">
    <img src="{{ site.baseurl }}/assets/img/Licht/LEDPCB.png" alt="led-PCB Realisatie" style="width: 85%; transform: rotate(90deg);">
    <img src="{{ site.baseurl }}/assets/img/Licht/DriverPCB.png" alt="Driver-PCB Realisatie" style="width: 100%; transform: rotate(90deg);">
</div>

## Afgewerkt product

In de kast worden er 2 lades voorzien met verlichting in.


## Bronnen

📄 [Led keuze motivatie (PDF)](https://vertical-farming-ib3.github.io/assets/files/Licht/Leds_keuze_motivatie-2.pdf)
📄 [Documentatie driver (PDF)](https://vertical-farming-ib3.github.io/assets/files/Licht/Documentatie_driver.pdf)
