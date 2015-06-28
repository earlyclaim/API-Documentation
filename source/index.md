---
title: Earlyclaim API

language_tabs:
  - shell
  - html
  - javascript
  - php

toc_footers:
  - <a href='http://earlyclaim.com'>Sign Up to submit your startup</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Earlyclaim API documentation! You can use our API to access Earlyclaim API endpoints, which a startup can comunicate with Earlyclaim database.

We have language bindings in Shell, Node.js (comming soon), PHP (comming soon), iOS (working on)! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Buttons

> To integrate the EarlyClaim buttons use this code in your frontend HTML

```html
<div id="ec-button" data-callback="your callback endpoint after authorization"></div> <!-- Put this html in the place of the button -->
<script>(function(d, s, id) {
  var js, ecjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) return;
  js = d.createElement(s); js.id = id;
  js.src = "//cdn.earlyclaim.com/sdk.js#bId=earlyclaimBusinessId";
  ecjs.parentNode.insertBefore(js, ecjs);
}(document, 'script', 'earlyclaim-jssdk'));</script>
```

```shell
# No shell provided
```

```javascript
# No node.js provided
```

```php
# No PHP provided
```
> Make sure to replace `earlyclaimBusinessId` with your API key.

Earlyclaim Buttons are pretty simple to integrate in your frontend. You can register to Earlyclaim as a startup and get your Earlyclaim Business ID

