# Example API
A schema for a small example API.

* [App](#app)
 * [POST /apps](#post-apps)
 * [DELETE /apps/:id](#delete-appsid)
 * [GET /apps/:id](#get-appsid)
 * [GET /apps](#get-apps)
 * [PATCH /apps/:id](#patch-appsid)
* [Recipe](#recipe)
 * [GET /recipes](#get-recipes)
* [User](#user)

## App
An app is a program to be deployed.

### Properties
* id
 * unique identifier of app
 * Example: `"01234567-89ab-cdef-0123-456789abcdef"`
 * Type: string
 * Format: uuid
 * ReadOnly: true
* name
 * unique name of app
 * Example: `"example"`
 * Type: string
 * Patern: `(?-mix:^[a-z][a-z0-9-]{3,50}$)`
* private
 * true if this resource is private use
 * Example: `false`
 * Type: boolean
* deleted_at
 * When this resource was deleted at
 * Example: `nil`
 * Type: null
* user_ids
 * Type: array
* users
 * Type: array

### POST /apps
Create a new app.

```
POST /apps HTTP/1.1
Content-Type: application/json
Host: api.example.com

{
  "name": "example"
}
```

```
HTTP/1.1 201
Content-Type: application/json

{
  "id": "01234567-89ab-cdef-0123-456789abcdef",
  "name": "example",
  "private": false,
  "deleted_at": null,
  "user_ids": [
    1
  ],
  "users": [
    {
      "name": "alice"
    }
  ]
}
```

### DELETE /apps/:id
Delete an existing app.

```
DELETE /apps/:id HTTP/1.1
Host: api.example.com
```

```
HTTP/1.1 200
Content-Type: application/json

{
  "id": "01234567-89ab-cdef-0123-456789abcdef",
  "name": "example",
  "private": false,
  "deleted_at": null,
  "user_ids": [
    1
  ],
  "users": [
    {
      "name": "alice"
    }
  ]
}
```

### GET /apps/:id
Info for existing app.

```
GET /apps/:id HTTP/1.1
Host: api.example.com
```

```
HTTP/1.1 200
Content-Type: application/json

{
  "id": "01234567-89ab-cdef-0123-456789abcdef",
  "name": "example",
  "private": false,
  "deleted_at": null,
  "user_ids": [
    1
  ],
  "users": [
    {
      "name": "alice"
    }
  ]
}
```

### GET /apps
List existing apps.

```
GET /apps HTTP/1.1
Host: api.example.com
```

```
HTTP/1.1 200
Content-Type: application/json

[
  {
    "id": "01234567-89ab-cdef-0123-456789abcdef",
    "name": "example",
    "private": false,
    "deleted_at": null,
    "user_ids": [
      1
    ],
    "users": [
      {
        "name": "alice"
      }
    ]
  }
]
```

### PATCH /apps/:id
Update an existing app.

```
PATCH /apps/:id HTTP/1.1
Content-Type: application/json
Host: api.example.com

{
  "name": "example"
}
```

```
HTTP/1.1 200
Content-Type: application/json

{
  "id": "01234567-89ab-cdef-0123-456789abcdef",
  "name": "example",
  "private": false,
  "deleted_at": null,
  "user_ids": [
    1
  ],
  "users": [
    {
      "name": "alice"
    }
  ]
}
```

## Recipe


### Properties
* name
 * Example: `"Sushi"`
* user
 * Type: object
 * name
  * Example: `"alice"`
  * Type: string

### GET /recipes
List recipes

```
GET /recipes HTTP/1.1
Host: api.example.com
```

```
HTTP/1.1 200
Content-Type: application/json

[
  {
    "name": "Sushi",
    "user": {
      "name": "alice"
    }
  }
]
```

## User


### Properties
* name
 * Example: `"alice"`
 * Type: string

