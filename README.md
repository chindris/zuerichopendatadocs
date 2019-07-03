# Zurich Tourismus Open Data API

## Introduction

This document describes the open data API of zuerich.com for retrieving information about restaurants / cafes, places and accommodation locations published on the site. Each of these entities are also tagged with one or more categories. The following objects can be retrieved via the API:
- Restaurants / Cafes
- Places
- Accommodations

## API Endpoints

The main endpoint of the api is located at https://www.zuerich.com/data

By just calling the endpoint, without any other parameters, the result is a list of all the available categories. The category items are stored as a hierarchical tree, so each of the category item has also a reference to its parent. If the parent is 0, then the category is a root item. An excerpt from the result list can be seen bellow:

```json
[
{
    id: "74",
    parent: "0",
    name: {
        de: "Gastronomie",
        en: "Gastronomy",
        fr: "Gastronomie",
        it: "Gastronomia"
    },
    path: "/data/gastronomy"
},
{
    id: "101",
    parent: "74",
    name: {
        de: "Restaurants",
        en: "Restaurants",
        fr: "Restaurants",
        it: "Ristoranti"
    },
    path: "/data/gastronomy/restaurants"
},
{
    id: "165",
    parent: "101",
    name: {
        de: "Küche",
        en: "Cuisine",
        fr: "Cuisine",
        it: "Cucina"
    },
    path: "/data/gastronomy/restaurants/cuisine"
},
{
    id: "193",
    parent: "165",
    name: {
        de: "Amerikanisch",
        en: "American",
        fr: "Américaine",
        it: "Americano"
    },
    path: "/data/gastronomy/restaurants/cuisine/american"
}]
```

The **name** field is actually an object which contains the name of the category item in all the four languages of the site: German(de), English (en), French (fr) and Italian (it). The value of the **path** field contains the URL that can be used to retrieve all the objects tagged with the respective category item.

By appending the path of a category to the API endpoint, you can get all the objects which are tagged with that respective category. For example, to get all the objects tagged with *American*, the following path can be used https://www.zuerich.com/data/gastronomy/restaurants/cuisine/american. The result would be a list of all the American cuisine restaurants, for example:

