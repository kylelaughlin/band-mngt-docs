---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Band Management API! This API helps make song and set list management tasks for a band easy and enjoyable. Example code can be viewed in the dark area to the right and provides example requests utilizing cURL.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:



```shell
curl http://localhost:3000/api/v1/authenticate \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{"email":"your_email@email.com", "password":"your_password"}'
```


> Make sure to replace `your_email@email.com` and `your_password` with your API key.


```shell
  #The above successful authentication request would return your session authentication token as follows:

  {"auth_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE0ODE1OTgzNzd9.SIxAbFk64GJU-a92SSB9F7aob0ekCpuJ3YbLw595-HA"}
```

This API utilizes an authentication token provided when a users credentials, email and password, are verified. The code to the right demonstrates the request made to retrieve your session authentication token. All requests made durring this session must have the following header:

`Authorization: your_authentication_token`


# Songs

## Get All Songs


```shell
curl "http://localhost:3000/api/v1/songs"
  -H "Authorization: your_session_token"
```

> The above command returns JSON structured like this:

```json
{
  "active_songs": [
    {
      "id": 3,
      "title": "3 am",
      "artist": "Matchbox 20",
      "active": true,
      "band_id": 1,
      "created_at": "2016-11-24T03:14:51.692Z",
      "updated_at": "2016-11-24T03:14:51.692Z"
    },
    {
      "id": 4,
      "title": "Black Magic Woman",
      "artist": "Santana",
      "active": true,
      "band_id": 1,
      "created_at": "2016-11-24T03:14:51.692Z",
      "updated_at": "2016-11-24T03:14:51.692Z"
    }
  ],
  "inactive_songs": [
    {
      "id": 1,
      "title": "Play That Funky Music",
      "artist": "Wild Chery",
      "active": false,
      "band_id": 1,
      "created_at": "2016-11-24T03:14:51.665Z",
      "updated_at": "2016-11-24T03:17:41.837Z"
    }
  ]
}
```

This endpoint retrieves all songs for the current user's band.

### HTTP Request

`GET http://localhost/api/v1/songs`

The JSON response show to the right returns two lists of songs. A list of the band's active songs and a list of inactive_songs.

## Get a Specific Song

```shell
curl "http://localhost:3000/api/v1/songs/2"
  -H "Authorization: meowmeowmeow"
```
