---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL
  # - ruby
  # - python
  # - javascript

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Planif API
---

# Introduction

Welcome to the Planif API!

Base url : `https://dev.planif.fr/`

<!-- You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database. -->

<!-- We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right. -->

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

<!-- # Authentication 

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
-->

# Authentification

## How it works

> An authoriation header should be like that

```
Authorization: Bearer <your_token>
```

```shell
curl -v \
	-H "Authorization: Bearer <your_token>"
```

To access all ressources that need authentification, you need to pass an authorization header.

This header is composed of a token associated with each user. You first need to retrieve the token. To do so, you must send a POST request to the login endpoint

## Login endpoint

```shell
curl -v \
	-X POST \
	-d "password=password&username=username" \
	"https://dev.planif.fr/api-shared/api-token-auth/"
```

> The above command returns JSON structured like this:

```json
{
"token": "23d8f0bed20b838474b782454f68ba4f1195b476"
}
```

Use this endpoint to retrieve the authorization token by sending the credentials as POST parameters

`POST api-shared/api-token-auth/`

Property | Description
--------- | -----------
username | required (string)
password | required (string)

<!-- 
# Sessions

## Built session

Here is an example of a built session object with Planif session builder. This example contains 3 differents variants of the session.

Property | Description
--------- | -----------
_id | The ID of the session (ObjectId)
sport | instance of sport of the session (string)
title | title of the session (string)
description | description of the session (string)
tags | list of tags choose by the creator (Array of string)
steps | list of steps of the session, null if variants (Array of steps)
variants | list of variants of the session, empty if only one variant (Array of variants)

> JSON structured like this:

```json
{
  "_id":{
    "$oid":"6225e150d19fffa18fa4139f"
  },
  "sport":"RUNNING",
  "title":"30/30",
  "description":"Session 30/30 for beginners, intermediates, experts",
  "steps":null,
  "variants":[
    {
      "name":"Beginner",
      "steps":[
        {
          "intensity":"WARMUP",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"1200"
          }
        },
        {
          "repeatType":"REPEAT_UNTIL_STEPS_CMPLT",
          "repeatValue":{
            "$numberInt":"2"
          },
          "steps":[
            {
              "repeatType":"REPEAT_UNTIL_STEPS_CMPLT",
              "repeatValue":{
                "$numberInt":"6"
              },
              "steps":[
                {
                  "intensity":"INTERVAL",
                  "targetType":"SPEED_LAP",
                  "durationType":"TIME",
                  "durationValue":{
                    "$numberInt":"30"
                  },
                  "targetValue":"5"
                },
                {
                  "intensity":"RECOVERY",
                  "targetType":"OPEN",
                  "durationType":"TIME",
                  "durationValue":{
                    "$numberInt":"30"
                  }
                }
              ]
            },
            {
              "intensity":"COOLDOWN",
              "targetType":"OPEN",
              "durationType":"TIME",
              "durationValue":{
                "$numberInt":"240"
              }
            }
          ]
        },
        {
          "intensity":"COOLDOWN",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"360"
          }
        }
      ]
    },
    {
      "name":"Intermediate",
      "steps":[
        {
          "intensity":"WARMUP",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"1200"
          }
        },
        {
          "repeatType":"REPEAT_UNTIL_STEPS_CMPLT",
          "repeatValue":{
            "$numberInt":"2"
          },
          "steps":[
            {
              "repeatType":"REPEAT_UNTIL_STEPS_CMPLT",
              "repeatValue":{
                "$numberInt":"8"
              },
              "steps":[
                {
                  "intensity":"INTERVAL",
                  "targetType":"SPEED_LAP",
                  "durationType":"TIME",
                  "durationValue":{
                    "$numberInt":"30"
                  },
                  "targetValue":"5"
                },
                {
                  "intensity":"RECOVERY",
                  "targetType":"OPEN",
                  "durationType":"TIME",
                  "durationValue":{
                    "$numberInt":"30"
                  }
                }
              ]
            },
            {
              "intensity":"COOLDOWN",
              "targetType":"OPEN",
              "durationType":"TIME",
              "durationValue":{
                "$numberInt":"240"
              }
            }
          ]
        },
        {
          "intensity":"COOLDOWN",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"360"
          }
        }
      ]
    },
    {
      "name":"Expert",
      "steps":[
        {
          "intensity":"WARMUP",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"1800"
          }
        },
        {
          "repeatType":"REPEAT_UNTIL_STEPS_CMPLT",
          "repeatValue":{
            "$numberInt":"2"
          },
          "steps":[
            {
              "repeatType":"REPEAT_UNTIL_STEPS_CMPLT",
              "repeatValue":{
                "$numberInt":"8"
              },
              "steps":[
                {
                  "intensity":"INTERVAL",
                  "targetType":"SPEED_LAP",
                  "durationType":"TIME",
                  "durationValue":{
                    "$numberInt":"30"
                  },
                  "targetValue":"5"
                },
                {
                  "intensity":"RECOVERY",
                  "targetType":"OPEN",
                  "durationType":"TIME",
                  "durationValue":{
                    "$numberInt":"30"
                  }
                }
              ]
            },
            {
              "intensity":"COOLDOWN",
              "targetType":"OPEN",
              "durationType":"TIME",
              "durationValue":{
                "$numberInt":"240"
              }
            }
          ]
        },
        {
          "intensity":"COOLDOWN",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"360"
          }
        }
      ]
    }
  ],
  "coach_id":{
    "$numberInt":"4"
  }
}
```

> Simple example with tags

```json
{
  "_id":{
    "$oid":"62261a8b4f3f8e0b136791c7"
  },
  "sport":"LAP_SWIMMING",
  "title":"Swim open water example",
  "description":"Example with tags",
  "tags":[
    "easy swim",
    "beginner",
    "intermediate",
    "open water"
  ],
  "steps":[
    {
      "intensity":"INTERVAL",
      "targetType":"OPEN",
      "durationType":"DISTANCE",
      "durationValue":{
        "$numberInt":"5"
      },
      "durationValueType":"KM"
    }
  ],
  "variants":[
    
  ],
  "coach_id":{
    "$numberInt":"4"
  }
}
```
> Example ramp

```json
{
  "_id":{
    "$oid":"6228c63e06b096526738dae8"
  },
  "sport":"CYCLING",
  "title":"Cycling ramp",
  "description":null,
  "tags":[
    "cycling"
  ],
  "steps":[
    {
      "intensity":"WARMUP",
      "targetType":"OPEN",
      "durationType":"TIME",
      "durationValue":{
        "$numberInt":"1200"
      }
    },
    {
      "repeatValue":{
        "$numberInt":"4"
      },
      "uuid-Comment":"a0612b3ef9024151b3947a5e6ac5da7b",
      "steps":[
        {
          "intensity":"INTERVAL",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"60"
          }
        },
        {
          "intensity":"INTERVAL",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"60"
          }
        },
        {
          "intensity":"INTERVAL",
          "targetType":"OPEN",
          "durationType":"DISTANCE",
          "durationValueType":"KM",
          "durationValue":{
            "$numberInt":"12"
          }
        },
        {
          "intensity":"INTERVAL",
          "targetType":"OPEN",
          "durationType":"TIME",
          "durationValue":{
            "$numberInt":"10"
          }
        }
      ]
    },
    {
      "intensity":"COOLDOWN",
      "targetType":"OPEN",
      "durationType":"TIME",
      "durationValue":{
        "$numberInt":"600"
      }
    }
  ],
  "variants":[
    
  ],
  "coach_id":{
    "$numberInt":"4"
  }
}
```

## Text & Image session

Text and image session object

Property | Description
--------- | -----------
id | The ID of the session (int)
coach | Coach creator ID (int or Coach model instance)
title | title of the session (string)
description | description of the session (string)
tags | list of tags choose by the creator (Array of string)
session | content of the session produced by timyMce (html string)



## Session builder -->

<!-- ****** -->
<!-- SHARED -->
<!-- ****** -->

# Shared REST API

## Sport

`reverse URL shared_rest:sport`

Property | Description | Type
--------- | ----------- | -----------
name | Name of the sport  | String

```shell
curl --location --request GET 'https://dev.planif.fr/api-shared/sport/'
```

> The GET command returns a list of all possible sport as an array of string structured like this:

```json
[
    "RUNNING",
    "CYCLING",
    "SWIMMING",
    "WORKOUT",
    "SKIING",
    "CLIMBING"
]
```

### Get all sports

`GET /api-shared/sport/`

This endpoint retrieves all the sports available on Planif.

## Profile Coach

`reverse URL shared_rest:profile-coach`

Property | Description | Type
--------- | ----------- | -----------
first_name | First name  | String
last_name | Last name  | String
birth_date | Birth date in a YYYY-MM-DD format  | String
phone_number | Full phone number with the country code prepended  | String
height | Height in meters | Float
weight | Weight in grams | Float
address | Full address | String
profile_picture | Relative url of the profile picture, or the default picture if none. It is relative to the base url | String
sex | Sex of the coach, 0 if male, 1 if female, can be null | Boolean
age | Age in years, read-only field, can be null if empty birth_date | Integer

```shell
curl -v \
	-X GET \
	-H "Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476" \
	"https://dev.planif.fr/api-shared/profile-coach/"
```

> The above command returns JSON structured like this:

```json
{
"first_name": "John",
"last_name": "Doe",
"birth_date": "1998-12-28",
"height": {
  "unit": "m",
  "value": 2
},
"weight": {
  "unit": "g",
  "value": 90718.4
},
"phone_number": "+33751515151",
"sex": false,
"age": 23,
"address": "12 Jean Jaures, 38000 Grenoble",
"profile_picture": "/mediafiles/1/4ujo5kXS4AjWufTY88YdgV/43336475_054_ea9e.jpg"
}
```

