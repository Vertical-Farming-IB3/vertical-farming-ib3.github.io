---
icon: fas fa-plug
order: 4
---

> Under construction
{: .prompt-warning }

## Power


## Energieverbruik en vermogen
Het systeem verbruikt natuurlijk elektriciteit. Om dit goed in de gaten te houden, wordt het energieverbruik per onderdeel apart gemeten en weergegeven via het home assitant. Zo kunnen we makkelijk zien waar veel of weinig vermogen wordt gebruikt.
Het doel is om zo weinig mogelijk energie te verbruiken, terwijl alles toch goed blijft werken.

### Hall-efect stroomsensor (team water)
<img src="{{ '/assets/img/Watersysteem/hall-effect-cs.png' | relative_url }}" alt="Hall effect" width="400" />

Voor Team Water gebeurt dit met een systeem dat we hergebruiken van vorig jaar. Daarbij meten we de hoeveelheid vloeiende stroom gebruikmakend van een Hall-effect sensor.

Deze sensor werkt op een slimme manier: hij hoeft de stroomdraad niet door te knippen of te onderbreken, maar meet de stroom gewoon vanop afstand. Hoe dat kan? Als er stroom door een draad gaat, ontstaat er een klein magnetisch veld rondom die draad. De sensor meet dat veld en zet het om in een signaal dat we kunnen aflezen.
De spanning is geweten waardoor we door een simple formule het verbruikt vermogen kunnen berekenen: vermogen = spanning x stroom.

Zo kunnen we veilig en nauwkeurig meten hoeveel het watersysteem verbruikt — zonder het systeem zelf te storen.

### ACS712 module (team plantenbak)
Voor de plantenbakken werd een al gemaakte module gebruikt. Een teamlid had deze thuis nog op overschot en dit bespaarde ons  tijd omdat we zelf geen module moesten maken. Het werkingsprincipe is idem als bij team water: het is een hall-effect stroomsensor.

<img src="{{ '/assets/img/Plantenbak/acs712.png' | relative_url }}" alt="Hall effect" width="400" />
