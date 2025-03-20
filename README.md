# Project Recipe

## Opdrachten

### Opdracht 1 - Database ontwerp

- Maak op basis van onderstaande userstories en het SQL-bestand een database ontwerp. 

### Opdracht 2 - Repository

- Maak gebruik van de repository: https://github.com/NOVA-college-Haarlem/recipe-project-blok-3
- Fork de repository
- Clone de repository

### Opdracht 3 - Website

- Maak een website voor een receptenboek.

### Opdracht 4 - Controleren

- Controleer je website door gebruik te maken van de rubric.

## Userstories

### Overzichtspagina

# User Stories Recipe Book

## Overzichtspagina

**Als een** bezoeker  
**Wil ik** een overzicht zien van alle beschikbare recepten  
**Zodat ik** snel kan bladeren door verschillende recepten

**Als een** bezoeker  
**Wil ik** basisinformatie zien van elk recept (naam, bereidingstijd, thumbnail afbeelding)  
**Zodat ik** een eerste indruk krijg zonder naar de detailpagina te hoeven gaan

**Als een** bezoeker  
**Wil ik** op een recept kunnen klikken  
**Zodat ik** naar de detailpagina kan gaan voor meer informatie

## Filtering

**Als een** bezoeker  
**Wil ik** kunnen filteren op maaltijdtype (ontbijt, lunch, diner, dessert, etc.)  
**Zodat ik** alleen recepten zie die passen bij het moment van de dag

**Als een** bezoeker  
**Wil ik** kunnen filteren op moeilijkheidsgraad (makkelijk, gemiddeld, moeilijk)  
**Zodat ik** recepten vind die passen bij mijn kookvaardigheid

## Overige Functionaliteiten

**Als een** bezoeker  
**Wil ik** kunnen sorteren op bereidingstijd (van kort naar lang of lang naar kort)  
**Zodat ik** recepten kan vinden die passen bij de tijd die ik beschikbaar heb

**Als een** bezoeker  
**Wil ik** zien hoeveel resultaten er beschikbaar zijn binnen mijn gekozen filters  
**Zodat ik** weet hoeveel opties ik heb