```json
[{
    id: "403242",
    @context: "https://schema.org/",
    @type: "LocalBusiness",
    copyright: {
        en: "Zurich Tourism www.zuerich.com",
        de: "Zürich Tourismus www.zuerich.com",
        it: "Zürich Tourismo www.zuerich.com",
        fr: "Zürich Tourisme www.zuerich.com"
    },
    cc: "BY-SA",
    category: [
        "Restaurants",
        "Cuisine",
        "American"
    ],
    name: {
        de: "The High Heel Gourmet Café",
        en: "The High Heel Gourmet Café",
        fr: "The High Heel Gourmet Café",
        it: "The High Heel Gourmet Café"
    },
    disambiguatingDescription: {
        de: "Lecker, gesund und ohne Schnickschnack, dafür auf höchstem Niveau: Ein kleiner Geheimtipp in Wiedikon.",
        en: "Delicious, healthy, and without frills yet still at a first-class culinary level: a small insider tip in Wiedikon.",
        fr: "Délicieux, sain et sans chichi mais haut de gamme : la bonne adresse de Zurich Wiedikon.",
        it: "Buono, sano, senza fronzoli, ma di altissimo livello: una chicca di Wiedikon."
    },
    description: {
        de: "<p>Die Sonne Kaliforniens geniessen – nun ja, das ist in Zürich nicht ganz einfach. Aber wer das The High Heel Gourmet Café im hübschen Quartier Wiedikon besucht, kommt dem entspannten Gefühl Kaliforniens sehr nahe.</p><p>Das kleine Restaurant begeistert durch seine Herzlichkeit und mit kreativen Gerichten, die südamerikanische Klassiker mit asiatischen Einflüssen paaren: Hühnchen Jambalaya, diverse Acai Bowls oder vegetarisches Loco Moco sind nur einige der Köstlichkeiten, welche die Gäste – zumindest im Geiste – in südliche Gefilde entführen.</p><p>Das kleine Restaurant im Vintage-Stil verfügt über eine Sommerterrasse und begrüsst hungirge Mäuler unter der Woche von früh bis spät sowie am Samstagabend.</p>",
        en: "<p>Enjoy the Californian sun – that is not exactly easy in Zurich. But if you visit The High Heel Gourmet Café in the pretty Wiedikon district, you will come very close to the laid-back Californian feeling.</p><p>The little restaurant delights with its friendly hospitality and its creative dishes, which combine South American classics with Asian influences: Chicken Jambalaya, various acai bowls, and vegetarian Loco Moco are just some of the delicacies that – at least in spirit – transport guests to southern climes.</p><p>The vintage-style restaurant also has a summer terrace and welcomes hungry guests during the week from early to late, as well as on Saturday evening.</p>",
        fr: "<p>Profiter du soleil de Californie ? Pas simple à Zurich ! Mais vous approcherez cette sensation californienne si vous vous rendez au The High Heel Gourmet Café dans le magnifique quartier de Wiedikon.</p><p>Ce petit restaurant séduit par sa cordialité et ses plats créatifs – une combinaison de classiques sud-américains et d’influences asiatiques : Jambalaya de poulet, divers bols d’açaï ou loco moco végétarien sont quelques-uns des délices qui vous transporteront dans des contrées méridionales – du moins en pensée.</p><p>Ce petit restaurant vintage avec terrasse d’été accueille les clients souhaitant se restaurer en semaine du matin au soir et le samedi en soirée. </p>",
        it: "<p>Godersi il sole della California! A Zurigo non è così semplice. Eppure, chi visita il The High Heel Gourmet Café nel grazioso quartiere di Wiedikon, si avvicina parecchio alla spensieratezza californiana.</p><p>Il piccolo ristorante colpisce per la sua cordialità e i suoi piatti creativi, che combinano classici sudamericani e influenze asiatiche: galletto Jambalaya, diverse Acai Bowl o Loco Moco vegetariano sono alcune delle prelibatezze che catapultano gli ospiti al caldo.</p><p>Allestito in stile vintage, il ristorantino vanta una terrazza estiva e, in settimana, accoglie i suoi ospiti da mattina a sera, di sabato solo di sera.</p>"
    },
    title_teaser: {
        de: "The High Heel Gourmet Café",
        en: "The High Heel Gourmet Café",
        fr: "The High Heel Gourmet Café",
        it: "The High Heel Gourmet Café"
    },
    text_teaser: {
        de: "Gourmetgerichte ohne Schnickschnack: Das verspricht das herzliche Lokal in Zürich Wiedikon.",
        en: "Gourmet dishes without frills: that is what the friendly restaurant in Zürich Wiedikon promises. ",
        fr: "Ce chaleureux local de Zurich Wiedikon est la promesse de plats pour gourmets sans chichi.",
        it: "Piatti gourmet senza fronzoli: è ciò che promette l’accogliente locale a Zürich Wiedikon."
    },
    osm_id: "338042836",
    image: {
        url: "https://cdn.zuerich.com/sites/default/files/web_zurich_restaurants_01.jpg",
        caption: {
            de: "Restaurants in Zürich",
            en: "Restaurants in Zurich",
            fr: "Restaurants à Zurich",
            it: "Ristoranti a Zurigo"
        }
    },
    photo: [ ],
    updated: "2019-06-11 17:44:24 +0200",
    detailedInformation: {
        de: [
            "Zero Waste Küche",
            "Kalifornische Küche",
            "Gesund, frisch, regional"
        ],
        en: [
            "Zero waste philosophy ",
            "Californian cuisine",
            "Healthy, fresh, regional"
        ],
        fr: [
            "Cuisine zéro déchet",
            "Cuisine californienne",
            "Sain, frais, régional"
        ],
        it: [
            "Cucina Zero Waste",
            "Cucina californiana",
            "Piatti sani, freschi e regionali"
        ]
    },
    address: {
        addressCountry: "CH",
        addressLocality: "Zürich",
        postalCode: "8003",
        streetAddress: "Zentralstrasse 72",
        phone: "+41 44 559 46 00",
        url: "www.highheelgourmetclub.com"
    },
    geo: {
        latitude: "47.373071000000",
        longitude: "8.518197209078"
    },
    openingHours: {
        de: "<p>Dienstag und Mittwoch, 09.00 – 14.30 Uhr<br />Donnerstag, 09.00 – 14.30 Uhr und 17.00 – 20.30 Uhr<br />Freitag, 09.00 – 14.30 Uhr und 17.00 – 22.30 Uhr</p>",
        en: "<p>Tuesday & Wednesday, 9am – 2.30pm<br />Thursday, 9am – 2.30pm & 5 – 8.30pm<br />Friday, 9am – 2.30pm & 5 – 10.30pm</p>",
        fr: "<p>Mardi et mercredi, 9h – 14h30<br />Jeudi, 9h – 14h30 et 17h – 20h30<br />Vendredi, 9h – 14h30 et 17h - 22h30 </p>",
        it: "<p>Martedì e mercoledì, 09.00 – 14.30<br />Giovedì, 09.00 – 14.30 e 17.00 – 20.30<br />Venerdì, 09.00 – 14.30 e 17.00 – 22.30</p>"
    },
    openingDays: "Tuesday,Wednesday,Thursday,Friday"
}]
```

The fields which do not support translation are just returning their value directly. The ones which can have a translation are objects having the language codes as properties.

The **@type** attribute of the object can have the following values:
- **LodgingBusiness** for accommodations.
- **Place** for places.
- **LocalBusiness** for restaurants / cafes.

The **@type** attribute matches actually the schema.org definitions for Places (https://schema.org/Place), Lodging Business (https://schema.org/LodgingBusiness) and Local Business (https://schema.org/LocalBusiness). There are, however, a few fields which are not schema.org standard. Here is the full list of non standard fields:
- All types:
  - copyright
  - cc
  - category: a list of categories this object is tagged with on the site.
  - title_teaser: a special title that is used when the object is displayed as a teaser (in lists of results for example).
  - text_teaser: same as the title_teaser, a special description to be used when displaying the object as a teaser.
  - osm_id: the open street map node id.
  - updated: the date and time the object was last updated on the site
- Place specific fields:
  - detailedInformation: a list with short text items containing some more highlights of the place.
  - zurichcard: a short text specifying what kind of reductions are available based on the Zurich Card (discount, free entry, zurich card partner)
  - zurichcardDescription: a text with some more details for the applicable reductions, using the Zurich Card, if any.
  - place: can have one or more from the following values: Indoors, Outdoors.
  - openingDays: a comma separated list of all the days when the place is open.
- LocalBusiness specific fields:
  - detailedInformation: a list with short text items containing some more highlights of the restaurant / cafe.
  - zurichcard: a short text specifying what kind of reductions are available based on the Zurich Card (discount, free entry, zurich card partner)
  - zurichcardDescription: a text with some more details for the applicable reductions, using the Zurich Card, if any.
  - openingDays: a comma separated list of all the days when the restaurant / cafe is open.

As mentioned above, each object exposes the **osm_id** field, for the integration with the open street maps service. The value stored in that field should be the OSM node id, so it can be used to access the node on the map, like *https://www.openstreetmap.org/node/xxxxxxx*.