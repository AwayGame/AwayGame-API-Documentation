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

# Cities and Teams

## Get All Cities

This endpoint retrieves all cities and their associated teams in the database. Ideally this
endpoint should be called as the application loads, as this data is needed to make
a user's AwayGame.

### HTTP Request

`GET https://us-central1-awaygame-api.cloudfunctions.net/api/cities`

### Response

```json
[{
    "ticketMasterDmaId": "409",
    "imageUrl": "https://i1.wp.com/donate.ncjw.org/wp-content/uploads/2015/11/washington-dc-skyline-photo.jpg?fit=1200%2C675",
    "googlePlaceId": "ChIJW-T2Wt7Gt4kRKl2I1CJFUsI",
    "name": "Chicago",
    "teams": [{
        "name": "Bulls",
        "sport": "Basketball",
        "stadiumUrl": "https://i.ytimg.com/vi/GnKJ-_DspMI/maxresdefault.jpg",
        "logoUrl": "https://i.ytimg.com/vi/GnKJ-_DspMI/maxresdefault.jpg"
      }]
}]
```

Key | Description
--------- | -----------
ticketMasterDmaId | The ID used by the TicketMaster API to identify the city
imageUrl | A URL for an image of the city
googlePlaceId | The ID used by the Google Places API to identify the city
name | The name of the city
teams | List of teams associated with this city

# Ticket Master

## Get Available Games

```json
[{
    "sport": "Hockey",
    "city": "Dallas",
    "name": "Stars"
},
{
    "sport": "Basketball",
    "city": "Dallas",
    "name": "Mavericks"
}]
```

Searches the TicketMaster API for games between the dates specified and involving the team
posted.

### HTTP Request

`POST https://us-central1-awaygame-api.cloudfunctions.net/api/getAvailableGames`

### Request Body

Parameter | Description
--------- | -----------
team | The name of the team
dmaId | The DMA ID associated with the city that the user has chosen. 
startDate | The beginning time to search for games
endDate | The end time to search for games

### Response

Key | Description
--------- | -----------
sport | The sport the team is associated with
city | The city the team is from
name | The name of the team

```json
[{
    "sport": "Hockey",
    "city": "Dallas",
    "name": "Stars"
},
{
    "sport": "Basketball",
    "city": "Dallas",
    "name": "Mavericks"
}]
```


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