### HTTP Request

`GET /api-shared/profile-coach/`

This endpoint retrieves the coach profile.

### HTTP Request

`PATCH /api-shared/profile-coach/`

This endpoint patch (update partially) the coach profile. You can pass one or more query parameters to update the profile.

```shell
curl -v \
	-X PATCH \
	-H "Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476" \
	-H "Content-Type: application/x-www-form-urlencoded; charset=utf-8" \
	-d "address=12%20Jean%20Jaures%2C%2038000%20Grenoble&height_unit=cm&height_value=200&phone_number=%2B33751515151" \
	"https://dev.planif.fr/api-shared/profile-coach/"
```

> The above command returns the updated profile in JSON structured like this:

```json
{
"first_name": "Jack",
"last_name": "Deen",
"birth_date": "1998-12-28",
"height": {
  "unit": "cm",
  "value": 200
},
"weight": {
  "unit": "g",
  "value": 90718.4
},
"phone_number": "+33751515151",
"address": "12 Jean Jaures, 38000 Grenoble",
"sex": false,
"age": 23,
"profile_picture": "/mediafiles/1/4ujo5kXS4AjWufTY88YdgV/43336475_054_ea9e.jpg"
}
```
## Profile Club

`reverse URL shared_rest:profile-club`

Property | Description | Type
--------- | ----------- | -----------
club_name | club name  | String
creation_date | Creation date in a YYYY-MM-DD format  | String
phone_number | Full phone number with the country code prepended  | String
address | Full address | String
profile_picture | Relative url of the profile picture, or the default picture if none. It is relative to the base url | String
age | Age in years, read-only field, can be null if empty creation_date | Integer

```shell
curl --location --request GET 'http://localhost:8000/api-shared/profile-club/' \
--header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjU0ODEwNDg4LCJpYXQiOjE2NTQ4MDY4ODgsImp0aSI6ImFhZjE4YmYyYzdiYjQ5MDE5MWQwZWFlMzQ5YzUzYjNkIiwidXNlcl9pZCI6MTN9.XcAQWfoxdgYT2Pk256oz1tmuUmuHKspQGPK0XY-E_VI'
```

> The above command returns JSON structured like this:

```json
{
    "club_name": "Cluuub",
    "creation_date": null,
    "phone_number": null,
    "age": null,
    "address": null,
    "profile_picture": null,
    "profile_picture_id": null
}
```

### HTTP Request

`GET /api-shared/profile-club/`

This endpoint retrieves the club profile.

### HTTP Request

`PATCH /api-shared/profile-club/`

This endpoint patch (update partially) the club profile. You can pass one or more query parameters to update the profile.

```shell
curl --location --request PATCH 'http://localhost:8000/api-shared/profile-club/' \
--header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjU0ODEwNDg4LCJpYXQiOjE2NTQ4MDY4ODgsImp0aSI6ImFhZjE4YmYyYzdiYjQ5MDE5MWQwZWFlMzQ5YzUzYjNkIiwidXNlcl9pZCI6MTN9.XcAQWfoxdgYT2Pk256oz1tmuUmuHKspQGPK0XY-E_VI' \
--header 'Content-Type: application/json' \
--data-raw '{
"club_name": "New club name",
"creation_date": "2022-02-23",
"phone_number":"+33651024955",
"address":"17 Chemin de la Capuche Grenoble 38100 France"
}'
```

> The above command returns the updated profile in JSON structured like this:

```json
{
    "club_name": "New club name",
    "creation_date": "2022-02-23",
    "phone_number": "+33651024955",
    "age": 0,
    "address": "17 Chemin de la Capuche Grenoble 38100 France",
    "profile_picture": null,
    "profile_picture_id": null
}
```

## Profile Athlete

`reverse URL shared_rest:profile-athlete`

Property | Description | Type
--------- | ----------- | -----------
first_name | First name  | String
last_name | Last name  | String
birth_date | Birth date in a YYYY-MM-DD format  | String
phone_number | Full phone number with the country code prepended  | String
height | Height in meters | Float
weight | Weight in grams | Float
address | Full address | String
profile_picture | Relative url of the profile picture, or the default picture if none. It is relative to the base url | String
sex | Sex, 0 if male, 1 if female, can be null | Boolean
age | Age in years, read-only field, can be null if empty birth_date | Integer

```shell
curl -v \
	-X GET \
	-H "Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476" \
	"https://dev.planif.fr/api-shared/profile-athlete/"
```

> The above command returns JSON structured like this:

```json
{
"first_name": "John",
"last_name": "Doe",
"birth_date": "1998-12-28",
"height": {
  "unit": "m",
  "value": 2
},
"weight": {
  "unit": "g",
  "value": 90718.4
},
"phone_number": "+33751515151",
"sex": false,
"age": 23,
"address": "12 Jean Jaures, 38000 Grenoble",
"profile_picture": "/mediafiles/1/4ujo5kXS4AjWufTY88YdgV/43336475_054_ea9e.jpg"
}
```

### HTTP Request

`GET /api-shared/profile-athlete/`

This endpoint retrieves the athlete profile.

### HTTP Request

`PATCH /api-shared/profile-athlete/`

This endpoint patch (update partially) the coach profile. You can pass one or more query parameters to update the profile.

```shell
curl -v \
	-X PATCH \
	-H "Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476" \
	-H "Content-Type: application/x-www-form-urlencoded; charset=utf-8" \
	-d "address=12%20Jean%20Jaures%2C%2038000%20Grenoble&height_unit=cm&height_value=200&phone_number=%2B33751515151" \
	"https://dev.planif.fr/api-shared/profile-coach/"
```

> The above command returns the updated profile in JSON structured like this:

```json
{
"first_name": "Jack",
"last_name": "Deen",
"birth_date": "1998-12-28",
"height": {
  "unit": "cm",
  "value": 200
},
"weight": {
  "unit": "g",
  "value": 90718.4
},
"phone_number": "+33751515151",
"address": "12 Jean Jaures, 38000 Grenoble",
"sex": false,
"age": 23,
"profile_picture": "/mediafiles/1/4ujo5kXS4AjWufTY88YdgV/43336475_054_ea9e.jpg"
}
```

### Query Parameters that are allowed

Parameter | Description | Type
--------- | ------- | -----------
first_name | First name  | String
last_name | Last name  | String
birth_date | Birth date in a MM/DD/YYYY format  | String
phone_number | Full phone number with the country code prepended  | String
height_value | Height value corresponding to the unit in the query | Float
height_unit | Height unit one of ('cm', 'm', 'inch', 'ft')| String
weight_value | Weight value corresponding to the unit in the query | Float
weight_unit | Weight unit one of ('kg', 'g', 'lb')| String
address | Full address | String

<aside class="warning">When updating the weight or height, _unit must be set</aside>


## Profile picture

`reverse URL shared_rest:profile-picture`

HTTP Code | Meaning
---------- | -------
201 | Created -- Your picture has been successfully uploaded.
204 | No content -- Your picture has been delete.
400 | Bad request -- Bad format or type error.
404 | Not Found -- Your temporary picture or uploaded could not be found.


```javascript
```

### HTTP Request

`POST /api-shared/profile-picture/`

Store a temporary uploaded object and update the profile picture filed in the database

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | upload_id assigned by filepond_drf

`DELETE /api-share/profile_picture/`

Delete the profile picture and set the field to default in database

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | upload_id assigned by filepond_drf


<!-- # Plan -->

# Coach REST API

<aside class="notice">For all the next endpoints, you will need to be authenticated as a Coach and sending request containing a Bearer with such headers <code>Authorization: Bearer <your_token></code>.</aside>

## Plan

`reverse URL coach_rest:plan-coach`
`reverse URL coach_rest:plan-coach-obj`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the plan  | Integer
name | Name of the plan  | String
coach | Id of the coach, owner of the plan  | Integer
description | Description of the plan (optional)  | String
duration | Duration of a static plan in week, available only if the plan is static  | Integer
price | Price of a public plan in Eur, available only if the plan is public  | Integer
rate | The rating of the plan, average of all the rate given by the athlete. Could be null, cannot be changed by this endpoint  | Float
is_public | True if the plan is public, false otherwise  | Boolean
is_static | True if the plan is static, false otherwise  | Boolean
athletes | List of 4 random selected athletes linked to this plan to display the avatars | List of athletes object as specified below
count_athletes | Number of athletes linked to this plan | Integer

Athlete object in the list of athletes

Property | Description | Type
--------- | ----------- | -----------
id | Id of the athlete  | Integer
first_name | First name of the athlete  | String
last_name | Last name of the athlete  | String
email | Email of the athlete  | String
username | Username of the athlete  | String
profile_picture | link source of the profile picture of the athlete, could be null  | String


