---
title: API Reference

# language_tabs: # must be one of https://git.io/vQNgJ
#   - shell
#   - ruby
#   - python
#   - javascript

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


<!-- # Plan -->

# Coach

<aside class="notice">For all the next endpoints, you will need to be authenticated as a Coach and sending a CRSF Token containing a <code>Coach</code> instance.</aside>

## Athletes

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

This endpoint retrieves or delete a coach profile.

### HTTP Request

`GET /api/athletes/`

## Text Session

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

`GET /api/sessions-text/`

Retrieves all the text sessions of the coach

### HTTP Request

`GET /api/sessions-text/<id>`
`DELETE /api/sessions-text/<id>`

Retrieves or deletes a the text session

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | ID of the text session

### HTTP Request

`POST /api/sessions-text/`

Creates a the text session

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

## Profile

Property | Description
--------- | -----------
coach_id | The ID of the coach
first_name | (string)
last_name | (string)
profile_picture | upload_id of the profile picture created by filepond_drf, null if no profile picture (string)


```javascript
```

> The above command returns JSON structured like this:

```json
{
    "first_name": "Lucas",
    "last_name": "Damalix",
    "profile_picture": "4hK2NvuZJD34oWmvnBSeKo"
}
```

This endpoint retrieves or delete a coach profile.

### HTTP Request

`GET /api/profile-coach/<id>`
`DELETE /api/profile-coach/<id>`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | ID of the coach

### HTTP Request

`PUT /api/profile-coach/<id>`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | ID of the coach
first_name | False | (string)
last_name | False | (string)
profile_picture | False | upload_id of the profile picture created by filepond_drf, null if no profile picture (string)

## Profile picture

HTTP Code | Meaning
---------- | -------
201 | Created -- Your picture has been successfully uploaded.
204 | No content -- Your picture has been delete.
400 | Bad request -- Bad format or type error.
404 | Not Found -- Your temporary picture or uploaded could not be found.


```javascript
```

### HTTP Request

`POST /api/profile_picture/`
`DELETE /api/profile_picture/`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | True | upload_id assigned by filepond_drf


## Tags

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

`GET /api/tag-coach/`

Get all coach tags, if metadata parameter is set, filter the tags case-insensitive

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
metadata | False | usr to filter the result (string)

### HTTP Request

`POST /api/tag-coach/`

Creates a tag assigned to the logged coach

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
metadata | True | string


<aside class="success">
Remember — a happy coach is an authenticated coach!
</aside>


