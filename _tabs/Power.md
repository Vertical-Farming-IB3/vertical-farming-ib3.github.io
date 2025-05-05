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

### Hall-efect stroomsensor (team water)
<img src="{{ '/assets/img/Watersysteem/hall-effect-cs.png' | relative_url }}" alt="Hall effect" width="400" />

Voor Team Water gebeurt dit aan de hand van een gerecupereerd systeem. Daarbij meten we de hoeveelheid verbruikte stroom gebruikmakend van een Hall-effect sensor.

Deze sensor werkt op een slimme manier: hij hoeft de stroomdraad niet door te knippen of te onderbreken, maar meet de stroom gewoon parallel. Hoe dat kan? Als er stroom door een draad gaat, ontstaat er een klein magnetisch veld rondom die draad. De sensor meet dat veld en zet het om in een signaal dat we kunnen uitlezen.
De spanning is bekend waardoor we door een simpele formule het verbruikt vermogen kunnen berekenen: vermogen = spanning x stroom.

Zo kunnen we veilig en nauwkeurig meten hoeveel het watersysteem verbruikt — zonder het systeem zelf te storen.

De UV-C zit op een afzonderlijke kring, deze word niet rechtstreeks gemeten (hoge spanning!). Er wordt hiervoor een theoretisch verbruik bij de meting opgeteld.

- **Voordelen:**
    - Output eenvoudig in te lezen op een microcontroller
- **Nadelen:**
    - Kan beinvloed worden door temperatuur en andere EM-uitstraling

### ACS712 module (team plantenbak)
Voor de plantenbakken werd een al gemaakte module gebruikt. Een teamlid had deze thuis nog op overschot en dit bespaarde ons  tijd omdat we zelf geen module moesten maken. Het werkingsprincipe is idem als bij team water: het is een hall-effect stroomsensor.

<img src="{{ '/assets/img/Plantenbak/acs712.png' | relative_url }}" alt="Hall effect" width="400" />

### ZXCT1107 Stroommonitor (team licht)

Voor team Licht gebeurt de powermeting via een stroommonitor: de ZXCT1107, een high-side stroommonitor van Diodes Incorporated. Alles wordt duidelijk uitgelegd in de bijgevoegde pdf.

 [Powermeting (PDF)](https://vertical-farming-ib3.github.io/assets/img/Licht/powermeting.pdf)
