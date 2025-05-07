---
title: "Home Assistant"
icon: fas fa-house-signal
order: 5
layout: default
---

> Under construction
{: .prompt-warning }
> 


<!-- Algemene info over HomeAssistant dashboard en data agregatie-->


# Dashboard

Wanneer u surft naar het Home Assistant dashboard (http://homeassistant.local:8123) of de Home Assistant app opent vindt u verschillende dashboards terug. Eventueel heeft u een wachtwoord nodig om in te loggen, deze wachtwoorden staan [hier](#wachtwoorden) opgesomd. U klikt links op 'Home' voor de toegang tot de hieronder besproken dashboards.

## Home

<!-- Afbeelding Home dashboard-->

Het 'Home' dashboard toont enkel de meest belangrijke zaken. Hier kunt u in een oogopslag zien of alle subsystemen van de vertical farm online zijn, wat de hoogtes van de reservoirs zijn en wat het energieverbruik is. Ook enkele belangrijke parameters van de plantenlades worden hier meegegeven.

## Lades

<!-- Afbeelding Lade dashboard-->

<!-- Uitleg Lade dashboard-->

## Energieverbruik

<!-- Afbeelding energieverbruik dashboard-->

Op dit dashboard vindt u het vermogenverbruik van het volledige systeem en alle subsystemen terug. Ook het energieverbruik wordt hier weergegeven. U kunt terugkeren in de tijd en het verbruik per lade analyseren.

## Watersysteem

<img src="{{ '/assets/img/HomeAssistant/HomeAssistantWater.png' | relative_url }}" alt="Watersysteem dashboard" />

Dit dashboard bevat enkele veiligheidschakelaars. Wanneer deze schakelaars zijn ingeschakeld krijgt het systeem 'controle' over de waterpompjes en wordt het waterpeil op hoogte gehouden. Deze schakelaars komen van pas bij het uitkuisen van de reservoirs of bij het verplaatsen van een lade. De schakelaar 'Pompen mixer' geeft aan of er water uit het water- en voedingsstoffenreservoir mogen gepompt worden naar het mixreservoir. De 'Pomp lade' geeft telkens aan of er water naar bijhorende lade mag gepompt worden.

Verder vindt u hier ook de hoogte van de reservoirs terug en de chemische waarden van het water in het mixreservoir. Ook het vermogenverbruik en energieverbruik worden weergegeven.

# Data aggregatie

In bovenstaande dashboards wordt telkens de meest recente data weergegeven. Het is ook mogelijk om historische data te bekijken. Hiervoor kunt op op eender welke grafiek/statistiek klikken in de dashboards. Als u dan op 'show more' klikt krijgt u een uitgebreide grafiek te zien waarbij u de begin- en einddata zelf kan kiezen.

# Automatisaties

<!-- Uitleg over de automatisaties -->

# Wachtwoorden

| Toepassing           | Gebruikersnaam | Wachtwoord           |
|----------------------|----------------|----------------------|
| WiFi (IB3)           | /              | ingenieursbeleving3  |
| Home Assistant       | Gast           | ib3gast              |