---
icon: fas fa-calendar-check
order: 6
---

> Under construction
{: .prompt-warning }

# 🌱 Vertical Farm Project "Plan-T" Logboek

---

## Sem 1: Voorbereidende fase

---

### 📸 Concepttekeningen
<div style="display: flex; gap: 10px;">
  <img src="/assets/img/Logboek//figure1.jpg" alt="Concept 1" width="200"/>
  <img src="/assets/img/Logboek//figure2.jpg" alt="Concept 2" width="200"/>
  <img src="/assets/img/Logboek//figure3.jpg" alt="Concept 3" width="200"/>
</div>

---

### 📅 16-10-2024: Brainstorming 💡
#### 🔄 Herstellen van het oude systeem
- **Vervangen van de drainage**.
- **Upgraden van de relays**.
- **Test van alternatieve substraten**.
- **Verbeteren van waterafvoer**.

#### 🏡 Nieuw systeem: Focus op modulariteit
We mikken op het **ontwerpen van een huisvriendelijke vertical farm**, geen industrieel ontwerp. Ons systeem moet **modulair** zijn.
- **Lade gebaseerd systeem** in een andere lade.
- **Sensoren geconnecteerd via de I2C bus**. <!---->
- **Gemeenschappelijke voedingsmodule** voor alle modules.
- **Plug-and-Play-systeem** voor een makkelijke setup.

#### 📅 Doel van de volgende sessie
- Het opstarten van het oude systeem.

---

### 📅 22-10-2024: Werken aan het oude systeem ⚙️
We verzamelden om het vorige systeem te **analyseren en herstarten**.