```sql
- Database schema voor Recipe Book met één tabel

-- Recepten tabel
CREATE TABLE recepten (
    id INT PRIMARY KEY AUTO_INCREMENT,
    naam VARCHAR(100) NOT NULL,
    maaltijdtype VARCHAR(50) NOT NULL,
    moeilijkheidsgraad VARCHAR(50) NOT NULL,
    bereidingstijd INT NOT NULL, -- in minuten
    aantal_personen INT NOT NULL,
    beschrijving TEXT,
    ingredienten TEXT,
    bereidingswijze TEXT,
    thumbnail_url VARCHAR(255)
);

-- Voorbeelddata invoegen
INSERT INTO recepten (naam, maaltijdtype, moeilijkheidsgraad, bereidingstijd, aantal_personen, beschrijving, ingredienten, bereidingswijze, thumbnail_url) VALUES 
('Pasta Carbonara', 'Diner', 'Gemiddeld', 30, 4, 'Een romige Italiaanse pastaschotel met spek.', '400g spaghetti, 200g spekblokjes, 2 eieren, 50g Parmezaanse kaas, 2 teentjes knoflook, zwarte peper, zout', 'Kook de pasta volgens de aanwijzingen op de verpakking. Bak ondertussen de spekblokjes knapperig. Meng de eieren met de kaas. Meng de pasta met de spekblokjes en voeg het ei-kaasmengsel toe. Roer goed door zodat een romige saus ontstaat.', 'carbonara.jpg'),
('Avocado Toast', 'Ontbijt', 'Makkelijk', 10, 1, 'Een snel en gezond ontbijt met avocado en toast.', '1 rijpe avocado, 2 sneetjes volkorenbrood, citroensap, zeezout, zwarte peper, rode pepervlokken', 'Toast het brood. Prak de avocado en breng op smaak met citroensap, zout en peper. Verdeel over de toast en bestrooi met rode pepervlokken.', 'avocadotoast.jpg'),
('Chocolade Brownie', 'Dessert', 'Makkelijk', 45, 9, 'Smeuïge chocolade brownies met een krokant laagje.', '200g pure chocolade, 175g boter, 325g suiker, 130g bloem, 3 eieren, 1 tl vanille-extract', 'Verwarm de oven voor op 180°C. Smelt chocolade en boter. Meng met suiker, eieren en vanille. Voeg bloem toe. Giet in een bakvorm en bak 25-30 minuten.', 'brownie.jpg'),
('Caesar Salade', 'Lunch', 'Gemiddeld', 20, 2, 'Een klassieke salade met romige dressing en knapperige croutons.', '1 krop Romaine sla, 100g Parmezaanse kaas, 2 sneetjes oud brood, 1 teentje knoflook, 1 ei, 2 ansjovisfilets, 2 el citroensap, 5 el olijfolie, 1 tl mosterd', 'Maak croutons van het brood. Maak de dressing van ei, ansjovis, knoflook, mosterd, citroensap en olijfolie. Snijd de sla en meng met dressing, croutons en geschaafde Parmezaanse kaas.', 'caesarsalade.jpg'),
('Tomatensoep', 'Lunch', 'Makkelijk', 30, 4, 'Romige tomatensoep gemaakt van verse tomaten.', '1kg rijpe tomaten, 1 ui, 2 teentjes knoflook, 1 wortel, 1 stengel bleekselderij, 1l groentebouillon, 100ml slagroom, basilicum, olijfolie, zout, peper', 'Fruit ui, knoflook, wortel en bleekselderij. Voeg tomaten en bouillon toe. Laat 20 minuten sudderen. Pureer de soep en voeg room toe. Breng op smaak met zout en peper.', 'tomatensoep.jpg'),
('Lasagne', 'Diner', 'Moeilijk', 90, 6, 'Laagjes pasta met een rijke gehaktsaus en bechamelsaus.', '12 lasagnebladen, 500g rundergehakt, 2 uien, 2 teentjes knoflook, 2 wortelen, 2 stengels bleekselderij, 800g tomatenblokjes, 50g boter, 50g bloem, 500ml melk, 200g geraspte kaas, nootmuskaat, zout, peper', 'Maak de gehaktsaus. Maak de bechamelsaus. Laag afwisselend pasta, gehaktsaus en bechamelsaus in een ovenschaal. Eindig met bechamelsaus en kaas. Bak 30 minuten in de oven op 180°C.', 'lasagne.jpg'),
('Smoothie Bowl', 'Ontbijt', 'Makkelijk', 10, 1, 'Een voedzame ontbijtkom met fruit en toppings.', '1 bevroren banaan, 100g bevroren bessen, 120ml amandelmelk, 1 el chiazaad, vers fruit voor topping, 1 el granola, 1 tl honing', 'Blend de bevroren banaan, bessen en amandelmelk tot een dikke smoothie. Giet in een kom. Top af met chiazaad, vers fruit, granola en een druppel honing.', 'smoothiebowl.jpg'),
('Chicken Curry', 'Diner', 'Gemiddeld', 45, 4, 'Een aromatische curry met kip en groenten.', '600g kipfilet, 2 uien, 3 teentjes knoflook, 3 el currypoeder, 400ml kokosmelk, 400g tomatenblokjes, 2 paprika\'s, 200g sperziebonen, verse koriander, jasmijnrijst', 'Bak de kip. Fruit ui en knoflook. Voeg currypoeder toe en bak kort mee. Voeg tomatenblokjes en kokosmelk toe. Voeg kip en groenten toe en laat sudderen tot gaar. Serveer met rijst.', 'chickencurry.jpg'),
('Tiramisu', 'Dessert', 'Moeilijk', 240, 8, 'Een Italiaans dessert met lagen van koffie-gedrenkte biscuits en mascarpone.', '250g mascarpone, 3 eieren, 100g suiker, 300g lange vingers, 250ml sterke koffie, 2 el amaretto, cacaopoeder', 'Scheid de eieren. Klop de eigelen met suiker, voeg mascarpone toe. Klop de eiwitten stijf en spatel door het mascarpone-mengsel. Doop de lange vingers in koffie met amaretto. Laag afwisselend koekjes en mascarpone-mengsel. Bestrooi met cacao. Laat minimaal 4 uur opstijven in de koelkast.', 'tiramisu.jpg'),
('Griekse Salade', 'Lunch', 'Makkelijk', 15, 2, 'Een frisse salade met feta en olijven.', '1 komkommer, 3 tomaten, 1 rode ui, 150g feta, 100g zwarte olijven, 1 groene paprika, 2 el olijfolie, 1 el rode wijnazijn, 1 tl oregano, zout, peper', 'Snijd alle groenten in stukken. Verkruimel de feta erover. Voeg olijven toe. Maak een dressing van olijfolie, azijn, oregano, zout en peper. Giet over de salade.', 'grieksesalade.jpg'),
('Pompoensoep', 'Lunch', 'Gemiddeld', 40, 4, 'Een romige seizoenssoep van pompoen.', '1 butternut pompoen, 1 ui, 2 teentjes knoflook, 1 wortel, 1l groentebouillon, 100ml slagroom, nootmuskaat, zout, peper, pompoenpitten', 'Bak ui, knoflook en wortel. Voeg pompoen in blokjes toe en bak kort mee. Voeg bouillon toe en laat 30 minuten sudderen. Pureer de soep en voeg room toe. Breng op smaak en garneer met pompoenpitten.', 'pompoensoep.jpg'),
('Appeltaart', 'Dessert', 'Moeilijk', 90, 8, 'Een klassieke Nederlandse appeltaart.', '300g bloem, 200g koude boter, 150g suiker, 1 ei, snufje zout, 1kg appels, 2 tl kaneel, 50g rozijnen, 50g suiker', 'Maak deeg van bloem, boter, suiker, ei en zout. Laat 30 minuten rusten. Schil en snijd de appels. Meng met kaneel, rozijnen en suiker. Bekleed een taartvorm met 2/3 van het deeg. Vul met appelmengsel. Dek af met repen van het resterende deeg. Bak 50-60 minuten op 170°C.', 'appeltaart.jpg'),
('Sushi Rolls', 'Diner', 'Moeilijk', 60, 4, 'Zelfgemaakte sushi rolls met verse vis en groenten.', '300g sushirijst, 60ml rijstazijn, 4 nori vellen, 1 komkommer, 1 avocado, 200g zalm, 200g tonijn, wasabi, sojasaus, gember', 'Kook de rijst en meng met rijstazijn. Leg een nori vel op een bamboe matje. Verdeel rijst over het vel. Leg vis en groenten in een rij. Rol strak op met het matje. Snijd in stukken. Serveer met wasabi, sojasaus en gember.', 'sushi.jpg'),
('Omelet', 'Ontbijt', 'Makkelijk', 10, 1, 'Een eenvoudige en voedzame omelet.', '3 eieren, 30ml melk, 50g geraspte kaas, 50g champignons, 50g spinazie, 1 tomaat, zout, peper, boter', 'Klop de eieren met melk, zout en peper. Bak champignons en spinazie. Giet het eimengsel erover. Bestrooi met kaas. Dek af tot de bovenkant gestold is. Vouw dubbel en serveer met plakjes tomaat.', 'omelet.jpg'),
('Quinoa Bowl', 'Lunch', 'Gemiddeld', 30, 2, 'Een voedzame kom met quinoa, groenten en eiwitten.', '200g quinoa, 400ml groentebouillon, 1 avocado, 100g kikkererwten, 100g cherrytomaatjes, 100g komkommer, 50g feta, 2 el olijfolie, 1 el citroensap, verse munt, zout, peper', 'Kook quinoa in bouillon. Laat afkoelen. Snijd alle groenten. Meng met quinoa. Maak dressing van olijfolie, citroensap, zout en peper. Meng door de salade. Garneer met feta en munt.', 'quinoabowl.jpg'),
('Chocolademousse', 'Dessert', 'Gemiddeld', 180, 4, 'Een luchtige chocolademousse.', '200g pure chocolade, 4 eieren, 50g suiker, 200ml slagroom, 1 tl vanille-extract', 'Smelt de chocolade au bain-marie. Scheid de eieren. Klop de eiwitten stijf met suiker. Klop de slagroom. Meng de eidooiers door de gesmolten chocolade. Vouw de slagroom en eiwitten erdoor. Laat minimaal 3 uur opstijven in de koelkast.', 'chocolademousse.jpg');

```

