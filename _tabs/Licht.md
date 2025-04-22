---
icon: fas fa-lightbulb
order: 3
---

> Under construction
{: .prompt-warning }

## Introductie

Bij Team Licht werken we aan LED-verlichtingssystemen die speciaal zijn afgestemd voor de vertical farm. Ons huidige project richt zich op de teelt van snijsla en groene kruiden zoals basilicum, koriander en munt. De nadruk ligt op een efficiënte en uniforme lichtverdeling met een optimale
Photosynthetic Photon Flux Density (PPFD), afgestemd op bladgroenten. 

## LED-selectie

Voor dit project zijn drie types LED’s geselecteerd uit de Cree J Series JE2835 Color-reeks:

| Type       | Kleur       | Golflengte (nm) | PPF (µmol/s⁻¹) | View Angle (°) |
|------------|-------------|------------------|----------------|----------------|
| JE2835ARY  | Royal Blue  | 450–460          | 1.01           | 124            |
| JE2835AHR  | Photo Red   | 650–670          | 0.72           | 121            |
| JE2835AFR  | Far-Red     | 720–740          | 0.72           | 121            |

## Spectrum en kleurverhouding

De keuze van lichtkleuren is cruciaal voor het sturen van de fotosynthese, bladontwikkeling en
morfologie. Dit project gebruikt drie spectraalkleuren:

#### Blauw licht (450–460 nm)
Bevordert bladontwikkeling, fotomorfogenese, pigmentvorming en compactheid van de plant.
Het helpt overmatige strekking voorkomen.

#### Rood licht (650–670 nm)
Stimuleert fotosynthese en draagt sterk bij aan biomassavorming. Rood licht is bijzonder efficiënt in de activering van chlorofyl.

#### Far-Red licht (720–740 nm)
Hoewel buiten het PAR-bereik, versterkt far-red in combinatie met rood licht de fotosynthese via
het Emerson-effect. Het wordt beperkt ingezet om ongewenst schieten en bloei te vermijden.

#### Verhouding en doel
Per lade wordt gebruikgemaakt van:
- 12 blauwe LED’s
- 20 rode LED’s
- 16 far-red LED’s

Verhoudingen:
- $R:B = \frac{20}{12} \approx 1.67$
- $R:FR = \frac{20}{16} = 1.25$

Deze zijn gekozen om zowel compacte groei als efficiënte fotosynthese te bevorderen, zonder te
veel far-red dat tot bloei of strekking kan leiden.

## Far-Red overweging

Hoewel far-red licht buiten het fotosynthetisch actieve spectrum (PAR) valt, draagt het bij aan
het Emerson-effect, waarbij de combinatie van rood en far-red licht leidt tot een verhoogde
fotosynthetische effici¨entie [1]. In dit ontwerp wordt far-red licht daarom in beperkte mate
toegepast. Aangezien de focus ligt op bladgroei en niet op de reproductieve fase (zoals bloei of
zaadvorming), is het nodig om overmatige stimulatie van fotosynthese te vermijden. Bij te hoge
lichtintensiteit kan dit proces van voortijdig schieten bevorderen, wat ongewenst is bij de teelt
van bladgewassen.

## Photosynthetic Photon Flux Density (PPFD)

PPFD, uitgedrukt in µmol m⁻² s⁻¹, meet het aantal fotosynthetisch actieve lichtfotonen dat een
plantoppervlak bereikt. Dit is essentieel in vertical farming, waar kunstlicht de enige bron van
energie is voor fotosynthese.

#### Sla en basilicum
-  PPFD van 250 µmol m⁻² s⁻¹ is optimaal voor biomassa, kwaliteit en energiegebruik.
- 200 µmol m⁻² s⁻¹ volstaat bij hoge plantdichtheid (680 planten/m2).
  
#### Koriander
- PPFD van 250–300 µmol m⁻² s⁻¹ bevordert biomassatoename en antioxidantproductie.
- Optimale prestaties bij verhoogde worteltemperatuur en CO2.

Aanbevolen richtlijn: Voor bladgewassen is 200–250 µmol m⁻² s⁻¹ geschikt, afhankelijk vanruimtegebruik en teeltstrategie

### PPFD-berekening

Voor een en lade van 0.173 m² met 12 blauwe, 20 rode en 16 far-red LED's geldt:

PPFD<sub>totaal</sub> = (12 × 1.01) + (20 × 0.72) + (16 × 0.72)  
= 12.12 + 14.4 + 11.52 = 38.04 µmol/s  

PPFD = 38.04 / 0.173 = 219.05 µmol/m²/s

## Afstand en uniformiteit

De LED’s worden op 25–30 cm boven het gewas geplaatst. Dankzij de brede uitstralingshoek
(121–124°) ontstaat een egale belichting. De kast is voorzien van een witte coating die fungeert
als reflectieve achtergrond en zo schaduwvorming vermindert.

## Fotoperiode

Een cyclus van 16 uur licht en 8 uur donker (16L/8D) is toegepast, wat bewezen effectief is voor
bladgroenten.

## Ontwerp

Voor het ontwerp van de LED-PCB is bewust gekozen voor een compact formaat. Door kleinere printplaten te gebruiken, kan de lichtspreiding beter worden beheerst en afgestemd op de omstandigheden. Elke LED-PCB bevat:
- 3 blauwe LED’s
- 5 rode LED’s
- 4 far-red LED’s

<img src="{{ '/assets/img/Licht/LEDPCB3D.png' | relative_url }}" alt="PCB-ontwerp van de LED-PCB" width="600" />

Voor het aansturen van de LED’s is een aparte driver-PCB ontworpen. Per lade is één driver-PCB nodig, waarop maximaal zes LED-PCB’s kunnen worden aangesloten. Dit biedt flexibiliteit: er kan eenvoudig wit licht worden toegevoegd of het lichtniveau verhoogd worden door extra LED-PCB’s te installeren.

De driver-PCB bevat drie drivers en een ESP32-microcontroller voor de aansturing. De voedingsspanning bedraagt 24V, waarbij een LDO-regelaar wordt gebruikt om de ESP32 van 3,3V te voorzien.

<img src="{{ '/assets/img/Licht/DriverPCBSide.png' | relative_url }}" alt="PCB-ontwerp van de Driver-PCB" width="600" />

Voor de verbinding tussen de LED-PCB’s en de driver-PCB’s wordt gebruikgemaakt van terminal blocks, wat zorgt voor een eenvoudige en robuuste aansluiting.

## Uitvoering

De verlichting wordt toegepast in lades van 45,7 cm x 38 cm (0.174 m²). Elke lade bevat uiteindelijk 4 PCB’s met:
- 3 blauwe LED’s
- 5 rode LED’s
- 4 far-red LED’s
  
Totaal per lade: 12 blauwe, 20 rode, 16 far-reds.

<div style="display: flex; justify-content: center; gap: 4px; align-items: center; text-align: center;">
    <img src="{{ site.baseurl }}/assets/img/Licht/LEDPCB.png" alt="LED-PCB Realisatie" style="width: 40%;">
    <img src="{{ site.baseurl }}/assets/img/Licht/DriverPCB.png" alt="Driver-PCB Realisatie" style="width: 40%;">
</div>