#### 🔌 Opstarten van het systeem
Gebruik makende van [deze handleiding](https://verticalfarmib3.github.io/inhoud/operation/), hebben we alles ingeschakeld:
- **ESPHome server** draait op `192.168.0.40:8123` van het CM3-netwerk. <!-- CM3-->
- **Grafana interface** is bereikbaar via poort `3000`.
- **Licht, pompen, ventilatoren en de mixer** zijn succesvol getest.
- **Automatisering** verzekert het in- en uitschakelen van het licht op de juiste ogenblikken.

#### 📦 De constructie herlocaliseren
1. Verwijderen van de **houten constructie**.
2. Het **glazen paneel** uit elkaar gehaald.
3. Het schoonmaken van **de oude planten en het interieur**.
4. Verplaatsen van het **houten frame**.
5. Installeren van het **aluminum frame**.

#### 🌱 Nieuwe zaadjes
We plantten verse zaadjes:
- Basilicum
- Dille
- Bieslook
- Oregano
- Peterselie
- Afrikaanse goudsbloemen

📌 **Geüpdatet lichttiming**: **08:00 - 20:00**
📌 **Geüpdatet ventilatortiming**: **5 minuten elke 30 minuten**

#### ❌ Gevonden problemen
- ⚠️ De mixer werkt slechts **enkele seconden** aan een stuk.
- ⚠️ **De drainage verstopt** door de rotswol.
- ⚠️ **Hete lijm was gebruikt** in de plaats van waterbestendige silicone.
- ⚠️ **Hoge opstartstroom** zorgt voor het aan elkaar lassen van de relaiscontacten.
- ⚠️ **Kapotte vochtsensoren** leiden tot overbewatering en lekken.

---

### 📅 19-11-2024: Planning fase 📝
Wachtende op onze **PCB's** hebben we:
- Een planning gemaakt
- Een taakverdeling gemaakt
Er is beslist om, voor een efficiënte realisatie van het project, een aantal gespecialiseerde teams op te delen.
Nl. een team plantenbak (sensoren bij de planten), water (toe- en afvoer), licht (groeilampen) en power (centrale voeding).
Het integreren zal dan met alle groepen samen gebeuren.

---

### 📅 17-12-2024: Presentatie & feedback
We stelden onze vooruitgang voor en vergaarden feedback in onze **ClickUp notities**.

---

## Sem 2: Praktische fase

---

### 📸 Concepttekeningen
<div style="display: flex; gap: 10px;">
  <!-- Tekeningen en 3D-modellen toevoegen -->
  <!-- <img src="/assets/img/Logboek/figure1.jpg" alt="Concept 1" width="200"/> -->
  <img src="/assets/img/Logboek/Sem2/figure1.png" alt="Concept 1" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure2.png" alt="Concept 2" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure3.png" alt="Concept 3" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure4.png" alt="Concept 4" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure5.png" alt="Concept 5" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure6.png" alt="Concept 6" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure7.png" alt="Concept 7" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure8.png" alt="Concept 8" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure9.png" alt="Concept 9" width="200" style="border-radius: 15px;"/>
  <img src="/assets/img/Logboek/Sem2/figure10.png" alt="Concept 10" width="200" style="border-radius: 15px;"/>
</div>

---

### 📅 Dinsdag 11-02-2025: De voorbereiding begint

Iedere groep (Team Plantenbak, Team Licht, Team Water) zijn begonnen met onderzoek en het ontwerpen van hun systemen. 
- We **hergebruikten zoveel mogelijk componenten** van de oude constructie.

##### Team Water: 
-	Teamverdeling schakels (+ herverdeling) + inlichten
-	Opstellen taakverdeling
-	Afwerken planning 
-	Besluiten welk systeem te gebruiken 
-	Bestellijst aanvullen

##### Team Plantenbak: 
- Teamverdeling (NFC en Plantenbak/Sensoren)
- Planning opstelling voor ons team
- Onderzoek naar sensoren, substraat, verluchting, planten, ...
- Bestelijst aanvullen
- Overleg met team water over watersysteem
  
##### Team Licht: 
- Teamverdeling (code, led PCB en driver PCB)
- onderzoek naar drivers, leds, ...
- Planning opstelling voor ons team

---

### 📅 Dinsdag 18-02-2025:
##### Team Water: 
-	Afronden bestellijst en opsturen 
-	Voeding bepaald
-	Onderzoek naar ADC voor de chemische probes
-	Start elektrisch schema PCB
-	Afwerken planning + indienen
-	Uitwerken toevoer/afvoer

##### Team Plantenbak: 
- Bepalen van sensoren
- Bestelijst afwerken
- Onderzoek naar NFC systeem
- Elektrisch schema voor PCB tekenen
- Uitdenken van vorm en manier om alle sensoren, ventielen, substraat, ...
  te verwerken in de plantenbak
- Vervoldigen planning van team plantenbak

##### Team Licht: 
- bepalen van leds + overleggen met mensen van licht over aantal leds en kleur
- bepalen van driver, datasheets lezen
- onderzoek koeling driver
- Bestelijst afwerken
  
---

### 📅 Dinsdag 25-02-2025: Eerste bestelling geplaatst! 🛒
We bestelden meerdere benodigde componenten voor onze constructie.
#### 📦 Gebruikte websites:
- Mouser
- RS Components
- TinyTronics
- PCBWay
- AliExpress

##### Team Water: 
-	Elektrisch schema verder afwerken
- Water schema afwerken
- Start binnenkast
-	Componenten besteld
-	Bedrijfsbezoek Colruyt

##### Team Plantenbak:
- Elektrisch schema verder afwerken
- Helpen met ontwerpen binnenkast
- Begin ontwikkeling NFC systeem
- Start van testen beschikbare sensoren
- Bestellijst indienen
- Bedrijfsbezoek Colruyt

##### Team Licht:
- Led en driver PCB design
- lezen datascheet driver + start code schrijven
- thermische berekeningen
- Bestellijst indienen
- Bedrijfsbezoek Colruyt

##### Team Power:
- Overleg met alle teams
- conectoren en voedingen kiezen
- bestellijst indienen
  
---

### 📅 Dinsdag 04-03-2025: Eerste zaaisel! 🌱 
##### Team Water: 
-	Elektrisch schema afgemaakt
-	PCB maken gestart
- Binnenkast opouwen  
-	Afbreken en recycleren oud systeem met team plantenbak
-	Bedrijfsbezoek Citymesh

##### Team Plantenbak: 
We zaaiden onze eerste zaadjes als een referentie, of misschien wel om ze binnenkort in onze werkende vertical farm te verpotten! 
### 🌿 Geplant:
- Basilicum
- Koriander
- Munt
- Oregano
- Bladsla

Bijkomend hebben we, 
- De oude constructie afgebroken.
- PCB ontwerpen
- Verder NFC systeem ontwikkelen
- Bedrijfsbezoek Citymesh

##### Team Licht:
- Led en driver PCB design
- code verder schrijven
-	Bedrijfsbezoek Citymesh

---

### 📅 Dinsdag 11-03-2025: PCB's besteld! 🎉
De PCB's zijn besteld bij **PCBWay**.

##### Team Water: 
-	Elektronische componenten testen
-	PCB-componenten gecontroleerd en PCB besteld
-	Pinout voor PCB beschreven
-	YAML voor watersysteem gestart
-	Gewerkt aan opbouw kast met team plantenbak

##### Team Plantenbak:
- Verder ontwikkelen van NFC systeem
- Beschikbare sensoren verder testen
- Algemene YAML code schrijven voor de plantenbak
- Gewerkt aan opbouw kast met team water
- PCB afgewerkt en gecontroleerd
- Opstarten van de github pages (website)

##### Team Licht:
- PCB afgewerkt en gecontroleerd
- Code verder schrijven
- Voorbereiden levering PCB
  
---

### 📅 Donderdag 13-03-2025:
##### Team Water: 
-	Overleg met chemie (meneer De Vreese)

---

### 📅 Zaterdag 15-03-2025: Wachten op bestellingen & voorbereiden opendeurdag 
##### Team Water: 
-	UV-C Lamp testen 
-	Bekijken wat nodig voor chemie
-	Verder werken aan YAML-code

##### Team Plantenbak: 
Met de meeste componenten besteld en Mr. Coppens die aan de kast werkt, werken wij aan:
- Het testen van sensoren, ESP's en YAML-code.
- Verder schrijven aan de algemen YAML-code voor de platnebakken
- Het zoeken naar bijkomende materialen: witte verf, verfborstels, kokosvezels, etc.---
- Volledig in orde brengen van de template voor de github pages (website)
- NFC verder ontwikkelen

##### Team Licht:
- CSBE challenge
- bestellen heatsinks en thermal pads
  
---

### 📅 Dinsdag 18-03-2025: De echte constructie komt dichterbij! :hammer:
##### Team Plantenbak: 
- Naar de Action om verf, borstels en andere benodigdheden.
- Verder werken aan de github pages (website)
- YAML-code verder schrijven
- NFC systeem verder ontwikkelen
- Extra planten gezaaid
- Overleg met team water voor uitwerking watersysteem in plantenbak

##### Team Water: 
- Kalibratie van de ion-sensoren nagekeken.
- YAML-code afgewerkt
-	Afgewerkt kastframe met team plantenbak
- Stroomsensoren
  
##### Team Licht: 
- LDO bestellen
- Voorbereiding componenten PCB
- Code verder schrijven

---

### 📅 Donderdag 20-03-2025:
##### Team Water: 
-	Chemie: kalibratievloeistoffen gemaakt

---

### 📅 Vrijdag 21-03-2025: Een kast om in te werken 🎆
##### Team Water: 
-	Kast afgewerkt met team licht
-	Kast verplaatst naar B225

---

### 📅 Dinsdag 25-03-2025:
##### Team Water: 
-	Verder gewerkt aan kast (indeling uitgewerkt, laden gerepareerd, …)
-	Materiaal gekocht in de Gamma
-	Oude profielen uit elkaar gehaald en nieuwe profielen in elkaar gezet
-	Plantenbakken hellend gemaakt
-	Indeling uitgedacht van de la 
-	PCB's gesoldeerd
-	Probehouder ontworpen en geprint
  
##### Team Plantenbak: 
- PCB's solderen
- Kast wit schilderen
- NFC systeem verder ontwikkelen
- YAML-code verder schrijven
- 3D prints voor in platenbak ontwerpen
- In overleg de indeling van de plantenbak verder uitgedacht
- Extra aanpassingen aan de algemene structuur van de github pages (website)

##### Team Licht: 
- bestukken led PCB's 
- uittesten led PCB's
- Code verder schrijven

---

### 📅 Woensdag 26-03-2025: 
##### Team Water: 
-	Ultrasone sensorhouders ontworpen en geprint
-	PCB programmeren en verbinden met HomeAssistant

---

### 📅 Dinsdag 01-04-2025:
##### Team Water: 
-	Chemische probes gekalibreerd
-	Stroomsensor gekalibreerd
-	Documentatie kalibraties op Github aangevuld
-	Probes, pompjes, tubes gemonteerd en aangesloten
-	Hoogtesensoren gemonteerd
-	Afvoeren in plantenlades bevestigd
-	Pompen aangesloten 
- Buizen leggen voor de toevoer

##### Team Plantenbak: 
-	Elektronica samen beginnen brengen
-	Sensoren afhankelijk testen via yaml
-	3D-print ontwerpen om onze elektronica in te steken en een houder voor NFC-kaarten

##### Team Licht: 
- bestukken driver PCB's 
- uittesten driver PCB's
- Code verder schrijven

---

### 📅 Vrijdag 04-04-2025:
##### Team Water: 
-	Nagekeken realisatie buitenkast

---

### 📅 Paasvakantie: 07-04-2025 tot en met 20-04-2025
##### Team Water: 
- Verder gewerkt aan afvoer: montage + boren regenpijp
-	Gekeken naar buitenkast
-	Nagemeten kapotte probe
-	Test op lekkages + lekken opgelost
-	Waterproofen
-	Hoogtesensoren aangesloten en gekalibreerd
-	Houder voor middelste hoogtesensor ontworpen
-	Kabels in kabelhulzen gestoken
-	Kraantjeswater en voedingsstoffen uitgemeten
-	Reservoirs gevuld, pompjes getest, mixer getest, circulatie getest

##### Team Plantenbak: 
- Houdersysteem voor plantenpotjes gemaakt
- Volledige elekronicasysteem verbonden en getest
- Lang bugfixen op probleem bij relais ( Schottky-diode )
- Nieuwe batch plantjes gezaaid

##### Team Licht: 
- Led PCB's monteren in de lades
- Driver + led PCB's te samen testten
- Code verder schrijven

---

### 📅 Dinsdag 22-04-2025:
##### Team Water: 
- Site verderwerken
- Power aansluiten pcb water
- Automatisaties schrijven (circulatie, mengreservoir bijvullen, waarschuwingen laag waterniveau, ventilatie, water pompen naar lades)
- Reservoirs uitkuisen
- Hoogtesensoren op nieuwe brackets gemonteerd
-	Verdergewerkt aan frame
-	Bekeken PH-sensor
-	Acryl gesneden (voorkomen stilstaand water).
-	Samengezeten andere groepen
-	Besproken verdere aanpak project

##### Team Plantenbak: 
- Site verder afwerken
- Elektronica in de bakken gefit
- Dubbele bodem in de bakken gekit 
- Automatisatie schrijven

##### Team Licht: 
- Led + driver PCB's monteren in de lades
- Alle PCB's uittesten en debuggen
- Kleine aanpassingen code + uittesten

##### Team Power:
- Voedingen aan binnnenkast bevestigen
- Fuse en schakelaar aansluiten
- Eerste conectoren solderen
  
---

### 📅 Woensdag 23-04-2025:
##### Team Water:
- Dashboards in Home Assistant beginnen maken
- Connectoren powergedeelte verder geplaatst
  
##### Team Plantenbak:  
- Kabels gelabeld
- Bugfixing: waarom werkt onze schakeling niet meer in de kast?
  - ESP1 heeft plots kortsluiting?
  - ESP2 kan geen verbinding meer maken met esphome

---

### 📅 Donderdag 24-04-2025:
##### Team Water:
- Herkalibratie probes

---

### 📅 Vrijdag 25-04-2025:
##### Team Plantenbak:  
- Bugfixing: beide bakken terug werkende gekregen 

---

### 📅 Weekend 26-04-2025 tot en met 27-04-2025:
##### Team Plantenbak:  
- De bakken een dubbele bodem geven, poging twee ( vorige waren niet waterdicht )
- Solenoid valve werd vervangen door een regentonkraantje
  - De druk van het laagje water was niet groot genoeg om de valve te kunnen sturen

---

### 📅 Dinsdag 29-04-2025:
##### Team Water: 
- pH-probe gekalibreerd en geïntegreerd
- Probleem PCB debuggen en oplossen (Buck converter ground)
- Dashboard Home Assistant afgewerkt (water)
- Website verder aanpassen
- Dimitri helpen met onderkant en linkerzijde kast
- Andere groepen helpen met debuggen
- Start eindpresentatie
- Waterafvoer, eb-vloed lade

##### Team Plantenbak: 
- Elektronica nog een laatste keer testen en in de lades bevestigen
- Verder werken aan de site
- Beginnen aan PowerPoint
- Plantjes in de bakken zetten

##### Team Licht: 
- Driver PCB's debuggen
- Laatste aanpassingen aan code
- PCB etsen van power meting
- Laatste PCB's monteren in lade
- Presentatie verdediging

---

### 📅 Woensdag 30-04-2025: 
##### Team Water: 
- Verder aan waterafvoer plantenlades gewerkt
- Ontbrekende slangklemmen aan pompen bevestigd
- Afwerkingen Home Assistant (verfijning automatisaties/dashboard/...)
- Probleem geïdentificeerd met de aquariumpomp (mixer)

---

### 📅 Dinsdag 06-05-2025: 

- Geïntegreerde test
- Voorbereiding eindpresentatie

##### Team Water: 
- Afwerken Frame buitenkast + start afwerking buitenkast
- Afwerkingen binnenkast
- Site + git
- Testen + verbeteringen
- Werken aan presentatie
- Afwerken power aansluiting
- Afwerken Home Assistant dashboard
- Verderzoeken naar probleem pH en mixer

##### Team Plantenbak: 
- Laatste plantjes in de bakken zetten
- Verder werken aan PowerPoint
- Verder werken aan site
- Sensoren kalibreren

##### Team Licht:
- Lade afwerken en uittesten
- Laatste aanpassingen aan code
- PCB etsen van power meting
- presentatie afwerken

##### Team Power:
- Laatste conectoren solderen
- Krimpkousen over alle connecties plaatsen
  
---

### 📅 Woensdag 07-05-2025: 
##### Team Water en Plantenbak: 
- Ophalen en bevestigen afwerking buitenkast 

##### Team Licht:
- Fixen lade 2

---

### 📅 Donderdag 08-05-2025: 
##### Team Water en Plantenbak: 
- Kast proper maken en volledig installeren voor opendeurdag op zaterdag 

---

### 📅 Vrijdag 09-05-2025: 
##### Team Water, Plantenbak en Licht: 
- De kast getest
- De finale plantjes geplant in de bak
- De rockwolbak werd volledig vervangen door kokosvezel
- De setup klaargezet voor op de opendeurdag (tv etc.)
- Last-minute probleempjes opgelost

---

### 📅 Zaterdag 10-05-2025: 
##### Team Water, Plantenbak en Licht: 
- De kast ligt nu officieel aan. 

---

### 📅 Dinsdag 13-05-2025:
- Eindpresentatie

---

<!-- Komt er nog ergens een verklarende woordenlijst?-->
