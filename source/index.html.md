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

Here is an example of a built session object with Planif session builder. This examples contains 3 differents variants of the session.

Property | Description
--------- | -----------
_id | The ID of the session (ObjectId)
sport | instance of sport of the session (string)
title | title of the session (string)
description | description of the session (string)
steps | list of steps of the session, null if variants(Array of steps)
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

## Text & Image session

Text and image session object

Property | Description
--------- | -----------
id | The ID of the session (int)
coach | Coach creator ID (int or Coach model instance)
title | title of the session (string)
description | description of the session (string)
session | content of the session produced by timyMce (html string)



## Session builder


<!-- # Plan -->

