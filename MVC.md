# Model-View-Controller (MVC)

## Inleiding
  - Design Patterns zijn de sleutel tot MVC.
  - Het geheim van MVC: `Het zijn een paar patterns die zijn samengevoegd`!

Controller > (verander je toestand) > Model
 - Het model bevat alle gegevens, de toestand en de logica van de applicatie. Het model is zich niet bewust van de view en de controller, hoewel het een interface heeft om zijn toestand te veranderen en op te vragen, en het kan berichten over veranderingen in zijn toestand naar observers sturen.
 
Model > (ik ben veranderd) > View
 - De view geeft je een presentatie van het model. De view krijgt gewoonlijk rechtstreeks van het model de toestand en gegevens die het nodig heeft voor de presentatie.

View > (De gebruiker deed iets) > Controller
 - De controller krijg input van de gebruiker en zoek uit wat dat betekent voor het model.

## Naar MVC kijken met een paternsbril
### Strategy
De controller is de strategy voor de view; het is een object dat weet hoe de gebruikersacties moet afhandelen.

We kunnen de view ander gedrag geven door van controller te veranderen.

De view delegeert het afhandelen van gebruikersacties aan de controller.

> De view maakt zich alleen zorgen om de presentatie, de controller maakt zich zorgen om de vertaling van de gebruikersinvoer naar acties die betrekking hebben op het model

### Observer
Model -> Observable (subject)
view/controller -> Observers

Al deze observers krijgen bericht als de toestand van het model verandert.

> Het model heeft geen afhankelijkheden met views of controllers. Elk object dat geïnteresseerd is in de toestandsverandering van het model meldt zich aan bij het model als een observer.

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.
### composite
> De view is een composite van GUI-componenten (labels, knoppen, invoervlakken, etc.). De toplevelcomponent bevat andere componenten, die weer andere componenten bevatten en zo door tot je de leaf nodes krijgt.

=> voorbeeld vanaf slide 4-5