```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/plan/' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns a list of plans as JSON structured like this:

```json
[
    {
        "id": 2,
        "name": "Ronaldo training week",
        "coach": 8,
        "description": "Be ready to unleash your inner footbal",
        "duration": null,
        "price": "12.00",
        "rate": null,
        "athletes": [
            {
                "first_name": "Lucas",
                "last_name": "Damalix",
                "profile_picture": "http://localhost:8000/mediafiles/media/2/profile/Riccione FINP.jpg",
                "email": "terspychore.yt@gmail.com",
                "username": "terspychore.yt",
                "id": 2
            },
            {
                "first_name": "Lucas",
                "last_name": "Damalix",
                "profile_picture": null,
                "email": "lucasdamaev@gmail.com",
                "username": "Terspy",
                "id": 5
            }
        ],
        "count_athletes": 2,
        "is_public": true,
        "is_static": false
    }
]
```

### Get all plans

`GET /api-coach/plan/`

This endpoint retrieves all the coach plans.

### Create an plan

`POST /api-coach/plan/`

This endpoint is used to create a training plan. You have to pass at the minimum all the required fields or more to create an plan.

To make a plan public, use the price paramater. To make the plan static, use the duration parameter.

By default, the plan will be private and dynamic.

```shell
curl --location --request POST 'https://dev.planif.fr/api-coach/plan/' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'name="My insane plan"' \
--form 'description="Be ready to become fiiiiit AF"' \
--form 'price="123.32"' \
--form 'duration="2"'
```

> The POST command returns the created plan in JSON structured like this:

```json
{
    "id": 17,
    "name": "My insane plan",
    "coach": 1,
    "description": "Be ready to become fiiiiit AF",
    "duration": 2,
    "rate": null,
    "price": "123.32",
    "is_public": true,
    "is_static": true
}
```

### Get a specific plan 

`GET /api-coach/plan/<id>/`

This endpoint is used to get a coach specific plan. You have to pass the id of the plan

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/plan/4' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns the target plan in JSON structured like this:

```json
{
    "id": 2,
    "name": "Ronaldo training week",
    "coach": 8,
    "description": "Be ready to unleash your inner footbal",
    "duration": null,
    "price": "12.00",
    "rate": null,
    "athletes": [
        {
            "first_name": "Lucas",
            "last_name": "Damalix",
            "profile_picture": null,
            "email": "lucasdamaev@gmail.com",
            "username": "Terspy",
            "id": 5
        },
        {
            "first_name": "Lucas",
            "last_name": "Damalix",
            "profile_picture": "http://localhost:8000/mediafiles/media/2/profile/Riccione FINP.jpg",
            "email": "terspychore.yt@gmail.com",
            "username": "terspychore.yt",
            "id": 2
        }
    ],
    "count_athletes": 2,
    "is_public": true,
    "is_static": false
}
```

### Modify a plan

`PATCH /api-coach/plan/<id>/`

This endpoint is used to update a coach training plan. You have to pass the id of the plan in the url and the data you want to modify as params. 

You can update partially the data. 

To make the plan static simply pass the duration, to make it dynamic, pass an empty duration. Same goes for the is_public attribute : to make the plan public, pass a price, to make it private pass an empty price. 

```shell
curl --location --request PATCH 'https://dev.planif.fr/api-coach/plan/4' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'price=""'
```

> If successful the PATCH command returns the updated plan in JSON structured like this:

```json
{
    "id": 4,
    "name": "Nice plan",
    "coach": 1,
    "description": "Excellent",
    "rate": null,
    "is_public": false,
    "is_static": false
}
```

### Delete a specific plan

`DELETE /api-coach/plan/<id>/`

This endpoint is used to delete a coach training plan. You have to pass the id of the plan. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'https://dev.planif.fr/api-coach/plan/3' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

### Link a plan to an athlete

`POST /api-coach/link-athlete-to-plan/`

This endpoint is used to link a training plan to a specific athlete. You have to pass the id of the plan and the id of the athlete  . If successful the request will return a 201 Created

```shell
curl --location --request POST 'http://localhost:8000/api-coach/link-athlete-to-plan/' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "plan": 2,
    "athlete": 2
}'
```

### Unlink a plan to an athlete

`DELETE /api-coach/link-athlete-to-plan/`

This endpoint is used to unlink a training plan to a specific athlete. You have to pass the id of the plan and the id of the athlete  . If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'http://localhost:8000/api-coach/link-athlete-to-plan/' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "plan": 2,
    "athlete": 2
}'
```
## Experience

`reverse URL coach_rest:experience-coach`
`reverse URL coach_rest:experience-coach-obj`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the experience  | Integer
position | Position in the company  | String
company | Company where he used to work  | String
start_date | Start date of the experience  | String
end_date | End date of the experience (could be null if today)  | String
description | Description of the experience (optional) | String
company_url | Company url (optional) | String

```shell
curl -v \
	-X GET \
	-H "Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476" \
	"https://dev.planif.fr/api-coach/experience/"
```

> The GET command returns a list of experiences as JSON structured like this:

```json
[
    {
        "id": 1,
        "position": "Position test",
        "company": "Company",
        "start_date": "2020-10-20",
        "end_date": null,
        "description": "Yay",
        "company_url": null,
        "coach": 1
    },
    {
        "id": 2,
        "position": "Position test",
        "company": "Company",
        "start_date": "2020-10-20",
        "end_date": "2022-01-01",
        "description": "Yay",
        "company_url": "https://gitlab.com/planif/django-ec2/-/pipelines",
        "coach": 1
    }
]
```

### Get all experiences

`GET /api-coach/experience/`

This endpoint retrieves the coach experiences.

### Create an experience

`POST /api-coach/experience/`

This endpoint is used to create a coach experience. You have to pass at the minimum all the required fields or more to create an experience

```shell
curl --location --request POST 'https://dev.planif.fr/api-coach/experience/' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'position="Position test"' \
--form 'company="Company"' \
--form 'start_date="2020-10-20"' \
--form 'description="Yay"' \
--form 'end_date="2022-01-01"' \
--form 'company_url="https://gitlab.com/planif/django-ec2/-/pipelines"'
```

> The POST command returns the created experience in JSON structured like this:

```json
{
    "id": 3,
    "position": "Position test",
    "company": "Company",
    "start_date": "2020-10-20",
    "end_date": "2022-01-01",
    "description": "Yay",
    "company_url": "https://gitlab.com/planif/django-ec2/-/pipelines",
    "coach": 1
}
```

### Get a specific experience 

`GET /api-coach/experience/<id>`

This endpoint is used to get a coach experience. You have to pass the id of the experience

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/experience/2' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns the target experience in JSON structured like this:

```json
{
    "id": 2,
    "position": "Position test",
    "company": "Company",
    "start_date": "2020-10-20",
    "end_date": "2022-01-01",
    "description": "Yay",
    "company_url": "https://gitlab.com/planif/django-ec2/-/pipelines",
    "coach": 1
}
```

### Modify an experience

`PATCH /api-coach/experience/<id>`

This endpoint is used to update a coach experience. You have to pass the id of the experience in the url and the data you want to modify as params. You can update partially the data.

```shell
curl --location --request PATCH 'https://dev.planif.fr/api-coach/experience/2' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'position="New position"'
```

> If successful the PATCH command returns the updated experience in JSON structured like this:

```json
{
    "id": 2,
    "position": "New position",
    "company": "Company",
    "start_date": "2020-10-20",
    "end_date": "2022-01-01",
    "description": "Yay",
    "company_url": "https://gitlab.com/planif/django-ec2/-/pipelines",
    "coach": 1
}
```

### Delete a specific experience

`DELETE /api-coach/experience/<id>`

This endpoint is used to delete a coach experience. You have to pass the id of the experience. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'https://dev.planif.fr/api-coach/experience/10' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

## Education

`reverse URL coach_rest:education-coach`
`reverse URL coach_rest:education-coach-obj`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the education  | Integer
title | Title of education  | String
institution | Institution of the education  | String
start_date | Start date of the education  | String
end_date | End date of the education (could be null if today)  | String
description | Description of the education (optional) | String

```shell
curl -v \
	-X GET \
	-H "Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476" \
	"https://dev.planif.fr/api-coach/education/"
```

> The GET command returns a list of educations as JSON structured like this:

```json
[
    {
        "id": 1,
        "title": "Title test",
        "institution": "institution",
        "start_date": "2020-10-20",
        "end_date": "2022-01-01",
        "description": "Yay",
        "coach": 1
    },
    {
        "id": 2,
        "title": "Title test 2",
        "institution": "institution 2",
        "start_date": "2020-10-20",
        "end_date": null,
        "description": null,
        "coach": 1
    }
]
```

### Get all educations

`GET /api-coach/education/`

This endpoint retrieves the coach educations.

### Create an education

`POST /api-coach/education/`

This endpoint is used to create a coach education. You have to pass at the minimum all the required fields or more to create an education

```shell
curl --location --request POST 'https://dev.planif.fr/api-coach/education/' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57' \
--form 'title="Title test"' \
--form 'institution="institution"' \
--form 'start_date="2020-10-20"' \
--form 'description="Yay"' \
--form 'end_date="2022-01-01"'
```

> The POST command returns the created education in JSON structured like this:

```json
{
    "id": 1,
    "title": "Title test",
    "institution": "institution",
    "start_date": "2020-10-20",
    "end_date": "2022-01-01",
    "description": "Yay",
    "coach": 1
}
```

### Get a specific education 

`GET /api-coach/education/<id>`

This endpoint is used to get a coach education. You have to pass the id of the education

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/education/2' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57'
```

> The GET command returns the target education in JSON structured like this:

```json
{
    "id": 2,
    "title": "Title test 2",
    "institution": "institution 2",
    "start_date": "2020-10-20",
    "end_date": null,
    "description": null,
    "coach": 1
}
```

### Modify an education

`PATCH /api-coach/education/<id>`

This endpoint is used to update a coach education. You have to pass the id of the education in the url and the data you want to modify as params. You can update partially the data.

```shell
curl --location --request PATCH 'https://dev.planif.fr/api-coach/education/1' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57' \
--form 'institution="New institution"'
```

> If successful the PATCH command returns the updated education in JSON structured like this:

```json
{
    "id": 1,
    "title": "Title test",
    "institution": "New institution",
    "start_date": "2020-10-20",
    "end_date": "2022-01-01",
    "description": "Yay",
    "coach": 1
}
```

### Delete a specific education

`DELETE /api-coach/education/<id>`

This endpoint is used to delete a coach education. You have to pass the id of the education. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'https://dev.planif.fr/api-coach/education/2' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57'
```

## Socials

