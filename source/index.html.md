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
	"https://dev.planif.fr/api-shared/profile-coach/"
```

> The above command returns JSON structured like this:

```json
{
"first_name": "John",
"last_name": "Doe",
"birth_date": "12/28/1998",
"height": {
  "unit": "m",
  "value": 2
},
"weight": {
  "unit": "g",
  "value": 90718.4
},
"phone_number": "+33751515151",
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
	-H "Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476" \
	-H "Content-Type: application/x-www-form-urlencoded; charset=utf-8" \
	-d "address=12%20Jean%20Jaures%2C%2038000%20Grenoble&height_unit=cm&height_value=200&phone_number=%2B33751515151" \
	"https://dev.planif.fr/api-shared/profile-coach/"
```

> The above command returns the updated profile in JSON structured like this:

```json
{
"first_name": "Jack",
"last_name": "Deen",
"birth_date": "12/28/1998",
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

<aside class="notice">For all the next endpoints, you will need to be authenticated as a Coach and sending request containing a Token with such headers <code>Authorization: Token <your_token></code>.</aside>

## Plan

`reverse URL coach_rest:plan-coach`
`reverse URL coach_rest:plan-coach-obj`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the plan  | Integer
coach | Id of the coach, owner of the plan  | Integer
name | Name of the plan  | String
description | Description of the plan (optional)  | String
is_public | True if the plan is public, false otherwise  | Boolean
is_static | True if the plan is static, false otherwise  | Boolean
duration | Duration of a static plan in week, available only if the plan is static  | Integer
price | Price of a public plan in Eur, available only if the plan is public  | Integer

```shell
curl --location --request GET 'http://localhost:8000/api-coach/plan/' \
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns a list of plans as JSON structured like this:

```json
[
    {
        "id": 15,
        "name": "My insane plan",
        "coach": 1,
        "description": null,
        "duration": 12,
        "is_public": false,
        "is_static": true
    },
    {
        "id": 16,
        "name": "My insane plan",
        "coach": 1,
        "description": "Be ready to become fiiiiit AF",
        "duration": 2,
        "price": "123.32",
        "is_public": true,
        "is_static": true
    },
    {
        "id": 4,
        "name": "A nice plan",
        "coach": 1,
        "description": "Great for beginners",
        "is_public": false,
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
curl --location --request POST 'http://localhost:8000/api-coach/plan/' \
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476' \
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
    "price": "123.32",
    "is_public": true,
    "is_static": true
}
```

### Get a specific plan 

`GET /api-coach/plan/<id>`

This endpoint is used to get a coach specific plan. You have to pass the id of the plan

```shell
curl --location --request GET 'http://localhost:8000/api-coach/plan/4' \
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476'
```

> The GET command returns the target plan in JSON structured like this:

```json
{
    "id": 4,
    "name": "Nice plan",
    "coach": 1,
    "description": "Excellent",
    "is_public": false,
    "is_static": false
}
```

### Modify a plan

`PATCH /api-coach/plan/<id>`

This endpoint is used to update a coach training plan. You have to pass the id of the plan in the url and the data you want to modify as params. 

You can update partially the data. 

To make the plan static simply pass the duration, to make it dynamic, pass an empty duration. Same goes for the is_public attribute : to make the plan public, pass a price, to make it private pass an empty price. 

```shell
curl --location --request PATCH 'http://localhost:8000/api-coach/plan/4' \
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476' \
--form 'price=""'
```

> If successful the PATCH command returns the updated plan in JSON structured like this:

```json
{
    "id": 4,
    "name": "Nice plan",
    "coach": 1,
    "description": "Excellent",
    "is_public": false,
    "is_static": false
}
```

### Delete a specific plan

`DELETE /api-coach/plan/<id>`

This endpoint is used to delete a coach training plan. You have to pass the id of the plan. If successful the request will return a 204 No content

```shell
curl --location --request DELETE 'http://localhost:8000/api-coach/plan/3' \
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476'
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
	-H "Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476" \
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
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476' \
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
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476'
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
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476' \
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
--header 'Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476'
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
	-H "Authorization: Token 23d8f0bed20b838474b782454f68ba4f1195b476" \
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57' \
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57'
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57' \
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57'
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57'
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57' \
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57'
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57' \
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
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57'
```

## Hashtag

`reverse URL coach_rest:hashtag-coach`
`reverse URL coach_rest:hashtag-coach-obj`

Property | Description | Type
--------- | ----------- | -----------
id | Id of the hashtag  | Integer
name | Name of the hashtag  | String

```shell
curl --location --request GET 'http://localhost:8000/api-coach/hashtag/' \
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57'
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
curl --location --request POST 'http://localhost:8000/api-coach/hashtag/' \
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57' \
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
curl --location --request GET 'http://localhost:8000/api-coach/hashtag/1' \
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57'
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
curl --location --request PATCH 'http://localhost:8000/api-coach/hashtag/1' \
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57' \
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
curl --location --request DELETE 'http://localhost:8000/api-coach/hashtag/2' \
--header 'Authorization: Token a7816be6d761730bbca7b3de33d7b76467786b57'
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