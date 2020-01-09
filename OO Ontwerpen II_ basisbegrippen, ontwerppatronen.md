# OO Ontwerpen II: basisbegrippen, ontwerppatronen
## Basiskennis
**ontwerppatronen**
* Abstractie
* Encapsulatie
* Delegatie
* Modulariteit
* Hiërarchie
* Typing
## Abstractie
Een abstractie toont de essentiële functies van een object, dit hangt af van het gezichtspunt van de observator.
_Vb. een oma ziet haar kat anders dan de dierenarts_
## Encapsulatie
Encapsulatie verbergt de geïmplementeerde details van een object. De gebruiker van een object is enkel geconfronteerd met de buitenkant van een object, dat is zijn gedrag, niet de bron van het gedrag. In ontwerpen moet de abstractie van een object elke beslissing over de implementatie voorgaan.

Ook zorgt Encapsulatie ervoor dat het data beschermt die op de verkeerder manier kan worden toegevoeg. Met geëncapsuleerde data is elke berekening, toekenning beveiligd omdat de data niet direct toegangkelijk is.

> Dus Encapsulatie doet meer dan enkel informatie verbergen, het zorgt ervoor dat de methodes die je schrijft werken met de gebruikte data.

Encapsulatie scheidt je data van jouw applicatie z'n gdrag. Dan kan je controleren hoe elk onderdeel is gebruikt bij de rest van de applicatie.
## Delegatie
Delegatie is wanneer een object een bepaalde taak moet doen en i.p.v. deze direct uit te voeren, vraagt het aan een ander object om de taak (of een deel ervan) uit te voeren.

**voordeel:**
Delegatie maakt je code meer herbruikbaar.
Delegatie laat elk object zorgen voor z'n eigen taak. Dit betekent dat je objecten meet onafhankelijk van elkaar zijn (LOOSELY COUPLED)

> **Loosely coupled**
_Wanneer het object in je applicatie elk een specifieke opdracht te doen hebben, en enkel deze opdracht uitvoeren_ 


| Voordelen |
|----|
|loosely coupled objecten kunnen gebruikt worden van een andere applicatie en gemakkelijk hergebruikt worden in een andere, omdat ze niet verbonden zijn aan code van een andere object.|
|Loosely coupled applicaties zijn vaak meer flexibel en gemakkelijk te wijzigen.|

## Modulariteit
Wanneer men een complex systeem maakt is het gemakkelijk om onderelen (componenten, modules) te gebruiken.

Een module (zoals een klasse) verpergt de geïmplementeerde details. De gebruiker wordt enkel geconfronteerd met de interface van het onderdeel (component, module).

## Hiërarchie
Een hiërarchische set van abstracties helpt om het domein beter te verstaan en om de complexiteit van een probleem te verminderen.
### Deze kunnen we opdelen in: 
**klasse-hiërarchie**
SOORT VAN relatie (Overerving)
**Object-hierarchie**
ONDERDEEL VAN een relatie (compositie, aggreagatie)

### Stackoverflow:
> A **class** hierarchy probably refers to the structure composed by classes and inheritance links between them. For example, you may have class Car that inherits from class Vehicle, and so on. That makes up a class hierarchy.

> Now, when you create an instance of Car using the new operator, you obtain a Car object; there is no hierarchy involved. That is, there is no "two objects linked together through inhertance" like the two classes are. We can say that, at instantiation time, class hierarchies "get flattened".

>The phrase **object hierarchies**, therefore, often refers to whole/part structures. You may have another class, perhaps named Wheel, plus a reference from Car to Wheel so that cars may contain up to four wheels (imagine an array of wheels in a car object, or any other kind of container if you wish). This arrangement makes up a graph (rather than a hierarchy) of objects ar run time where whole/part (sometimes called "aggregation" or "composition") relationships are the major links. 

## Typing
Typing dwingt de klasse van een object, zodat object of een ander type niet kan veranderd worden.

Programmeertalen kunnen STRONGLY TYPED zijn (Ada, C ++) of aan de andere kant UNTYPED zijn (Smalltalk, Lisp). 

Programmeertalen die STRONGLY TYPED zijn, hebben meer bedieningsmechanismen dan niet-getypeerde talen, die meer flexibiliteit bieden.

Statische of dynamische binding verwijst naar het moment waarop het type variabelen en uitdrukkingen zijn gevestigd. 
* Statisch: op het moment van compilatie
* Dynamisch: tijdens uitvoering 

voorbeeld: wanneer een programma een lijst gebruikt die kan worden gesorteerd en het is alleen tijdens de uitvoering dat we weten wat er zal worden gesorteerd (woorden, getallen, studenten, ... ), kan de juiste sorteermethode alleen worden gekozen wanneer het exacte object bekend is (tijdens uitvoering).

Het feit dat één naam naar verschillende methoden verwijst, wordt polymorfisme genoemd.
