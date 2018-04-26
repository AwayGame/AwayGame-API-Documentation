---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href="https://www.awaygame.co/">AwayGame</a>

includes:
  - errors

search: true
---

<!-- To run dev server, run 'bundle exec middleman server' -->

# Introduction

Welcome to the AwayGame Internal API documentation! This documentation can be used by any developer working
on the AwayGame mobile app.

# Authentication

<!-- 
  Uncomment when ready for Authentication

> To authorize, use this code:

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

-->

Coming soon...

<!--

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>
-->

# Search

## Search For Team

This endpoint searches the `teams` index in `Algolia` and returns
a list of matching teams based on the query string.

### HTTP Request

`GET https://us-central1-awaygame-api.cloudfunctions.net/api/search/teams/:qs`

### Response

```json
[{
    "name": "New England Patriots",
    "isSchool": false,
    "league": "NFL",
    "objectID": "456394311",
    "_highlightResult": {
        "name": {
            "value": "<em>New</em> <em>England</em> <em>Patriots</em>",
            "matchLevel": "full",
            "fullyHighlighted": true,
            "matchedWords": [
                "new",
                "england",
                "patriots"
            ]
        },
        "league": {
            "value": "NFL",
            "matchLevel": "none",
            "matchedWords": []
        }
    },
    {
        "conference": "SEC",
        "name": "Wildcats",
        "isSchool": "true",
        "school": "Kentucky",
        "league": "FBS",
        "objectID": "456398501",
        "_highlightResult": {
            "conference": {
                "value": "SEC",
                "matchLevel": "none",
                "matchedWords": []
            },
            "name": {
                "value": "<em>Wildcats</em>",
                "matchLevel": "partial",
                "fullyHighlighted": true,
                "matchedWords": [
                    "wildcats"
                ]
            },
            "isSchool": {
                "value": "true",
                "matchLevel": "none",
                "matchedWords": []
            },
            "school": {
                "value": "<em>Kentucky</em>",
                "matchLevel": "partial",
                "fullyHighlighted": true,
                "matchedWords": [
                    "kentucky"
                ]
            },
            "league": {
                "value": "FBS",
                "matchLevel": "none",
                "matchedWords": []
            }
        }
    }
}]
```

Key | Description
--------- | -----------
isSchool | If the team is collegiate level
school | Name of the school - only returned if `isSchool` is `true`
league | The league the team is in
conference | Conference the team is associated with
name | Name of the team
objectID | Firebase ObjectID
_highlightResult | Highlighted result to display from Algolia.

<aside>`_highlightResult` should be used to display the search results to the user</aside>


# Ticket Master

## Search For Games

Searches the TicketMaster API for games between the dates specified and involving the team
posted.

### HTTP Request

`POST https://us-central1-awaygame-api.cloudfunctions.net/api/searchForGames`

### Request Body

Parameter | Description
--------- | -----------
team | The name of the team
dmaId | The DMA ID associated with the city that the user has chosen. 
startDate | The beginning time to search for games
endDate | The end time to search for games

### Response

```json
[{
    "name": "Kentucky Wildcats Football at Louisville Cardinals Football",
    "id": "Z7r9jZ1Ae1bu_",
    "images": [
        {
            "ratio": "16_9",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_RECOMENDATION_16_9.jpg",
            "width": 100,
            "height": 56,
            "fallback": true
        },
        {
            "ratio": "16_9",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_TABLET_LANDSCAPE_16_9.jpg",
            "width": 1024,
            "height": 576,
            "fallback": true
        },
        {
            "ratio": "4_3",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_CUSTOM.jpg",
            "width": 305,
            "height": 225,
            "fallback": true
        },
        {
            "ratio": "16_9",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_RETINA_LANDSCAPE_16_9.jpg",
            "width": 1136,
            "height": 639,
            "fallback": true
        },
        {
            "ratio": "3_2",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_TABLET_LANDSCAPE_3_2.jpg",
            "width": 1024,
            "height": 683,
            "fallback": true
        },
        {
            "ratio": "16_9",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_TABLET_LANDSCAPE_LARGE_16_9.jpg",
            "width": 2048,
            "height": 1152,
            "fallback": true
        },
        {
            "ratio": "3_2",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_RETINA_PORTRAIT_3_2.jpg",
            "width": 640,
            "height": 427,
            "fallback": true
        },
        {
            "ratio": "3_2",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_ARTIST_PAGE_3_2.jpg",
            "width": 305,
            "height": 203,
            "fallback": true
        },
        {
            "ratio": "16_9",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_RETINA_PORTRAIT_16_9.jpg",
            "width": 640,
            "height": 360,
            "fallback": true
        },
        {
            "ratio": "16_9",
            "url": "https://s1.ticketm.net/dam/c/093/c74cfd95-af21-4e64-9f85-47677b951093_105651_EVENT_DETAIL_PAGE_16_9.jpg",
            "width": 205,
            "height": 115,
            "fallback": true
        }
    ],
    "date": {
        "start": {
            "localDate": "2018-11-24",
            "dateTBD": false,
            "dateTBA": false,
            "timeTBA": true,
            "noSpecificTime": false
        },
        "status": {
            "code": "onsale"
        },
        "spanMultipleDays": false
    },
    "stadium": {
        "name": "Papa John's Cardinal Stadium",
        "type": "venue",
        "id": "ZFr9jZeda6",
        "test": false,
        "locale": "en-us",
        "postalCode": "40209",
        "timezone": "America/New_York",
        "city": {
            "name": "Louisville"
        },
        "state": {
            "name": "Kentucky",
            "stateCode": "KY"
        },
        "country": {
            "name": "United States Of America",
            "countryCode": "US"
        },
        "address": {
            "line1": "2770 S. Floyd St."
        },
        "location": {
            "longitude": "-85.751801",
            "latitude": "38.192699"
        },
        "dmas": [
            {
                "id": 325
            }
        ],
        "upcomingEvents": {
            "_total": 8,
            "tmr": 7,
            "ticketmaster": 1
        },
        "_links": {
            "self": {
                "href": "/discovery/v2/venues/ZFr9jZeda6?locale=en-us"
            }
        }
    }
}]
```

Key | Description
--------- | -----------
name | The name of the event
id | The EventID from Ticket Master
images | Image urls of various sizes for the event
date | The date of the event
stadium | Where the event is located

# Itinerary

## Create Itinerary

Build the user's AwayGame, saves it to the database, and returns the data to the application

### HTTP Request

`POST https://us-central1-awaygame-api.cloudfunctions.net/api/createItinerary`

### Request Body

```json
"tbd"
```

Parameter | Description
--------- | -----------
category | The type of location to find
longitude | Longitude of the city
latitude | Latitude of the city

### Response

Response here