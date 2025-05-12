---
title: "Home Assistant"
icon: fas fa-house-signal
order: 5
layout: default
---

# Dashboard

Bij onze slimme vertical farm hoort natuurlijk ook een interactief dashboard waar ook alle data wordt verzameld. 

Wanneer u surft naar het Home Assistant dashboard ([http://homeassistant.local:8123](http://homeassistant.local:8123)) of de Home Assistant app opent vindt u verschillende dashboards terug. Eventueel heeft u een wachtwoord nodig om in te loggen, deze wachtwoorden staan [hier](#wachtwoorden) opgesomd. U klikt links op 'Home' voor de toegang tot de hieronder besproken dashboards.

## Home

<img src="{{ '/assets/img/HomeAssistant/Home.png' | relative_url }}" alt="Home dashboard" />

Het 'Home' dashboard toont enkel de meest belangrijke zaken. Hier kunt u in een oogopslag zien of alle subsystemen van de vertical farm online zijn, wat de hoogtes van de reservoirs zijn en wat het energieverbruik is.

## Lades

<img src="{{ '/assets/img/HomeAssistant/Lade_1.png' | relative_url }}" alt="Lade dashboard" />

Elke lade krijgt zijn eigen dashboard. Hier bevindt zich alle info over die specifieke lade: het planttype, de bodemvochtigheid, temperatuur, CO2-gehalte, ... Ook het vermogen- en energieverbruik zijn hier terug te vinden. Verder kan op deze pagina makkelijk het lichttype gewijzigd worden.

## Energieverbruik

<img src="{{ '/assets/img/HomeAssistant/Energie.png' | relative_url }}" alt="Energie dashboard" />

Op dit dashboard vindt u het vermogenverbruik van het volledige systeem en alle subsystemen terug. Ook het energieverbruik wordt hier weergegeven. U kunt terugkeren in de tijd en het verbruik per lade analyseren.

## Watersysteem

<img src="{{ '/assets/img/HomeAssistant/HomeAssistantWater.png' | relative_url }}" alt="Watersysteem dashboard" />

Dit dashboard bevat enkele veiligheidschakelaars. Wanneer deze schakelaars zijn ingeschakeld krijgt het systeem 'controle' over de waterpompjes en wordt het waterpeil op hoogte gehouden. Deze schakelaars komen van pas bij het uitkuisen van de reservoirs of bij het verplaatsen van een lade. De schakelaar 'Pompen mixer' geeft aan of er water uit het water- en voedingsstoffenreservoir mogen gepompt worden naar het mixreservoir. De 'Pomp lade' geeft telkens aan of er water naar bijhorende lade mag gepompt worden.

Verder vindt u hier ook de hoogte van de reservoirs terug en de chemische waarden van het water in het mixreservoir. Ook het vermogenverbruik en energieverbruik worden weergegeven.

# Data aggregatie

In bovenstaande dashboards wordt telkens de meest recente data weergegeven. Het is ook mogelijk om historische data te bekijken. Hiervoor kunt op op eender welke grafiek/statistiek klikken in de dashboards. Als u dan op 'show more' klikt krijgt u een uitgebreide grafiek te zien waarbij u de begin- en einddata zelf kan kiezen.

# Automatisaties

De automatisaties worden slim aangestuurd vanuit de Home Assistant server. Op deze manier is er een centraal besturingssysteem dat toegang heeft tot alle in- en outputs van alle subsystemen. Indien u deze automatisaties (op eigen risico) wenst te wijzigen, dan doet u dat door naar de instellingen van de server te gaan en door te klikken naar 'services & automatisations'. Daar vindt u een overzicht van de automatisaties. Uiteraard dient u hiervoor in te loggen via het admin account (zie [wachtwoorden](#wachtwoorden)).

# Wachtwoorden

Met onderstaande wachtwoorden kan u met het lokaal WiFi-netwerk verbinden om daarna in te loggen op het Home Assistant-dashboard. 

| Toepassing           | Gebruikersnaam | Wachtwoord           |
|----------------------|----------------|----------------------|
| WiFi (IB3)           | /              | ingenieursbeleving3  |
| Home Assistant       | Gast           | ib3gast              |


Onderstaande login-gegevens dienen enkel gebruikt te worden code of instellingen te wijzigen.

| Toepassing           | Gebruikersnaam | Wachtwoord           |
|----------------------|----------------|----------------------|
| Raspberry Pi ssh     | ib3            | ingenieursbeleving3  |
| Home Assistant admin | ib3            | ingenieursbeleving3  |