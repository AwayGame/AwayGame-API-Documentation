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
objectID | Algolia ObjectID
_highlightResult | Highlighted result to display from Algolia.

<aside>`_highlightResult` should be used to display the search results to the user</aside>


# Ticket Master

## Search For Games

Searches the TicketMaster API for games between the dates specified and involving the team
posted.

### HTTP Request

`POST https://us-central1-awaygame-api.cloudfunctions.net/api/searchForGames`

### Request Body

```javascript
{
    team: "Chicago Cubs",
    startDate: "07-11-2018",
    endDate: "07-13-2018"
}
```

Parameter | Description
--------- | -----------
team | The name of the team
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
{
    "lat": 41.8781,
    "long": -87.6298,
    "radius": "5.0",
    "preferences": {
        "dayActivities": ["shopping"],
        "nightActivities": ["partybars", "nightclubs"],
        "food": ["fastFood", "localCusine"]
    },
    "arrivalTime": "2018-07-11T15:15:00.000Z",
    "departureTime": "2018-07-14T12:00:00.000Z"
}
```

Parameter | Description
--------- | -----------
lat | The latitude of the stadium - from TicketMaster result
long | The longitude of the stadium - from TicketMaster result
radius (optional) | The distance in miles that the user is willing to travel
preferences | The user's preferences that they entered during the walkthrough
arrivalTime | The time the user is getting to the city
departureTime | The time the user is leaving the city

### Response

*Each key in the object is a datestring*

Key | Description
--------- | -----------
activityName | The name of the activity (i.e 'breakfast', 'lunch', etc)
name | Name of the business
placeId | The Google Places ID for the business
phone | The formatted phone number of the business
location | Object containing latitude, longitude, and a URL that can be used to show the location on a map via Google
hours | Object containing the business' formal hours, formatted and raw
reviews | Array of user reviews
photos | Image IDS from Google. Use the Google API to show these photos directly
rating | The rating of the business, from 1 to 5


```json
{
    "2018-07-13T11:15:00-04:00": {
        "breakfast": {
            "name": "Mangis Fast Foods",
            "placeId": "ChIJv4QCiEHSD4gRpMHIKvOO1Gw",
            "phone": "(773) 477-0406",
            "address": "3801 N Lincoln Ave, Chicago, IL 60613, USA",
            "location": {
                "lat": 41.9506851,
                "long": -87.6760199,
                "mapsUrl": "https://maps.google.com/?cid=7842050026204873124"
            },
            "hours": {
                "formattedHours": [
                    "Monday: 7:00 AM – 8:00 PM",
                    "Tuesday: 7:00 AM – 8:00 PM",
                    "Wednesday: 7:00 AM – 8:00 PM",
                    "Thursday: 7:00 AM – 8:00 PM",
                    "Friday: 7:00 AM – 8:00 PM",
                    "Saturday: 7:00 AM – 8:00 PM",
                    "Sunday: 11:00 AM – 5:00 PM"
                ],
                "individualDaysData": [
                    {
                        "close": {
                            "day": 0,
                            "time": "1700"
                        },
                        "open": {
                            "day": 0,
                            "time": "1100"
                        }
                    },
                    {
                        "close": {
                            "day": 1,
                            "time": "2000"
                        },
                        "open": {
                            "day": 1,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 2,
                            "time": "2000"
                        },
                        "open": {
                            "day": 2,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 3,
                            "time": "2000"
                        },
                        "open": {
                            "day": 3,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 4,
                            "time": "2000"
                        },
                        "open": {
                            "day": 4,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 5,
                            "time": "2000"
                        },
                        "open": {
                            "day": 5,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 6,
                            "time": "2000"
                        },
                        "open": {
                            "day": 6,
                            "time": "0700"
                        }
                    }
                ]
            },
            "reviews": [
                {
                    "author_name": "Jason Scerena",
                    "author_url": "https://www.google.com/maps/contrib/111547736121046477242/reviews",
                    "language": "en",
                    "profile_photo_url": "https://lh4.googleusercontent.com/-tt6FzVOE73U/AAAAAAAAAAI/AAAAAAAAE_Q/ey0XeUULMkg/s128-c0x00000000-cc-rp-mo-ba4/photo.jpg",
                    "rating": 4,
                    "relative_time_description": "8 months ago",
                    "text": "Classic Chicago fast food place. Vienna Beef, gyros, burgers, ect. Old school feel and immaculately clean.",
                    "time": 1503952145
                }
            ],
            "photos": [
                "CmRaAAAAL3Edp39F-J-K50wvTnRiUk54QB0O3Ra6yGoRytrWfSUBCPFnGMh7V4cuGWcDsFAw5D8nIEXeu-NbS__XJHbHaxQmJ_-M7l8OerdMy3SRyg245gHt7QXeHkyVm0YiZ9y7EhAjxwTRFo8SYkm4IzxBLq0XGhSF7GcQ6VNhAITNEsuFXmmUm0jD6w"
            ],
            "rating": 4,
            "category": "food",
            "subcategory": "fastFood"
        },
        "morningActivity": {
            "name": "Gap",
            "placeId": "ChIJU7L9qD7TD4gROOAjfPSw050",
            "phone": "(312) 494-8580",
            "address": "555 N Michigan Ave, Chicago, IL 60611, USA",
            "location": {
                "lat": 41.8923786,
                "long": -87.6238844,
                "mapsUrl": "https://maps.google.com/?cid=11372628048141869112"
            },
            "website": "http://www.gap.com/products/chicago-il-store-569.jsp?tid=gpss000001",
            "hours": {
                "formattedHours": [
                    "Monday: 9:00 AM – 9:00 PM",
                    "Tuesday: 9:00 AM – 9:00 PM",
                    "Wednesday: 9:00 AM – 9:00 PM",
                    "Thursday: 9:00 AM – 9:00 PM",
                    "Friday: 9:00 AM – 9:00 PM",
                    "Saturday: 9:00 AM – 9:00 PM",
                    "Sunday: 9:00 AM – 9:00 PM"
                ],
                "individualDaysData": [
                    {
                        "close": {
                            "day": 0,
                            "time": "2100"
                        },
                        "open": {
                            "day": 0,
                            "time": "0900"
                        }
                    },
                    {
                        "close": {
                            "day": 1,
                            "time": "2100"
                        },
                        "open": {
                            "day": 1,
                            "time": "0900"
                        }
                    },
                    {
                        "close": {
                            "day": 2,
                            "time": "2100"
                        },
                        "open": {
                            "day": 2,
                            "time": "0900"
                        }
                    },
                    {
                        "close": {
                            "day": 3,
                            "time": "2100"
                        },
                        "open": {
                            "day": 3,
                            "time": "0900"
                        }
                    },
                    {
                        "close": {
                            "day": 4,
                            "time": "2100"
                        },
                        "open": {
                            "day": 4,
                            "time": "0900"
                        }
                    },
                    {
                        "close": {
                            "day": 5,
                            "time": "2100"
                        },
                        "open": {
                            "day": 5,
                            "time": "0900"
                        }
                    },
                    {
                        "close": {
                            "day": 6,
                            "time": "2100"
                        },
                        "open": {
                            "day": 6,
                            "time": "0900"
                        }
                    }
                ]
            },
            "reviews": [
                {
                    "author_name": "Bill Stolte",
                    "author_url": "https://www.google.com/maps/contrib/108657571729523357657/reviews",
                    "language": "en",
                    "profile_photo_url": "https://lh4.googleusercontent.com/-dWsH6G5hUMA/AAAAAAAAAAI/AAAAAAAAJgM/QNXfs5rL_CA/s128-c0x00000000-cc-rp-mo-ba4/photo.jpg",
                    "rating": 5,
                    "relative_time_description": "3 months ago",
                    "text": "Huge sale day so I have to give it 5 stars.  Everything I needed and wanted was deeply discounted... When does that happen????",
                    "time": 1517506910
                }
            ],
            "photos": [
                "CmRaAAAAVUuSpjR3f16CBVdU-q0NG5wsJykP6hWVN0kGe2PXYhqe0UOJfsuDHy0bwkVyop9KqNever0v82m4TkRG3llc8yMV5Q-q2AQ6B7VdNsHHIauO29Lk9bJBG0bqdiTwTez_EhDZunwVng2f7wmrtdzRTiU5GhTXP2_NA0-rFRr9j1AUXQe4FYoM6Q"
            ],
            "price": 2,
            "rating": 4.3,
            "category": "day",
            "subcategory": "shopping"
        },
        "lunch": {
            "name": "Cohiba Cuban Cuisine",
            "placeId": "ChIJRwnqlQnTD4gRki9WmEChue8",
            "phone": "(773) 935-8866",
            "address": "2835 N Broadway St, Chicago, IL 60657, USA",
            "location": {
                "lat": 41.9338209,
                "long": -87.6443982,
                "mapsUrl": "https://maps.google.com/?cid=17274015144562012050"
            },
            "website": "https://themenustar1.com/webspace/menus.php?code=cohibarestaurant.mobile-webview1.com",
            "hours": {
                "formattedHours": [
                    "Monday: 11:00 AM – 10:00 PM",
                    "Tuesday: 11:00 AM – 10:00 PM",
                    "Wednesday: 11:00 AM – 10:00 PM",
                    "Thursday: 11:00 AM – 10:00 PM",
                    "Friday: 11:00 AM – 10:00 PM",
                    "Saturday: 11:00 AM – 10:00 PM",
                    "Sunday: 11:00 AM – 10:00 PM"
                ],
                "individualDaysData": [
                    {
                        "close": {
                            "day": 0,
                            "time": "2200"
                        },
                        "open": {
                            "day": 0,
                            "time": "1100"
                        }
                    },
                    {
                        "close": {
                            "day": 1,
                            "time": "2200"
                        },
                        "open": {
                            "day": 1,
                            "time": "1100"
                        }
                    },
                    {
                        "close": {
                            "day": 2,
                            "time": "2200"
                        },
                        "open": {
                            "day": 2,
                            "time": "1100"
                        }
                    },
                    {
                        "close": {
                            "day": 3,
                            "time": "2200"
                        },
                        "open": {
                            "day": 3,
                            "time": "1100"
                        }
                    },
                    {
                        "close": {
                            "day": 4,
                            "time": "2200"
                        },
                        "open": {
                            "day": 4,
                            "time": "1100"
                        }
                    },
                    {
                        "close": {
                            "day": 5,
                            "time": "2200"
                        },
                        "open": {
                            "day": 5,
                            "time": "1100"
                        }
                    },
                    {
                        "close": {
                            "day": 6,
                            "time": "2200"
                        },
                        "open": {
                            "day": 6,
                            "time": "1100"
                        }
                    }
                ]
            },
            "reviews": [
                {
                    "author_name": "Dallas Stobb",
                    "author_url": "https://www.google.com/maps/contrib/116769898312993628934/reviews",
                    "language": "en",
                    "profile_photo_url": "https://lh3.googleusercontent.com/-Ofn2q0gp68U/AAAAAAAAAAI/AAAAAAAAADA/SUm0YNeBnsQ/s128-c0x00000000-cc-rp-mo-ba3/photo.jpg",
                    "rating": 3,
                    "relative_time_description": "a week ago",
                    "text": "My server was very nice, but the Cuban sandwich lacked flavor. I ordered fried yuca and I had to ask for garlic sauce. not really a big deal, but that's the BEST part! if people don't get that they are really missing out!",
                    "time": 1524578445
                }
            ],
            "photos": [
                "CmRaAAAATzCnZK0fOpFnKuxuRU9xr50eHXOudnmluSS6THPUwMGzWVs69rZHMzfwwWuJm_0vcjbG9_DwrN3fSEs4zdTQKXsBouHltc3I3aYkdCIK92y7EkJCCgIn7ISXfcEYQVUZEhBoCR6EibaLCIcb7lRcoMSfGhSy0MrKcbO7pIW5cSQY2j7oxJADoA"
            ],
            "price": 1,
            "rating": 4.4,
            "category": "food",
            "subcategory": "localCusine"
        },
        "afternoonActivity": {
            "name": "Southgate Market",
            "placeId": "ChIJxQqi1uwsDogRGVPqkwQo7F0",
            "phone": "(312) 944-3777",
            "address": "1101 S Canal St, Chicago, IL 60607, USA",
            "location": {
                "lat": 41.868634,
                "long": -87.6386375,
                "mapsUrl": "https://maps.google.com/?cid=6767828340157600537"
            },
            "website": "http://www.mccafferyinterests.com/portfolio/southgate-market",
            "hours": {
                "formattedHours": [
                    "Monday: 7:00 AM – 10:00 PM",
                    "Tuesday: 7:00 AM – 10:00 PM",
                    "Wednesday: 7:00 AM – 10:00 PM",
                    "Thursday: 7:00 AM – 10:00 PM",
                    "Friday: 7:00 AM – 10:00 PM",
                    "Saturday: 7:00 AM – 10:00 PM",
                    "Sunday: 7:00 AM – 10:00 PM"
                ],
                "individualDaysData": [
                    {
                        "close": {
                            "day": 0,
                            "time": "2200"
                        },
                        "open": {
                            "day": 0,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 1,
                            "time": "2200"
                        },
                        "open": {
                            "day": 1,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 2,
                            "time": "2200"
                        },
                        "open": {
                            "day": 2,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 3,
                            "time": "2200"
                        },
                        "open": {
                            "day": 3,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 4,
                            "time": "2200"
                        },
                        "open": {
                            "day": 4,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 5,
                            "time": "2200"
                        },
                        "open": {
                            "day": 5,
                            "time": "0700"
                        }
                    },
                    {
                        "close": {
                            "day": 6,
                            "time": "2200"
                        },
                        "open": {
                            "day": 6,
                            "time": "0700"
                        }
                    }
                ]
            },
            "reviews": [
                {
                    "author_name": "Henok Tesfay",
                    "author_url": "https://www.google.com/maps/contrib/115907576235907344836/reviews",
                    "language": "en",
                    "profile_photo_url": "https://lh5.googleusercontent.com/-ZZieao_ih30/AAAAAAAAAAI/AAAAAAAAd30/aGKzuLDOgGE/s128-c0x00000000-cc-rp-mo/photo.jpg",
                    "rating": 5,
                    "relative_time_description": "a month ago",
                    "text": "OK! My first time in a Whole Foods grocery store. My mind was blown I literally stayed in there for 2 hours I couldn't control myself. I tried every sample possible. Search for any and every food. Ended up leaving with only lemonade. Great place with amazing employees especially a lady that worked in the food area she was very helpful. The food is fresh and amazing. I live in Indiana and never been to a whole foods even though theres some here. Would def recommend to anyone and everyone on Earth.",
                    "time": 1521654947
                }
            ],
            "photos": [
                "CmRaAAAAahNTHsSkbokRPe9e2CYjlneysl9elRT7F1YB3-_9TgySpyYMq7QIWQ-LXZ-difxZUf9tiur9fcgChj74RxukMn85gV4lK7aPu9E2CJufTE53rD23PMDbihvDtFY5oJ7KEhC0rtJnBR6WNL5L433AlSquGhTNGt7wVNbvpE90AMggsZ_HD8wVfQ"
            ],
            "rating": 4.2,
            "category": "day",
            "subcategory": "shopping"
        },
        "dinner": {
            "name": "Ramirez Fast Food",
            "placeId": "ChIJlXhtdi4tDogRbMuu-kpynx0",
            "phone": "(312) 666-8331",
            "address": "1521 W Grand Ave, Chicago, IL 60642, USA",
            "location": {
                "lat": 41.89085790000001,
                "long": -87.6664234,
                "mapsUrl": "https://maps.google.com/?cid=2134550414755810156"
            },
            "hours": {
                "formattedHours": [
                    "Monday: 5:00 AM – 4:00 PM",
                    "Tuesday: 5:00 AM – 4:00 PM",
                    "Wednesday: 5:00 AM – 4:00 PM",
                    "Thursday: 5:00 AM – 4:00 PM",
                    "Friday: 5:00 AM – 4:00 PM",
                    "Saturday: 5:00 AM – 2:00 PM",
                    "Sunday: Closed"
                ],
                "individualDaysData": [
                    {
                        "close": {
                            "day": 1,
                            "time": "1600"
                        },
                        "open": {
                            "day": 1,
                            "time": "0500"
                        }
                    },
                    {
                        "close": {
                            "day": 2,
                            "time": "1600"
                        },
                        "open": {
                            "day": 2,
                            "time": "0500"
                        }
                    },
                    {
                        "close": {
                            "day": 3,
                            "time": "1600"
                        },
                        "open": {
                            "day": 3,
                            "time": "0500"
                        }
                    },
                    {
                        "close": {
                            "day": 4,
                            "time": "1600"
                        },
                        "open": {
                            "day": 4,
                            "time": "0500"
                        }
                    },
                    {
                        "close": {
                            "day": 5,
                            "time": "1600"
                        },
                        "open": {
                            "day": 5,
                            "time": "0500"
                        }
                    },
                    {
                        "close": {
                            "day": 6,
                            "time": "1400"
                        },
                        "open": {
                            "day": 6,
                            "time": "0500"
                        }
                    }
                ]
            },
            "reviews": [
                {
                    "author_name": "Tina Marie",
                    "author_url": "https://www.google.com/maps/contrib/118445200191023633755/reviews",
                    "language": "en",
                    "profile_photo_url": "https://lh4.googleusercontent.com/-JAABTVqe4nI/AAAAAAAAAAI/AAAAAAAAAAA/AIcfdXAsxmIAVWEn7Q6KKxdEPDUWe1DqKw/s128-c0x00000000-cc-rp-mo-ba3/photo.jpg",
                    "rating": 4,
                    "relative_time_description": "a week ago",
                    "text": "...Because they serve a lot of different foods. Polish, hot dogs, Burgers, Italian beef,tacos, burritos, beans, rice, eggs,chips,luv their fries. Coffee/sodas. From breakfast - brunch - dinner.\n👌Everything i like to eat in one place💞",
                    "time": 1524946432
                }
            ],
            "photos": [
                "CmRaAAAAVUDwgr0xCMYjO_AyIZN7PMk6G-kmge2WzqGxFdjPUlwqfHb6t6QuwiDQFezObRPgQL31h8jrxPQlV1H5C4WcP9VrXtWeF992ZxlCLfqrs9QJFJQSmSfvBW72pP-an-qMEhBlWqv6dSeaulEGfk7VOm_lGhQsbiSwGN7DG1Z9DPB5Dr8Jx9C1mw"
            ],
            "rating": 3.7,
            "category": "food",
            "subcategory": "fastFood"
        },
        "eveningActivity": {
            "name": "La Cueva Night Club",
            "placeId": "ChIJgdaDIk8yDogRKbZz_Ha_5ls",
            "phone": "(773) 475-6544",
            "address": "4153 W 26th St, Chicago, IL 60623, USA",
            "location": {
                "lat": 41.84396199999999,
                "long": -87.7291023,
                "mapsUrl": "https://maps.google.com/?cid=6622190819857380905"
            },
            "hours": {
                "formattedHours": [
                    "Monday: Closed",
                    "Tuesday: Closed",
                    "Wednesday: Closed",
                    "Thursday: 8:00 PM – 4:00 AM",
                    "Friday: 8:00 PM – 4:00 AM",
                    "Saturday: 8:00 PM – 5:00 AM",
                    "Sunday: 8:00 PM – 4:00 AM"
                ],
                "individualDaysData": [
                    {
                        "close": {
                            "day": 1,
                            "time": "0400"
                        },
                        "open": {
                            "day": 0,
                            "time": "2000"
                        }
                    },
                    {
                        "close": {
                            "day": 5,
                            "time": "0400"
                        },
                        "open": {
                            "day": 4,
                            "time": "2000"
                        }
                    },
                    {
                        "close": {
                            "day": 6,
                            "time": "0400"
                        },
                        "open": {
                            "day": 5,
                            "time": "2000"
                        }
                    },
                    {
                        "close": {
                            "day": 0,
                            "time": "0500"
                        },
                        "open": {
                            "day": 6,
                            "time": "2000"
                        }
                    }
                ]
            },
            "reviews": [
                {
                    "author_name": "Jasmine Garcia",
                    "author_url": "https://www.google.com/maps/contrib/112433908557699725155/reviews",
                    "language": "en",
                    "profile_photo_url": "https://lh3.googleusercontent.com/-nEKcb-44kpg/AAAAAAAAAAI/AAAAAAAAMyw/0sA30HGpzHo/s128-c0x00000000-cc-rp-mo/photo.jpg",
                    "rating": 3,
                    "relative_time_description": "5 months ago",
                    "text": "The show was good but the waitress where stealing money from the clients. You will pay them for the beer and they would keep the change thinking u didn't wanted it so they where keeping the change as their tip.",
                    "time": 1511716189
                }
            ],
            "photos": [
                "CmRaAAAA92Gjw7bmACLgFBR4n5RYTcjY8pBJ9LISSO01VjGL_UL4fvs4F3fUfDLDg1FDt0YJXqUh8Wkw1bx2TejazZj1xNbHo-A1ubOKtHlnCmOabrcADjj1bRV3T3i52WyriwjEEhDM60wafF0cv0B-QI6lhqyiGhQDAXWY6sJGocJq9e7mLG1aDC7LQw"
            ],
            "rating": 4.6,
            "category": "night",
            "subcategory": "nightclubs"
        }
    }
}
```