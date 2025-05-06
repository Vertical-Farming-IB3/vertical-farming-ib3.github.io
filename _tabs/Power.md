---
icon: fas fa-plug
order: 4
---

> Under construction
{: .prompt-warning }

## Inhoud 

1. [Simple and safe](#simple-and-safe)
   - [Fuse](#fuse)
   - [Ingang en hoofdschakelaar](#ingang-en-hoofdschakelaar)
   - [Connectoren](#connectoren)
   - [Kabels](#kabels)
3. [Energieverbruik en vermogen](#energieverbruik-en-vermogen)
   - [ACS712 Hall-effect stroomsensor (team water)](#acs712-hall-effect-stroomsensor-team-water)
   - [ACS712 module (team plantenbak)](#acs712-module-team-plantenbak)
   - [ZXCT1107 Stroommonitor (team licht)](#zxct1107-stroommonitor-team-licht)
   
## Simple and safe
Als team Power willen we alle groepen op een zo veilig en eenvoudig mogelijke manier van stroom voorzien. Daarnaast moet het voor team Licht en team Plantenbak mogelijk zijn om op verschillende niveaus in de kast stroom af te halen.
### Fuse
Om de kast, de gebruikers en de plaatselijke infrastructuur te beschermen: voorzien we een fuse van 1 ampère aan de ingang. Deze beperkt het maximaal verbruik tot 230 watt en biedt bescherming bij technische defecten.
<img src="{{ 'assets/img/Licht/20mm-glass-fuse-f_6.png' | relative_url }}" alt="Afbeelding van een fuse" width="400" />
### Ingang en hoofdschakelaar
De fuse is verwerkt in een connector met ingebouwde schakelaar en een C14 ingang. Dit zorgt ervoor dat het aan en uit schakelen van de kast eenvoudig blijft.
<img src="{{ 'assets/img/Licht/main connector.png' | relative_url }}" alt="Afbeelding van de ingang" width="400" />
### Spanningen
Om de juiste spanningen te voorzien hebben we eerst samen gezeten met alle teams. Daar ondervonden we dat team licht minstens 24v nodig zal hebben voor de leds, water minstens 12v voor de pompen en team plantenbak minstens 12v voor de ventilatoren. Om het zo eenvoudig mogelijk te houden kozen we om te werken met twee voedingen, de omzettingen naar 3.3v voor de ESP wordt op de PCB zelf gedaan.
<img src="{{ 'assets/img/Licht/power.png' | relative_url }}" alt="Afbeelding van de voeding op de binnenkast" width="400" style="border-radius: 20px;" />
### Connectoren
We gebruiken GX12-4 connectoren, die bevatten 4 pinnen. Hierop worden zowel de 24 V als de 12 V aangesloten. De connectoren kunnen slechts op één manier worden aangesloten, wat garandeert dat team Plantenbak altijd 12 V ontvangt en team Licht 24 V.
Doordat beide spanningen op dezelfde connector beschikbaar zijn, is het systeem eenvoudig te gebruiken. In totaal zijn er vijf connectoren geplaatst op verschillende hoogtes in de kast.
<img src="{{ 'assets/img/Licht/connector.png' | relative_url }}" alt="Afbeelding van de connector" width="400" />
### Kabels
Voor de verbinding tussen de connector en de voedingen gebruiken we een kabel van 0,75 mm². Deze kunnen tot 1300 watt aan, dat is ruim voldoende aangezien de fuse het vermogen begrenst tot 230 watt.
Tussen de connectoren en de voedingen worden diverse kabeltypes gebruikt, maar met een minimale diameter van 1 mm². Aangezien de voedingen maximaal 100,8 watt leveren, zijn alle gebruikte kabels ruim voldoende gedimensioneerd.

## Energieverbruik en vermogen
Het systeem verbruikt natuurlijk wel wat elektriciteit. Om ons verbruik goed in de gaten te houden, wordt dit per onderdeel apart gemeten en weergegeven via Home Assitant. Zo kan je makkelijk zien waar veel of weinig vermogen wordt gebruikt.
Het doel is om zo weinig mogelijk energie te verbruiken, bij het behouden van een optimale werking.

### ACS712 Hall-effect stroomsensor (team water)
<img src="{{ '/assets/img/Watersysteem/hall-effect-cs.png' | relative_url }}" alt="Hall effect" width="400" />

Voor Team Water gebeurt de vermogensmeting met een hergebruikte sensor van vorig jaar: de ACS712 Hall-effect stroomsensor. Daarbij meten we de stroom die door de voedingskabel van de PCB loopt.

Deze sensor werkt op een galvanisch gescheiden manier, wat de veiligheid bevordert. Wanneer er stroom door de draad vloeit, ontstaat er een klein magnetisch veld rondom die draad. De sensor meet dat veld en zet het om in een analoog signaal dat we uitlezen op [onze PCB](https://vertical-farming-ib3.github.io/Water/#stuurlogica).
De spanning is gekend (een constante 12V) waardoor we door een simpele formule het verbruikt vermogen kunnen berekenen: vermogen = spanning x stroom. 

We voerden een kalibratie uit met deze sensor die [hier](https://github.com/Vertical-Farming-IB3/Plan-T/blob/main/Water/Vermogensmeting.md) terug te vinden is. Bij deze kalibratie merken we op dat er een hogere accuratie behaald wordt bij grote vermogens. Over het gehele meetbereik behalen we een gemiddelde meetfout van 6%.

De UV-C-lamp zit op een afzonderlijke vermogenskring, deze wordt niet rechtstreeks gemeten (hoge spanning!). Er wordt hiervoor een theoretisch verbruik bij de meting opgeteld.

- **Voordelen:**
    - Output eenvoudig in te lezen op een microcontroller
- **Nadelen:**
    - Kan beïnvloed worden door temperatuur en andere EM-uitstraling
    - Meet de bronspanning niet op

### ACS712 module (team plantenbak)
Voor de plantenbakken werd een al gemaakte module gebruikt. Een teamlid had deze thuis nog op overschot en dit bespaarde ons  tijd omdat we zelf geen module moesten maken. Het werkingsprincipe is idem als bij team water: het is een hall-effect stroomsensor.

<img src="{{ '/assets/img/Plantenbak/acs712.png' | relative_url }}" alt="Hall effect" width="400" />

### ZXCT1107 Stroommonitor (team licht)

Voor team Licht gebeurt de powermeting via een stroommonitor: de ZXCT1107, een high-side stroommonitor van Diodes Incorporated. Alles wordt duidelijk uitgelegd in de bijgevoegde pdf.

 [Powermeting (PDF)](https://vertical-farming-ib3.github.io/assets/img/Licht/powermeting.pdf)