## Beoordelingscriteria

| Criterium                     | Onvoldoende                                 | Voldoende                                       | Goed                                                                        |
| ----------------------------- | ------------------------------------------- | ----------------------------------------------- | --------------------------------------------------------------------------- |
| Basisweergave van recepten    | Recepten worden niet of nauwelijks getoond  | Recepten worden correct weergegeven             | Recepten worden aantrekkelijk weergegeven met duidelijke visuele hiërarchie |
| Filter op maaltijdtype        | Filter werkt niet of met ernstige fouten    | Filter werkt, maar heeft kleine gebreken        | Filter werkt perfect en is gebruiksvriendelijk                              |
| Filter op moeilijkheidsgraad  | Filter werkt niet of met ernstige fouten    | Filter werkt, maar heeft kleine gebreken        | Filter werkt perfect en is gebruiksvriendelijk                              |
| Sortering op bereidingstijd   | Sortering werkt niet of met ernstige fouten | Sortering werkt, maar heeft kleine gebreken     | Sortering werkt perfect en is gebruiksvriendelijk                           |
| Doorklikken naar detailpagina | Links werken niet of met ernstige fouten    | Links werken, maar zijn niet optimaal geplaatst | Links werken perfect en zijn intuïtief                                      |
Detailpagina
| Criterium | Onvoldoende | Voldoende | Goed |
| Weergave van recept details | Details worden niet of nauwelijks getoond | Details worden correct weergegeven | Details worden uitgebreid en aantrekkelijk weergegeven |
| Teruglink naar overzichtspagina | Link werkt niet of is niet aanwezig | Link is aanwezig en werkt | Link is duidelijk zichtbaar en gebruiksvriendelijk |
## Algemene aspecten

| Criterium              | Onvoldoende                                | Voldoende                                      | Goed                                           |
| ---------------------- | ------------------------------------------ | ---------------------------------------------- | ---------------------------------------------- |
| Database connectie| Query's werken niet of met ernstige fouten | Query's werken, maar zijn niet geoptimaliseerd | Query's werken goed en zijn geoptimaliseerd    |  | Responsief ontwerp | Website werkt niet op verschillende schermgroottes | Website werkt op verschillende schermgroottes, maar heeft kleine problemen | Website is volledig responsief en werkt uitstekend op alle schermgroottes |
| Code kwaliteit    | Rommelige code met veel fouten             | Redelijk nette code met enkele fouten          | Nette, goed gestructureerde code zonder fouten |

## Beoordeling

De beoordeling wordt gebaseerd op de volgende niveaus:
- **Onvoldoende**: Het project voldoet niet aan de basisvereisten
- **Voldoende**: Het project voldoet aan de basisvereisten
- **Goed**: Het project voldoet aan alle vereisten en toont extra aandacht voor gebruikerservaring en code kwaliteit