[Learn more](http://earlyclaim.com/learn-more/startup)

<aside class="notice">
You must replace <code>earlyclaimBusinessId</code> with your personal API key.
</aside>

# Authentication

> To authorize, use this code:

```html
# No HTML provided
```
```javascript
# No node.js provided
```

```php
# No PHP provided
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Bearer earlyclaimBusinessToken"
```

> Make sure to replace `earlyclaimBusinessToken` with your Business API Token.

Earlyclaim uses API Bearer Authorization  Tokens to allow access to the API.

Earlyclaim expects for the API Token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer earlyclaimBusinessToken`

<aside class="notice">
You must replace <code>earlyclaimBusinessToken</code> with your personal API key.
</aside>

# Reservations

## Get All the reservations

```html
# No HTML provided
```
```javascript
# No node.js provided
```

```php
# No PHP provided
```

```shell
curl "http://api.earlyclaim.com/reservations"
  -H "Authorization: Bearer earlyclaimBusinessToken"
```

> The above command returns JSON structured like this:

```json
{
  "info": {
    "businessID": "yourBusinessID",
    "action": "reservations",
    "total": "<total number of reservations>",
    "results": "<current number of reservations>"
  },
  "query": {
    "limit": 30,
    "self": "http://api.earlyclaim.com/reservations/?skip=0",
    "prev": "http://api.earlyclaim.com/reservations/?skip=0",
    "next": "http://api.earlyclaim.com/reservations/?skip=30"
  },
  "data": [
    {
      "subscriptionID":"subscriptionID",
      "status":"status of reservation",
      "username":"user username",
      "screenName":"user screenName",
      "profilePicture":"url of the profile picture",
      "email":"earlyclaim user email",
      "trust":"user trust level"
    }
  ],
  "createdAt": "GMT time of the launch freeze reservations"  
}
```

This endpoint retrieves all the reservations paginated. You can ask for the next page of result following the next query link.

### HTTP Request

`GET http://api.earlyclaim.com/reservations`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
skip | 0 | skip N of user reservaitons.

<aside class="success">
Remember — a happy startup  is an authenticated startup!
</aside>
<aside class="notice">
Pay attention the given email isn't the real one.
You have to ask the email during the on-boarding process on your Website/application.
</aside>
## Get a Specific Reservation

```html
# No HTML provided
```
```javascript
# No node.js provided
```

```php
# No PHP provided
```

```shell
curl "http://api.earlyclaim.com/reservations/:ReservationID"
  -H "Authorization: Bearer earlyclaimBusinessToken"
```

> The above command returns JSON structured like this:

```json
{
      "subscriptionID":"subscriptionID",
      "status":"status of reservation",
      "username":"user username",
      "screenName":"user screenName",
      "profilePicture":"url of the profile picture",
      "email":"earlyclaim user email",
      "trust":"user trust level"
}
```

This endpoint retrieves a specific reservation.


### HTTP Request

`GET http://api.earlyclaim.com/reservations/:ReservationID`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the subscription to retrieve

## Accept a Specific Reservation

```html
# No HTML provided
```
```javascript
# No node.js provided
```

```php
# No PHP provided
```

```shell
curl -X POST "http://api.earlyclaim.com/reservations/:ReservationID/accept"
  -H "Authorization: Bearer earlyclaimBusinessToken"
```

> The above command returns JSON structured like this:

```json
{
      "subscriptionID":"subscriptionID",
      "status":"subscribed",
      "username":"user username"
}
```

This endpoint accept a specific reservation.


### HTTP Request

`POST http://api.earlyclaim.com/reservations/:ReservationID/accept`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the subscription to accept

<aside class="notice">
You must accept a subscription if you don't the reservation will not be notified.
</aside>

## Deny a Specific Reservation

```html
# No HTML provided
```
```javascript
# No node.js provided
```

```php
# No PHP provided
```

```shell
curl -X POST "http://api.earlyclaim.com/reservations/:ReservationID/deny"
  -H "Authorization: Bearer earlyclaimBusinessToken"
```

> The above command returns JSON structured like this:

```json
{
      "subscriptionID":"subscriptionID",
      "status":"denied",
      "username":"user username"
}
```

This endpoint deny a specific reservation.


### HTTP Request

`POST http://api.earlyclaim.com/reservations/:ReservationID/deny`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the subscription to deny

<aside class="notice">
If the subscription will deny the user will be notified.
</aside>

## Ask for a backup username for a Specific Reservation

```html
# No HTML provided
```
```javascript
# No node.js provided
```

```php
# No PHP provided
```

```shell
curl "http://api.earlyclaim.com/reservations/:ReservationID/backup"
  -H "Authorization: Bearer earlyclaimBusinessToken"
```

> The above command returns JSON structured like this:

```json
{
      "subscriptionID":"subscriptionID",
      "username":"a backup username"
}
```

This endpoint retrieves a specific reservation backup username.



### HTTP Request

`POST http://api.earlyclaim.com/reservations/:ReservationID/backup`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the subscription backup username  to retrieve

<aside class="notice">
You must accept a subscription, if you don't the reservation will not be notified.
</aside>
<aside class="notice">
Earlyclaim trace the backup username reservation and will only send 1 time, please don't abuse.
</aside>

# Bunch of Reservation

Earlyclaim after the "Private Beta Launch" will send to you a queue of reservations.
In the Startup dashboard you have to setup the web-hook url where the Earlyclaim rooster can send the informations about your user reservation.

##Setting Up your Callback URL
  
First you'll need to prepare the page that will act as your callback URL. This URL will need to be accessible by Earlyclaim servers, and be able to receive both the POST data that is sent when an update happens, but also accept GET requests in order to verify subscriptions.
  
This URL should always return a 200 OK HTTP response when invoked by Earlyclaim.
  
##Receiving the Bunch

> The rooster will send you this informations

```json
{
    "info":{
        "businessID": "yourBusinessID",
        "action": "reservation",
        "total": "<total number of reservations>",
        "current": "<current number of reservation>"
    },
    "data":{
          "subscriptionID":"subscriptionID",
          "status":"status of reservation",
          "username":"user username",
          "screenName":"user screenName",
          "profilePicture":"url of the profile picture",
          "email":"earlyclaim user email",
          "trust":"user trust level"
    },
    "createdAt": "GMT time of the launch freeze reservations"
}
```

Earlyclaim will make an HTTP POST request to your callback URL every time that there are changes (to the chosen fields or edges).
    
The request will have content type of application/json and the body will contain the following fields:

The HTTP request will contain an X-Hub-Signature header which contains the SHA1 signature of the request payload, using the earlyclaimBusinessToken as the key, and prefixed with sha1=. Your callback endpoint can verify this signature to validate the integrity and origin of the payload.

Changes are aggregated and sent in batch at most once every 5 seconds, or when the number of unsent changes exceeds 1000 - your server callback should be able to handle this level of load.

<aside class="notice">
You must accept/deny a subscription, if you don't the reservation will not be notified and the queue will be blocked and you will not able to receive all the other subscriptions
</aside>
<aside class="notice">
You can ask for the backup username ass well
</aside>
  

