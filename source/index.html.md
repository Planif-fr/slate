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

Base url : `http://localhost:8000/`

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
Authorization: Token <your_token>
```

```shell
curl -v \
	-H "Authorization: Token <your_token>"
```

To access all ressources that need authentification, you need to pass an authorization header.

This header is composed of a token associated with each user. You first need to retrieve the token. To do so, you must send a POST request to the login endpoint

## Login endpoint

```shell
curl -v \
	-X POST \
	-d "password=password&username=username" \
	"http://localhost:8000/api-shared/api-token-auth/"
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



## Session builder

<!-- ****** -->
<!-- SHARED -->
<!-- ****** -->

# Shared REST API

## Profile

`reverse URL shared_rest:profile-coach`

Property | Description | Type
--------- | ----------- | -----------
first_name | First name  | String
last_name | Last name  | String
birth_date | Birth date in a MM/DD/YYYY format  | String
phone_number | Full phone number with the country code prepended  | String
height | Height in meters | Float
weight | Weight in grams | Float
address | Full address | String
profile_picture | Relative url of the profile picture, or the default picture if none. It is relative to the base url | String

```shell
curl -v \
	-X GET \
	-H "Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476" \
	"http://localhost:8000/api-shared/profile-coach/?password=6673boss&username=coach"
```

> The above command returns JSON structured like this:

```json
{
"first_name": "John",
"last_name": "Doe",
"birth_date": "12/28/1998",
"phone_number": "+33123456789",
"height": 1.8,
"weight": 75000,
"address": "17 Chemin de la Capuche, Grenoble, France",
"profile_picture": "/mediafiles/1/4ujo5kXS4AjWufTY88YdgV/43336475_054_ea9e.jpg"
}
```

### HTTP Request

`GET /api-shared/profile-coach/`

This endpoint retrieves the coach profile.

### HTTP Request

`PUT /api-shared/profile-coach/`

This endpoint update the coach profile.

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | ID of the profile
first_name | False | (string)
last_name | False | (string)
profile_picture | False | upload_id of the profile picture created by filepond_drf, null if no profile picture (string)



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

<aside class="notice">For all the next endpoints, you will need to be authenticated as a Coach and sending a CRSF Token containing a <code>Coach</code> instance.</aside>

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

`reverse URL coach_rest:sessions-text`

Property | Description
--------- | -----------
id | The ID of the text session
coach | The ID of the coach who created the session
title | (string)
description | (string)
tags | array of tags (Array of string)
session | HTML markup coming from tinyMce (string)


```javascript
```

> The above command returns JSON structured like this:

```json
    {
        "id": 8,
        "title": "Jogging",
        "description": "A simple workout",
        "tags": [
            "easy",
            "run",
            "jogging"
        ],
        "session": "<p>1 hour easy jogging</p>",
        "coach": 4
    }
```


### HTTP Request

`GET /api-coach/sessions-text/`

Retrieve all the text sessions of the coach

### HTTP Request

`GET /api-coach/sessions-text/<id>`

Retrieve the text session

`DELETE /api-coach/sessions-text/<id>`

Delete the text session

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | ID of the text session

### HTTP Request

`POST /api/sessions-text/`

Create a the text session

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
title | True | (string)
description | False | (string)
tags | False | array of tags (Array of string)
session | True | HTML markup coming from tinyMce (string)

### HTTP Request

`POST /api/sessions-text/<id>`

Updates a the text session

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
title | True | (string)
description | False | (string)
tags | False | array of tags (Array of string)
session | True | HTML markup coming from tinyMce (string)


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