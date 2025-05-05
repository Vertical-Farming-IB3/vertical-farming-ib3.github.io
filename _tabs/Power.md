---
icon: fas fa-plug
order: 4
---

> Under construction
{: .prompt-warning }

## Power


## Energieverbruik en vermogen
Het systeem verbruikt natuurlijk elektriciteit. Om dit goed in de gaten te houden, wordt het energieverbruik per onderdeel apart gemeten en weergegeven via Home Assitant. Zo kan je makkelijk zien waar veel of weinig vermogen wordt gebruikt.
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