Property | Description | Type
--------- | ----------- | -----------
facebook_url | Url of facebook profile, could be null  | String
twitter_url | Url of twitter profile, could be null  | String
instagram_url | Url of instagram profile, could be null  | String
youtube_url | Url of youtube profile, could be null  | String
linkedin_url | Url of linkedin profile, could be null  | String
website_url | Url of website profile, could be null  | String

```shell
curl --location --request GET 'http://localhost:8000/api-coach/socials/' \
--header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjU1MjA1MDk4LCJpYXQiOjE2NTUyMDE0OTgsImp0aSI6IjgxNzgwMjBhNTViNjQwYzk5MmY4YjEyOWUxNzIxOGE3IiwidXNlcl9pZCI6OH0.lNc9icQlfU6Vhj7_cGFherhvimwRt03mf8MmSrXc_Bw'
```

> The GET command returns a list of socials as JSON structured like this:

```json
{
    "facebook_url": null,
    "twitter_url": null,
    "instagram_url": null,
    "youtube_url": null,
    "linkedin_url": null,
    "website_url": null
}
```

### Get coach socials

`GET /api-coach/socials/`

This endpoint retrieves the coach social.

### Patch socials

`PATCH /api-coach/socials/`

This endpoint is used to patch the coach socials.

> The PATCH command returns the coach socials in JSON structured like this:

```json
{
    "facebook_url": null,
    "twitter_url": null,
    "instagram_url": null,
    "youtube_url": null,
    "linkedin_url": null,
    "website_url": null
}
```

## Skill

`reverse URL coach_rest:skill-coach`
`reverse URL coach_rest:skill-coach-obj`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the skill  | Integer
name | Name of the skill  | String
percentage | Percentage of the skill, int min: 0, max: 100  | Integer

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/skill/' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57'
```

> The GET command returns a list of skills as JSON structured like this:

```json
[
    {
        "id": 1,
        "name": "friendly",
        "percentage": 85,
        "coach": 1
    },
    {
        "id": 2,
        "name": "effiency",
        "percentage": 99,
        "coach": 1
    }
]
```

### Get all skills

`GET /api-coach/skill/`

This endpoint retrieves the coach skills.

### Create a skill

`POST /api-coach/skill/`

This endpoint is used to create a coach skill. You have to pass the name and the percentage to create a skill

```shell
curl --location --request POST 'https://dev.planif.fr/api-coach/skill/' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57' \
--form 'name="friendly"' \
--form 'percentage="85"'
```

> The POST command returns the created skill in JSON structured like this:

```json
{
    "id": 1,
    "name": "friendly",
    "percentage": 85,
    "coach": 1
}
```

### Get a specific skill 

`GET /api-coach/skill/<id>`

This endpoint is used to get a coach skill. You have to pass the id of the skill

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/skill/2' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57'
```

> The GET command returns the target skill in JSON structured like this:

```json
{
    "id": 2,
    "name": "effiency",
    "percentage": 99,
    "coach": 1
}
```

### Modify a skill

`PATCH /api-coach/skill/<id>`

This endpoint is used to update a coach skill. You have to pass the id of the skill in the url and the data you want to modify as params. You can update partially the data.

```shell
curl --location --request PATCH 'https://dev.planif.fr/api-coach/skill/1' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57' \
--form 'percentage="77"'
```

> If successful the PATCH command returns the updated skill in JSON structured like this:

```json
{
    "id": 1,
    "name": "friendly",
    "percentage": 77,
    "coach": 1
}
```

### Delete a specific skill

`DELETE /api-coach/skill/<id>`

This endpoint is used to delete a coach skill. You have to pass the id of the skill. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'https://dev.planif.fr/api-coach/skill/2' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57'
```

## Hashtag

`reverse URL coach_rest:hashtag-coach`
`reverse URL coach_rest:hashtag-coach-obj`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the hashtag  | Integer
name | Name of the hashtag  | String

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/hashtag/' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57'
```

> The GET command returns a list of skills as JSON structured like this:

```json
[
    {
        "id": 1,
        "name": "efficient",
        "coach": 1
    },
    {
        "id": 2,
        "name": "devoted",
        "coach": 1
    }
]
```

### Get all hashtags

`GET /api-coach/hashtag/`

This endpoint retrieves the coach hashtags.

### Create a hashtag

`POST /api-coach/hashtag/`

This endpoint is used to create a coach hashtag. You have to pass the nameto create a hashtag

```shell
curl --location --request POST 'https://dev.planif.fr/api-coach/hashtag/' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57' \
--form 'name="devoted"'
```

> The POST command returns the created hashtag in JSON structured like this:

```json
{
    "id": 2,
    "name": "devoted",
    "coach": 1
}
```

### Get a specific hashtag 

`GET /api-coach/hashtag/<id>`

This endpoint is used to get a coach hashtag. You have to pass the id of the hashtag

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/hashtag/1' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57'
```

> The GET command returns the target hashtag in JSON structured like this:

```json
{
    "id": 1,
    "name": "efficient",
    "coach": 1
}
```

### Modify a hashtag

`PATCH /api-coach/hashtag/<id>`

This endpoint is used to update a coach hashtag. You have to pass the id of the skill in the url and the data you want to modify as params. You can update partially the data.

```shell
curl --location --request PATCH 'https://dev.planif.fr/api-coach/hashtag/1' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57' \
--form 'name="new name"'
```

> If successful the PATCH command returns the updated hashtag in JSON structured like this:

```json
{
    "id": 1,
    "name": "new name",
    "coach": 1
}
```

### Delete a hashtag skill

`DELETE /api-coach/hashtag/<id>`

This endpoint is used to delete a coach hashtag. You have to pass the id of the hashtag. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'https://dev.planif.fr/api-coach/hashtag/2' \
--header 'Authorization: Bearer a7816be6d761730bbca7b3de33d7b76467786b57'
```

## Training Planned

`reverse URL coach_rest:training-planned`

This endpoint is used to retrieve, create, update training planned 


```javascript
```

### HTTP Request

`GET /api-coach/training-planned/?id=`

Used to retrieve a training planned

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | ID of the training planned (Integer)

### HTTP Request

`POST /api-coach/training-planned/`

Used to creates a training planned by sending data as a json like

> Data shoud be a json like this:

```json
[
  {
    "title": "title_training",
    "description": "description_training",
    "sport": "triathlon",
    "date": "2022-03-12",
    "duration": 3300,
    "is_morning": true,
    "athletes": [1, 2, 3],
    "sessions": [1, 2, 3],
  }
]
```

### HTTP Request

`PATCH /api-coach/training-planned/`

Used to update a training planned, data should be send as json with an ID field, data could be partial

> Data shoud be a json like this:

```json
[
  {
    "id": 12,
    "description": "new_description_training",
    "sport": "running",
    "sessions": [5, 4],
  }
]
```


## Athletes

`reverse URL coach_rest:list-athletes-coach`

Property | Description
--------- | -----------
athlete_id | The ID of the athlete
first_name | (string)
last_name | (string)
email | (string)
profile_picture | upload_id of the profile picture created by filepond_drf, null if no profile picture (string)


```javascript
```

> The above command returns JSON structured like this:

```json
{
  "athlete_id": 1,
    "first_name": "Lucas",
    "last_name": "Damalix",
    "email": "lucas.damalix@planif.fr",
    "profile_picture": "4hK2NvuZJD34oWmvnBSeKo"
}
```


### HTTP Request

`GET /api-coach/list-athletes-coach/`

This endpoint retrieves the athletes of a coach.

## Text Session

`reverse URL coach_rest:text-session-list`
`reverse URL coach_rest:text-session-detail`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the text session  | Integer
title | Title of the text session max_length=100  | String
description | Description of the text session (optional) max_length=500  | String
session | Body of the session (HTML markup)  | String
tags | Array of tags describing the session  | Array of String
coach | Id of the coach owner of the session  | Integer
estimated_duration | Estimated duration of the session in seconds (optional)  | Integer
sport | Name of the sport | String

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/text-session' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns a list of text sessions as JSON structured like this:

```json
[
    {
        "id": 2,
        "title": "A text session",
        "description": "Be ready to unleash your inner footbal",
        "tags": [
            "easy",
            " jogging"
        ],
        "session": "<p>1 hour easy jogging</p>",
        "coach": 1,
        "sport": "RUNNING",
        "estimated_duration": null
    },
    {
        "id": 3,
        "title": "A text session",
        "description": "Be ready to unleash your inner footbal",
        "tags": [
            "easy"
        ],
        "session": "<p>1 hour easy jogging</p>",
        "coach": 1,
        "sport": "CYCLING",
        "estimated_duration": null
    }
]
```

### Get all text session

`GET /api-coach/text-session`

This endpoint retrieves the coach text sessions.

### Create a text session

`POST /api-coach/text-session`

This endpoint is used to create a text session. You have to pass the minimum parameters to create a text session

```shell
curl --location --request POST 'https://dev.planif.fr/api-coach/text-session' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'title="A text session"' \
--form 'description="Be ready to unleash your inner footbal"' \
--form 'tags="easy, jogging"' \
--form 'session="<p>1 hour easy jogging</p>"'
--form 'sport="CYCLING"'
```

> The POST command returns the created text session in JSON structured like this:

```json
{
    "id": 3,
    "title": "A text session",
    "description": "Be ready to unleash your inner footbal",
    "tags": [
        "easy",
        " jogging"
    ],
    "session": "<p>1 hour easy jogging</p>",
    "coach": 1,
    "sport": "CYCLING",
    "estimated_duration": null
}
```

### Get a specific text session 

`GET /api-coach/text-session/<id>`

This endpoint is used to get a text session. You have to pass the id of the text session

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/text-session/2' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns the target text session in JSON structured like this:

```json
{
    "id": 2,
    "title": "A text session",
    "description": "Be ready to unleash your inner footbal",
    "tags": [
        "easy",
        " jogging"
    ],
    "session": "<p>1 hour easy jogging</p>",
    "coach": 1,
    "sport": "RUNNING",
    "estimated_duration": null
}
```

