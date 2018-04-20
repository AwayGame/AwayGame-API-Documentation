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

# Cities

## Get All Cities

```json
[{
    "ticketMasterDmaId": "409",
    "imageUrl": "https://i1.wp.com/donate.ncjw.org/wp-content/uploads/2015/11/washington-dc-skyline-photo.jpg?fit=1200%2C675",
    "googlePlaceId": "ChIJW-T2Wt7Gt4kRKl2I1CJFUsI",
    "name": "Washington DC"
},{
    "name": "Philadelphia",
    "ticketMasterDmaId": "358",
    "imageUrl": "https://i.ytimg.com/vi/GnKJ-_DspMI/maxresdefault.jpg",
    "googlePlaceId": "ChIJ60u11Ni3xokRwVg-jNgU9Yk"
}]
```

This endpoint retrieves all cities in the database.

### HTTP Request

`GET https://us-central1-awaygame-api.cloudfunctions.net/api/cities`

### Response

Key | Description
--------- | -----------
ticketMasterDmaId | The ID used by the TicketMaster API to identify the city
imageUrl | A URL for an image of the city
googlePlaceId | The ID used by the Google Places API to identify the city
name | The name of the city


<!-- Teams Endpoints -->


# Teams

## Get a Specific Team Based On City

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

This endpoint retrieves all teams associated with the city with objectId `cityId`.

### HTTP Request

`GET https://us-central1-awaygame-api.cloudfunctions.net/api/getTeamsFromCity/:cityId`

### URL Parameters

Parameter | Description
--------- | -----------
cityId | The objectId of the City

### Response

Key | Description
--------- | -----------
sport | The sport the team is associated with
city | The city the team is from
name | The name of the team


# Events

## Get Events

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

This endpoint searches TicketMaster for events and games within the date ranges provided for a specific team.

### HTTP Request

`POST https://us-central1-awaygame-api.cloudfunctions.net/api/getEvents`

### Request Body

Parameter | Description
--------- | -----------
team | The name of the team
city | The name of the city
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


# Restaurants

## Get Restaurant Locations

This endpoint searches Yelp and Foursquare for restaurants and activites that match the given category.

### HTTP Request

`POST https://us-central1-awaygame-api.cloudfunctions.net/api/getLocationsOfRestaurants`

### Request Body

```json
{
  "category": "intimate",
  "longitude": -122.3321,
  "latitude": 47.6062
}
```

Parameter | Description
--------- | -----------
category | The type of location to find
longitude | Longitude of the city
latitude | Latitude of the city

### Response

Response here