### Modify a text session

`PATCH /api-coach/text-session/<id>`

This endpoint is used to update a text session. You have to pass the id of the text session in the url and the data you want to modify as params. You can update partially the data.

```shell
curl --location --request PATCH 'https://dev.planif.fr/api-coach/text-session/2' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'title="New title 2"' \
--form 'tags="Hard, run, yeah"'
```

> If successful the PATCH command returns the updated text session in JSON structured like this:

```json
{
    "id": 2,
    "title": "New title 2",
    "description": "Be ready to unleash your inner footbal",
    "tags": [
        "Hard",
        "run",
        "yeah"
    ],
    "session": "<p>1 hour easy jogging</p>",
    "coach": 1,
    "sport": "CYCLING",
    "estimated_duration": null
}
```

### Delete a specific text session

`DELETE /api-coach/text-session/<id>`

This endpoint is used to delete a text session. You have to pass the id of the text session. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'https://dev.planif.fr/api-coach/text-session/2' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

## Built Session

`reverse URL coach_rest:built-session-list`
`reverse URL coach_rest:built-session-detail`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the built session  | Integer
title | Title of the built session max_length=100  | String
description | Description of the built session (optional) max_length=500  | String
steps | Steps of the session created by the session Builder | JSON
variants | Variants of the session created by the session Builder (multiple steps) | JSON
tags | Array of tags describing the session  | Array of String
coach | Id of the coach owner of the session  | Integer
estimated_duration | Estimated duration of the session in seconds. This field can be given or automatically calculated with the steps or mean of durations if variants  | Integer
sport | Name of the sport | String

Either Steps or Variants must be set but not both at the same time

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/built-session' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns a list of built sessions as JSON structured like this:

```json
[
    {
        "id": 2,
        "title": "A text session",
        "description": "Be ready to unleash your inner footbal",
        "sport": "CYCLING",
        "tags": [
            "Hard",
            "run",
            "yop"
        ],
        "steps": [
            {
                "intensity": "WARMUP",
                "targetType": "OPEN",
                "durationType": "TIME",
                "durationValue": {
                    "$numberInt": "1200"
                }
            },
            {
                "steps": [
                    {
                        "intensity": "INTERVAL",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "60"
                        }
                    },
                    {
                        "intensity": "INTERVAL",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "60"
                        }
                    },
                    {
                        "intensity": "INTERVAL",
                        "targetType": "OPEN",
                        "durationType": "DISTANCE",
                        "durationValue": {
                            "$numberInt": "12"
                        },
                        "durationValueType": "KM"
                    },
                    {
                        "intensity": "INTERVAL",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "10"
                        }
                    }
                ],
                "repeatValue": {
                    "$numberInt": "4"
                },
                "uuid-Comment": "a0612b3ef9024151b3947a5e6ac5da7b"
            },
            {
                "intensity": "COOLDOWN",
                "targetType": "OPEN",
                "durationType": "TIME",
                "durationValue": {
                    "$numberInt": "600"
                }
            }
        ],
        "variants": "",
        "coach": 1
    },
    {
        "id": 3,
        "title": "A built session run",
        "description": "Be ready to unleash your inner footbal",
        "sport": "RUNNING",
        "tags": [
            "easy",
            " jogging"
        ],
        "steps": "",
        "variants": [
            {
                "name": "Beginner",
                "steps": [
                    {
                        "intensity": "WARMUP",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "1200"
                        }
                    },
                    {
                        "steps": [
                            {
                                "steps": [
                                    {
                                        "intensity": "INTERVAL",
                                        "targetType": "SPEED_LAP",
                                        "targetValue": "5",
                                        "durationType": "TIME",
                                        "durationValue": {
                                            "$numberInt": "30"
                                        }
                                    },
                                    {
                                        "intensity": "RECOVERY",
                                        "targetType": "OPEN",
                                        "durationType": "TIME",
                                        "durationValue": {
                                            "$numberInt": "30"
                                        }
                                    }
                                ],
                                "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                                "repeatValue": {
                                    "$numberInt": "6"
                                }
                            },
                            {
                                "intensity": "COOLDOWN",
                                "targetType": "OPEN",
                                "durationType": "TIME",
                                "durationValue": {
                                    "$numberInt": "240"
                                }
                            }
                        ],
                        "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                        "repeatValue": {
                            "$numberInt": "2"
                        }
                    },
                    {
                        "intensity": "COOLDOWN",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "360"
                        }
                    }
                ]
            },
            {
                "name": "Intermediate",
                "steps": [
                    {
                        "intensity": "WARMUP",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "1200"
                        }
                    },
                    {
                        "steps": [
                            {
                                "steps": [
                                    {
                                        "intensity": "INTERVAL",
                                        "targetType": "SPEED_LAP",
                                        "targetValue": "5",
                                        "durationType": "TIME",
                                        "durationValue": {
                                            "$numberInt": "30"
                                        }
                                    },
                                    {
                                        "intensity": "RECOVERY",
                                        "targetType": "OPEN",
                                        "durationType": "TIME",
                                        "durationValue": {
                                            "$numberInt": "30"
                                        }
                                    }
                                ],
                                "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                                "repeatValue": {
                                    "$numberInt": "8"
                                }
                            },
                            {
                                "intensity": "COOLDOWN",
                                "targetType": "OPEN",
                                "durationType": "TIME",
                                "durationValue": {
                                    "$numberInt": "240"
                                }
                            }
                        ],
                        "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                        "repeatValue": {
                            "$numberInt": "2"
                        }
                    },
                    {
                        "intensity": "COOLDOWN",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "360"
                        }
                    }
                ]
            },
            {
                "name": "Expert",
                "steps": [
                    {
                        "intensity": "WARMUP",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "1800"
                        }
                    },
                    {
                        "steps": [
                            {
                                "steps": [
                                    {
                                        "intensity": "INTERVAL",
                                        "targetType": "SPEED_LAP",
                                        "targetValue": "5",
                                        "durationType": "TIME",
                                        "durationValue": {
                                            "$numberInt": "30"
                                        }
                                    },
                                    {
                                        "intensity": "RECOVERY",
                                        "targetType": "OPEN",
                                        "durationType": "TIME",
                                        "durationValue": {
                                            "$numberInt": "30"
                                        }
                                    }
                                ],
                                "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                                "repeatValue": {
                                    "$numberInt": "8"
                                }
                            },
                            {
                                "intensity": "COOLDOWN",
                                "targetType": "OPEN",
                                "durationType": "TIME",
                                "durationValue": {
                                    "$numberInt": "240"
                                }
                            }
                        ],
                        "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                        "repeatValue": {
                            "$numberInt": "2"
                        }
                    },
                    {
                        "intensity": "COOLDOWN",
                        "targetType": "OPEN",
                        "durationType": "TIME",
                        "durationValue": {
                            "$numberInt": "360"
                        }
                    }
                ]
            }
        ],
        "coach": 1
    }
]
```

### Get all built session

`GET /api-coach/built-session`

This endpoint retrieves the coach built sessions.

### Create a built session

`POST /api-coach/built-session`

This endpoint is used to create a built session. You have to pass the minimum parameters to create a built session

```shell
curl --location --request POST 'https://dev.planif.fr/api-coach/built-session' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'title="A built session run"' \
--form 'description="Be ready to unleash your inner footbal"' \
--form 'tags="easy, jogging"' \
--form 'sport="RUNNING"' \
--form 'variants="[
    {
      \"name\":\"Beginner\",
      \"steps\":[
        {
          \"intensity\":\"WARMUP\",
          \"targetType\":\"OPEN\",
          \"durationType\":\"TIME\",
          \"durationValue\":{
            \"$numberInt\":\"1200\"
          }
        },
        {
          \"repeatType\":\"REPEAT_UNTIL_STEPS_CMPLT\",
          \"repeatValue\":{
            \"$numberInt\":\"2\"
          },
          \"steps\":[
            {
              \"repeatType\":\"REPEAT_UNTIL_STEPS_CMPLT\",
              \"repeatValue\":{
                \"$numberInt\":\"6\"
              },
              \"steps\":[
                {
                  \"intensity\":\"INTERVAL\",
                  \"targetType\":\"SPEED_LAP\",
                  \"durationType\":\"TIME\",
                  \"durationValue\":{
                    \"$numberInt\":\"30\"
                  },
                  \"targetValue\":\"5\"
                },
                {
                  \"intensity\":\"RECOVERY\",
                  \"targetType\":\"OPEN\",
                  \"durationType\":\"TIME\",
                  \"durationValue\":{
                    \"$numberInt\":\"30\"
                  }
                }
              ]
            },
            {
              \"intensity\":\"COOLDOWN\",
              \"targetType\":\"OPEN\",
              \"durationType\":\"TIME\",
              \"durationValue\":{
                \"$numberInt\":\"240\"
              }
            }
          ]
        },
        {
          \"intensity\":\"COOLDOWN\",
          \"targetType\":\"OPEN\",
          \"durationType\":\"TIME\",
          \"durationValue\":{
            \"$numberInt\":\"360\"
          }
        }
      ]
    },
    {
      \"name\":\"Intermediate\",
      \"steps\":[
        {
          \"intensity\":\"WARMUP\",
          \"targetType\":\"OPEN\",
          \"durationType\":\"TIME\",
          \"durationValue\":{
            \"$numberInt\":\"1200\"
          }
        },
        {
          \"repeatType\":\"REPEAT_UNTIL_STEPS_CMPLT\",
          \"repeatValue\":{
            \"$numberInt\":\"2\"
          },
          \"steps\":[
            {
              \"repeatType\":\"REPEAT_UNTIL_STEPS_CMPLT\",
              \"repeatValue\":{
                \"$numberInt\":\"8\"
              },
              \"steps\":[
                {
                  \"intensity\":\"INTERVAL\",
                  \"targetType\":\"SPEED_LAP\",
                  \"durationType\":\"TIME\",
                  \"durationValue\":{
                    \"$numberInt\":\"30\"
                  },
                  \"targetValue\":\"5\"
                },
                {
                  \"intensity\":\"RECOVERY\",
                  \"targetType\":\"OPEN\",
                  \"durationType\":\"TIME\",
                  \"durationValue\":{
                    \"$numberInt\":\"30\"
                  }
                }
              ]
            },
            {
              \"intensity\":\"COOLDOWN\",
              \"targetType\":\"OPEN\",
              \"durationType\":\"TIME\",
              \"durationValue\":{
                \"$numberInt\":\"240\"
              }
            }
          ]
        },
        {
          \"intensity\":\"COOLDOWN\",
          \"targetType\":\"OPEN\",
          \"durationType\":\"TIME\",
          \"durationValue\":{
            \"$numberInt\":\"360\"
          }
        }
      ]
    },
    {
      \"name\":\"Expert\",
      \"steps\":[
        {
          \"intensity\":\"WARMUP\",
          \"targetType\":\"OPEN\",
          \"durationType\":\"TIME\",
          \"durationValue\":{
            \"$numberInt\":\"1800\"
          }
        },
        {
          \"repeatType\":\"REPEAT_UNTIL_STEPS_CMPLT\",
          \"repeatValue\":{
            \"$numberInt\":\"2\"
          },
          \"steps\":[
            {
              \"repeatType\":\"REPEAT_UNTIL_STEPS_CMPLT\",
              \"repeatValue\":{
                \"$numberInt\":\"8\"
              },
              \"steps\":[
                {
                  \"intensity\":\"INTERVAL\",
                  \"targetType\":\"SPEED_LAP\",
                  \"durationType\":\"TIME\",
                  \"durationValue\":{
                    \"$numberInt\":\"30\"
                  },
                  \"targetValue\":\"5\"
                },
                {
                  \"intensity\":\"RECOVERY\",
                  \"targetType\":\"OPEN\",
                  \"durationType\":\"TIME\",
                  \"durationValue\":{
                    \"$numberInt\":\"30\"
                  }
                }
              ]
            },
            {
              \"intensity\":\"COOLDOWN\",
              \"targetType\":\"OPEN\",
              \"durationType\":\"TIME\",
              \"durationValue\":{
                \"$numberInt\":\"240\"
              }
            }
          ]
        },
        {
          \"intensity\":\"COOLDOWN\",
          \"targetType\":\"OPEN\",
          \"durationType\":\"TIME\",
          \"durationValue\":{
            \"$numberInt\":\"360\"
          }
        }
      ]
    }
  ]"'
```

> The POST command returns the created built session in JSON structured like this:

```json
{
    "id": 3,
    "title": "A built session run",
    "description": "Be ready to unleash your inner footbal",
    "sport": "RUNNING",
    "tags": [
        "easy",
        " jogging"
    ],
    "steps": "",
    "variants": [
        {
            "name": "Beginner",
            "steps": [
                {
                    "intensity": "WARMUP",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "1200"
                    }
                },
                {
                    "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                    "repeatValue": {
                        "$numberInt": "2"
                    },
                    "steps": [
                        {
                            "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                            "repeatValue": {
                                "$numberInt": "6"
                            },
                            "steps": [
                                {
                                    "intensity": "INTERVAL",
                                    "targetType": "SPEED_LAP",
                                    "durationType": "TIME",
                                    "durationValue": {
                                        "$numberInt": "30"
                                    },
                                    "targetValue": "5"
                                },
                                {
                                    "intensity": "RECOVERY",
                                    "targetType": "OPEN",
                                    "durationType": "TIME",
                                    "durationValue": {
                                        "$numberInt": "30"
                                    }
                                }
                            ]
                        },
                        {
                            "intensity": "COOLDOWN",
                            "targetType": "OPEN",
                            "durationType": "TIME",
                            "durationValue": {
                                "$numberInt": "240"
                            }
                        }
                    ]
                },
                {
                    "intensity": "COOLDOWN",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "360"
                    }
                }
            ]
        },
        {
            "name": "Intermediate",
            "steps": [
                {
                    "intensity": "WARMUP",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "1200"
                    }
                },
                {
                    "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                    "repeatValue": {
                        "$numberInt": "2"
                    },
                    "steps": [
                        {
                            "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                            "repeatValue": {
                                "$numberInt": "8"
                            },
                            "steps": [
                                {
                                    "intensity": "INTERVAL",
                                    "targetType": "SPEED_LAP",
                                    "durationType": "TIME",
                                    "durationValue": {
                                        "$numberInt": "30"
                                    },
                                    "targetValue": "5"
                                },
                                {
                                    "intensity": "RECOVERY",
                                    "targetType": "OPEN",
                                    "durationType": "TIME",
                                    "durationValue": {
                                        "$numberInt": "30"
                                    }
                                }
                            ]
                        },
                        {
                            "intensity": "COOLDOWN",
                            "targetType": "OPEN",
                            "durationType": "TIME",
                            "durationValue": {
                                "$numberInt": "240"
                            }
                        }
                    ]
                },
                {
                    "intensity": "COOLDOWN",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "360"
                    }
                }
            ]
        },
        {
            "name": "Expert",
            "steps": [
                {
                    "intensity": "WARMUP",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "1800"
                    }
                },
                {
                    "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                    "repeatValue": {
                        "$numberInt": "2"
                    },
                    "steps": [
                        {
                            "repeatType": "REPEAT_UNTIL_STEPS_CMPLT",
                            "repeatValue": {
                                "$numberInt": "8"
                            },
                            "steps": [
                                {
                                    "intensity": "INTERVAL",
                                    "targetType": "SPEED_LAP",
                                    "durationType": "TIME",
                                    "durationValue": {
                                        "$numberInt": "30"
                                    },
                                    "targetValue": "5"
                                },
                                {
                                    "intensity": "RECOVERY",
                                    "targetType": "OPEN",
                                    "durationType": "TIME",
                                    "durationValue": {
                                        "$numberInt": "30"
                                    }
                                }
                            ]
                        },
                        {
                            "intensity": "COOLDOWN",
                            "targetType": "OPEN",
                            "durationType": "TIME",
                            "durationValue": {
                                "$numberInt": "240"
                            }
                        }
                    ]
                },
                {
                    "intensity": "COOLDOWN",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "360"
                    }
                }
            ]
        }
    ],
    "coach": 1
}
```

### Get a specific built session 

`GET /api-coach/built-session/<id>`

This endpoint is used to get a built session. You have to pass the id of the built session

```shell
curl --location --request GET 'https://dev.planif.fr/api-coach/built-session/2' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns the target built session in JSON structured like this:

```json
{
    "id": 2,
    "title": "A text session",
    "description": "Be ready to unleash your inner footbal",
    "sport": "CYCLING",
    "tags": [
        "Hard",
        "run",
        "yop"
    ],
    "steps": [
        {
            "intensity": "WARMUP",
            "targetType": "OPEN",
            "durationType": "TIME",
            "durationValue": {
                "$numberInt": "1200"
            }
        },
        {
            "steps": [
                {
                    "intensity": "INTERVAL",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "60"
                    }
                },
                {
                    "intensity": "INTERVAL",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "60"
                    }
                },
                {
                    "intensity": "INTERVAL",
                    "targetType": "OPEN",
                    "durationType": "DISTANCE",
                    "durationValue": {
                        "$numberInt": "12"
                    },
                    "durationValueType": "KM"
                },
                {
                    "intensity": "INTERVAL",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "10"
                    }
                }
            ],
            "repeatValue": {
                "$numberInt": "4"
            },
            "uuid-Comment": "a0612b3ef9024151b3947a5e6ac5da7b"
        },
        {
            "intensity": "COOLDOWN",
            "targetType": "OPEN",
            "durationType": "TIME",
            "durationValue": {
                "$numberInt": "600"
            }
        }
    ],
    "variants": "",
    "coach": 1
}
```

### Modify a built session

`PATCH /api-coach/built-session/<id>`

This endpoint is used to update a built session. You have to pass the id of the built session in the url and the data you want to modify as params. You can update partially the data.

```shell
curl --location --request PATCH 'https://dev.planif.fr/api-coach/built-session/2' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'tags="Hard, run, yop"'
```

> If successful the PATCH command returns the updated built session in JSON structured like this:

```json
{
    "id": 2,
    "title": "A text session",
    "description": "Be ready to unleash your inner footbal",
    "sport": "CYCLING",
    "tags": [
        "Hard",
        "run",
        "yop"
    ],
    "steps": [
        {
            "intensity": "WARMUP",
            "targetType": "OPEN",
            "durationType": "TIME",
            "durationValue": {
                "$numberInt": "1200"
            }
        },
        {
            "steps": [
                {
                    "intensity": "INTERVAL",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "60"
                    }
                },
                {
                    "intensity": "INTERVAL",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "60"
                    }
                },
                {
                    "intensity": "INTERVAL",
                    "targetType": "OPEN",
                    "durationType": "DISTANCE",
                    "durationValue": {
                        "$numberInt": "12"
                    },
                    "durationValueType": "KM"
                },
                {
                    "intensity": "INTERVAL",
                    "targetType": "OPEN",
                    "durationType": "TIME",
                    "durationValue": {
                        "$numberInt": "10"
                    }
                }
            ],
            "repeatValue": {
                "$numberInt": "4"
            },
            "uuid-Comment": "a0612b3ef9024151b3947a5e6ac5da7b"
        },
        {
            "intensity": "COOLDOWN",
            "targetType": "OPEN",
            "durationType": "TIME",
            "durationValue": {
                "$numberInt": "600"
            }
        }
    ],
    "variants": "",
    "coach": 1
}
```

### Delete a specific built session

`DELETE /api-coach/built-session/<id>`

This endpoint is used to delete a built session. You have to pass the id of the built session. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'https://dev.planif.fr/api-coach/built-session/2' \
--header 'Authorization: Bearer 23d8f0bed20b838474b782454f68ba4f1195b476'
```

## Tags

`reverse URL coach_rest:tag-coach`

Endpoint used to retrieve the tags of a coach, filtered or not, and create new ones.

Property | Description
--------- | -----------
id | The ID of the tag
metadata | text content of the tag (string)


```javascript
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 329,
        "metadata": "A nice tag !"
    }
]
```

This endpoint retrieves, creates ou deletes tags

### HTTP Request

`GET /api-coach/tag-coach/?metadata=`

Get all coach tags, if metadata parameter is set, filter the tags case-insensitive

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
metadata | False | use to filter the result (string)

### HTTP Request

`POST /api-coach/tag-coach/`

Creates a tag assigned to the logged coach

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
metadata | True | string


<aside class="success">
Remember — a happy coach is an authenticated coach!
</aside>

## Public profile Coach

Endpoint used to retrieve the public profile of a coach, and update it.

Property | Type | Description
--------- | ----------- | -----------
quote | String | Quote of the coach
bio | String | Bio of the coach
languages | Array of string, can only be inside LANGUAGE_CHOICES | Languages of the coach
sports | Array of string, can only be inside SPORT_CHOICES | Sports of the coach
is_public | Boolean, default False | Control wether the coach profile is public
is_public_email | Boolean, default True | Control wether the coach email is public
is_public_city | Boolean, default False | Control wether the coach address is public
is_public_phone | Boolean, default False | Control wether the coach phone is public
banner_id | String | id of the banner filepond object (don't update manually)
banner | String | url of the banner
pictures_id | Array of String | ids of the picture filepond objects (don't update manually)
pictures | Array of String | urls of the pictures

LANGUAGE_CHOICES = [
    "FR",
    "EN",
    "DE",
    "ES",
    "IT"
]

SPORT_CHOICES = [
   "OTHER",
    "RUNNING",
    "CYCLING",
    "TRANSITION",
    "FITNESS_EQUIPMENT",
    "SWIMMING",
    "BASKETBALL",
    "SOCCER",
    "TENNIS",
    "AMERICAN_FOOTBALL",
    "TRAINING",
    "WALKING",
    "CROSS_COUNTRY_SKIING",
    "ALPINE_SKIING",
    "SNOWBOARDING",
    "ROWING",
    "MOUNTAIN_EQUIPMENT",
    "HIKING",
    "MULTISPORT",
    "PADDING",
    "FLYING",
    "E_BIKING",
    "MOTORCYCLING",
    "BOATING",
    "DRIVING",
    "GOLF",
    "HANG_GLIDING",
    "HORSEBACK_RIDING",
    "HUNTING",
    "FISHING",
    "INLINE_SKATING",
    "ROCK_CLIMBING",
    "SAILING",
    "ICE_SKATING",
    "SKY_DIVING",
    "SNOWSHOEING",
    "SNOWMOBILING",
    "STAND_UP_PADDLEBOARDING",
    "SURFING",
    "WAKEBOARDING",
    "WATER_SKIING",
    "KAYAKING",
    "RAFTING",
    "WINDSURFING",
    "KITE_SURFING",
    "TACTICAL",
    "JUMP_MASTER",
    "BOXING",
    "FLOOR_CLIMBING",
    "DIVING",
]

```javascript
```

> The above command returns JSON structured like this:

```json
{
    "coach": 8,
    "languages": [
        "FR",
        "DE"
    ],
    "sports": [
        "RUNNING",
        "MULTISPORT"
    ],
    "is_public": true,
    "quote": "A new qute",
    "bio": "Yayyyyy",
    "is_public_email": true,
    "is_public_city": false,
    "is_public_phone": true,
    "banner": "http://localhost:8000/mediafiles/media/8/public_profile/Santa Claus.H16.2k.png",
    "banner_id": "J6PC2YRnApK7uXFMoKHubq",
    "pictures": [
        "http://localhost:8000/mediafiles/media/8/public_profile/Directing the arrow up-rafiki.png",
        "http://localhost:8000/mediafiles/media/8/public_profile/Fans-amico.png"
    ],
    "pictures_id": [
        "nChUoyH268mSy22rFQ6LLS",
        "5HkbFDhfUsFBbUy4nZ5xZP"
    ]
}
```

### GET public profile

`GET /api-coach/public-profile/`

Get public profile

```shell
curl --location --request PUT 'http://localhost:8000/api-coach/public-profile/' \
--header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjU0Njg0OTMxLCJpYXQiOjE2NTQ2ODEzMzEsImp0aSI6ImQxN2VjYmJkMjNhZDQ3ZWZhNGE4OTIyNTM0Zjc0YzY4IiwidXNlcl9pZCI6OH0.kDTsRRCu6Z1qN_rZB9hWfgLxFfbx5EvVzx6XbWX444o' \
--header 'Content-Type: application/json' \
--data-raw '{
    "quote":"A new qute",
    "bio":"Yayyyyy",
    "is_public": true,
    "is_public_email": true,
    "is_public_city": false,
    "is_public_phone":true,
    "languages" : [
        "FR",
        "DE"
    ],
    "sports" : [
        "RUNNING",
        "MULTISPORT"
    ]
}'
```

### PUT public profile

`PUT /api-coach/public-profile/`

Modify the public profile

<aside class="success">
Remember — a happy coach is an authenticated coach!
</aside>


# Athlete REST API

<aside class="notice">For all the next endpoints, you will need to be authenticated as a Athlete and sending request containing a Bearer with such headers <code>Authorization: Bearer <your_token></code>.</aside>

## Activities

`GET /api-athlete/activity/?limit={limit}&page={page}`

Retrieve all the activity of an athlete with pagination. Order by start_time desc

`GET /api-athlete/activity-month/?month={month}&year={year}`

Retrieve activities for an athlete by month and year

> Example activities list

```json
[
    {
        "id": "c427ac5e-3ee6-45f3-bfaa-36afbc004319",
        "name": "Footing a jeun",
        "sport": "RUNNING",
        "start_time": "2022-05-24T05:53:41Z",
        "notes": "",
        "private": true,
        "has_file": true,
        "stats": {
            "activity": "c427ac5e-3ee6-45f3-bfaa-36afbc004319",
            "distance": "6228.63",
            "timer_time": 1688,
            "elapsed_time": 1688,
            "moving_time": 1688,
            "energy": 324,
            "avg_speed": "3.56",
            "max_speed": "5.08",
            "max_elevation": 483,
            "min_elevation": 437,
            "gain_elevation": 118,
            "loss_elevation": 120,
            "avg_hr": "161.3",
            "max_hr": 176,
            "avg_cadence": "85.3",
            "max_cadence": 100,
            "strides": "1.30",
            "avg_temp": null,
            "max_temp": null,
            "min_temp": null,
            "avg_power": null,
            "max_power": null
        }
    }
]
```

`GET /api-athlete/activity/{id}`

Retrieve an activity of an athlete with the id of the activity.

> Example activity object 

```json
{
    "id": "c427ac5e-3ee6-45f3-bfaa-36afbc004319",
    "name": "Footing a jeun",
    "sport": "RUNNING",
    "start_time": "2022-05-24T05:53:41Z",
    "notes": "",
    "private": true,
    "has_file": true,
    "stats": {
        "activity": "c427ac5e-3ee6-45f3-bfaa-36afbc004319",
        "distance": "6228.63",
        "timer_time": 1688,
        "elapsed_time": 1688,
        "moving_time": 1688,
        "energy": 324,
        "avg_speed": "3.56",
        "max_speed": "5.08",
        "max_elevation": 483,
        "min_elevation": 437,
        "gain_elevation": 118,
        "loss_elevation": 120,
        "avg_hr": "161.3",
        "max_hr": 176,
        "avg_cadence": "85.3",
        "max_cadence": 100,
        "strides": "1.30",
        "avg_temp": null,
        "max_temp": null,
        "min_temp": null,
        "avg_power": null,
        "max_power": null
    },
    "laps": [
        {
            "timestamp": "2022-05-24T06:21:49",
            "start_time": "2022-05-24T05:53:41",
            "total_elapsed_time": 1688.795,
            "total_timer_time": 1688.795,
            "total_distance": 6228.63,
            "total_moving_time": 1688.795,
            "time_in_hr_zone": [
                0,
                0,
                0,
                0,
                1547.152
            ],
            "total_calories": 324,
            "enhanced_avg_speed": 3.688,
            "avg_speed": 3.688,
            "enhanced_max_speed": 5.083,
            "max_speed": 5.083,
            "total_ascent": 118,
            "total_descent": 119,
            "enhanced_avg_altitude": 463.20000000000005,
            "avg_altitude": 463.20000000000005,
            "enhanced_max_altitude": 483.79999999999995,
            "max_altitude": 483.79999999999995,
            "avg_grade": 0.32,
            "max_pos_grade": 17.7,
            "max_neg_grade": -10.65,
            "enhanced_min_altitude": 437.4,
            "min_altitude": 437.4,
            "avg_vertical_oscillation": 0,
            "avg_stance_time": 0,
            "event": "lap",
            "event_type": "stop",
            "avg_heart_rate": 157,
            "max_heart_rate": 176,
            "avg_running_cadence": 85,
            "max_running_cadence": 100,
            "lap_trigger": "session_end",
            "sport": "running",
            "sub_sport": "generic",
            "min_heart_rate": 118
        }
    ],
    "points_as_features": [
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    10.074628433212638,
                    48.83592551574111
                ]
            },
            "properties": {
                "time": 563
            }
        }
    ],
    "points_as_line": [
        [
            10.074469428509474,
            48.83623388595879
        ],
    ],
    "records": [
        {
            "duration": 0,
            "position_lat": 582638965,
            "position_long": 120193102,
            "distance": 0,
            "calories": 0,
            "battery_soc": 82,
            "lon_gps": 120193000,
            "lat_gps": 582638921,
            "enhanced_altitude": null,
            "altitude": null,
            "enhanced_speed": null,
            "speed": null,
            "grade": null,
            "vertical_speed": null,
            "heart_rate": null,
            "cadence": null,
            "gps_accuracy": null,
            "ascent": null
        },
    ]
}
```

`PATCH /api-athlete/activity/{id}`

Modify an activity of an athlete with the id of the activity.

`DELETE /api-athlete/activity/{id}`

Delete an activity of an athlete with the id of the activity.

## Statistics

`GET /api-athlete/stats-activity/?start_date={start_date}&end_date={end_date}`

Get all the statistics for a given duration

> Example stastitics object

```json
{
    "total": {
        "count": 1,
        "distance": 6228.63,
        "duration": 1688,
        "calories": 324
    },
    "by_sport": [
        {
            "sport": "RUNNING",
            "count": 1,
            "distance": 6228.63,
            "duration": 1688,
            "calories": 324
        }
    ],
    "by_sport_interval": [
        {
            "sport": "RUNNING",
            "day": "2022-05-24T00:00:00Z",
            "count": 1,
            "duration": 1688
        }
    ],
    "by_sport_previous": [],
    "total_previous": {
        "count": 0,
        "duration": null
    }
}
```

## Training Planned

`GET /api-athlete/training-planned/?start_date={start_date}&end_date={end_date}`

Get all the training planned of an athlete for the given date interval.

## Training Plan Rating

`reverse URL athlete_rest:rate-plan-athlete`
`reverse URL athlete_rest:rate-plan-athlete-obj`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the training plan rating  | Integer
rate | Rating of the training plan (must be between 1 to 5)  | Integer
text | Optional text of the rating  | String
training_plan | Id of the concerned training  | Integer
athlete | Id of the athlete giving the rating  | Integer

  
<aside class="notice">Careful, there can be only one rating per couple athlete - training plan</aside>

```shell
curl --location --request GET 'https://dev.planif.fr/api-athlete/rate-plan/' \
--header 'Authorization: Bearer 7c9aa8c2e995a233520e223d95a584e77636c057'
```

> The GET command returns a list of ratings as JSON structured like this:

```json
[
    {
        "id": 3,
        "rate": 5,
        "text": "A great plan 2",
        "training_plan": 2,
        "athlete": 2
    },
    {
        "id": 1,
        "rate": 4,
        "text": "Not so good",
        "training_plan": 1,
        "athlete": 2
    }
]
```

### Get all ratings for the athlete

`GET /api-athlete/rate-plan/`

This endpoint retrieves all the athlete ratings.

### Create a rating

`POST /api-athlete/rate-plan/`

This endpoint is used to create a rating for a specific training plan. You have to pass at the minimum the id of the plan and the rate to create a rating.

```shell
curl --location --request POST 'https://dev.planif.fr/api-athlete/rate-plan/' \
--header 'Authorization: Bearer 7c9aa8c2e995a233520e223d95a584e77636c057' \
--form 'training_plan="2"' \
--form 'rate="5"' \
--form 'text="A great plan 2"'
```

> The POST command returns the created rating in JSON structured like this:

```json
{
    "id": 1,
    "rate": 5,
    "text": "A great plan 2",
    "training_plan": 2,
    "athlete": 2
}
```

### Get a specific rating 

`GET /api-athlete/rate-plan/<id>`

This endpoint is used to get an athlete specific rating. You have to pass the id of the rating

```shell
curl --location --request GET 'https://dev.planif.fr/api-athlete/rate-plan/1' \
--header 'Authorization: Bearer 7c9aa8c2e995a233520e223d95a584e77636c057'
```

> The GET command returns the target rating in JSON structured like this:

```json
{
    "id": 1,
    "rate": 4,
    "text": "Not so good",
    "training_plan": 1,
    "athlete": 2
}
```

### Modify a rating

`PATCH /api-athlete/rate-plan/<id>`

This endpoint is used to update an athlete rating. You have to pass the id of the rating in the url and the data you want to modify as params. 

You can update partially the data. 

```shell
curl --location --request PATCH 'https://dev.planif.fr/api-athlete/rate-plan/1' \
--header 'Authorization: Bearer 7c9aa8c2e995a233520e223d95a584e77636c057' \
--form 'text="New text rating"'
```

> If successful the PATCH command returns the updated rating in JSON structured like this:

```json
{
    "id": 1,
    "rate": 4,
    "text": "New text rating",
    "training_plan": 1,
    "athlete": 2
}
```

### Delete a specific rating

`DELETE /api-athlete/rate-plan/<id>`

This endpoint is used to delete an athlete rating. You have to pass the id of the rating. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'https://dev.planif.fr/api-athlete/rate-plan/2' \
--header 'Authorization: Bearer 7c9aa8c2e995a233520e223d95a584e77636c057'
```

# Club REST API

<aside class="notice">For all the next endpoints, you will need to be authenticated as a Club and sending request containing a Token with such headers <code>Authorization: Bearer <your_token></code>.</aside>

## Public profile Club

Endpoint used to retrieve the public profile of a club, and update it.

Property | Type | Description
--------- | ----------- | -----------
bio | String | Bio of the club
languages | Array of string, can only be inside LANGUAGE_CHOICES | Languages of the club
sports | Array of string, can only be inside SPORT_CHOICES | Sports of the club
is_public | Boolean, default False | Control wether the club profile is public
is_public_email | Boolean, default True | Control wether the club email is public
is_public_city | Boolean, default False | Control wether the club address is public
is_public_phone | Boolean, default False | Control wether the club phone is public
banner_id | String | id of the banner filepond object (don't update manually)
banner | String | url of the banner
pictures_id | Array of String | ids of the picture filepond objects (don't update manually)
pictures | Array of String | urls of the pictures

LANGUAGE_CHOICES = [
    "FR",
    "EN",
    "DE",
    "ES",
    "IT"
]

SPORT_CHOICES = [
   "OTHER",
    "RUNNING",
    "CYCLING",
    "TRANSITION",
    "FITNESS_EQUIPMENT",
    "SWIMMING",
    "BASKETBALL",
    "SOCCER",
    "TENNIS",
    "AMERICAN_FOOTBALL",
    "TRAINING",
    "WALKING",
    "CROSS_COUNTRY_SKIING",
    "ALPINE_SKIING",
    "SNOWBOARDING",
    "ROWING",
    "MOUNTAIN_EQUIPMENT",
    "HIKING",
    "MULTISPORT",
    "PADDING",
    "FLYING",
    "E_BIKING",
    "MOTORCYCLING",
    "BOATING",
    "DRIVING",
    "GOLF",
    "HANG_GLIDING",
    "HORSEBACK_RIDING",
    "HUNTING",
    "FISHING",
    "INLINE_SKATING",
    "ROCK_CLIMBING",
    "SAILING",
    "ICE_SKATING",
    "SKY_DIVING",
    "SNOWSHOEING",
    "SNOWMOBILING",
    "STAND_UP_PADDLEBOARDING",
    "SURFING",
    "WAKEBOARDING",
    "WATER_SKIING",
    "KAYAKING",
    "RAFTING",
    "WINDSURFING",
    "KITE_SURFING",
    "TACTICAL",
    "JUMP_MASTER",
    "BOXING",
    "FLOOR_CLIMBING",
    "DIVING",
]

```javascript
```

> The above command returns JSON structured like this:

```json
{
    "club": 13,
    "languages": [
        "FR",
        "DE"
    ],
    "sports": [
        "RUNNING",
        "MULTISPORT"
    ],
    "is_public": true,
    "bio": "Yayyyyy",
    "is_public_email": true,
    "is_public_city": false,
    "is_public_phone": true,
    "banner": null,
    "banner_id": null,
    "pictures": [],
    "pictures_id": []
}
```

### GET public profile

`GET /api-club/public-profile/`

Get public profile

```shell
curl --location --request PUT 'http://localhost:8000/api-club/public-profile/' \
--header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjU0ODEwNDg4LCJpYXQiOjE2NTQ4MDY4ODgsImp0aSI6ImFhZjE4YmYyYzdiYjQ5MDE5MWQwZWFlMzQ5YzUzYjNkIiwidXNlcl9pZCI6MTN9.XcAQWfoxdgYT2Pk256oz1tmuUmuHKspQGPK0XY-E_VI' \
--header 'Content-Type: application/json' \
--data-raw '{
    "bio":"Yayyyyy",
    "is_public": true,
    "is_public_email": true,
    "is_public_city": false,
    "is_public_phone":true,
    "languages" : [
        "FR",
        "DE"
    ],
    "sports" : [
        "RUNNING",
        "MULTISPORT"
    ]
}'
```

### PUT public profile

`PUT /api-club/public-profile/`

Modify the public profile

<aside class="success">
Remember — a happy club is an authenticated club!
</aside>




<!-- 

TEMPLATE

## NAME_ENDPOINT

`reverse URL namespace:name`

Endpoint_description

Property | Description
--------- | -----------
id | The ID of the tag
metadata | text content of the tag (string)


```javascript
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 329,
        "metadata": "A nice tag !"
    }
]
```

### HTTP Request

`GET /api-coach/tag-coach/?metadata=`

Request_description

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
metadata | False | use to filter the result (string)

 -->