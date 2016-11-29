---
title: Ubersidad API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction

Welcome to the [Ubersidad](https://ubersidad.herokuapp.com) API! You can use our API to access Ubersidad API endpoints, which can get information on various Unversidad Católica campuses, user routes, user trips, and system-generated user notifications in our database.

# Authentication

Ubersidad uses token authentication to allow access to some parts of the API (some parts are publicly available). A token is created by the following request:


### HTTP Request

`POST http://ubersidad.herokuapp.com/api/v1/user/token`

### Query Parameters

Parameter | Description
--------- | -----------
email | Email address associated with the user's Ubersidad account
password | Password associated with the user's Ubersidad account

> The HTTP Request returns JSON structured like this:

```json
{
  "token": "bd2310d4af2f21f5fc684491c78c56891dc6ef84def6e59bb433bb49dc5fbb14201daaf374aaa1b57d85e2565348266e4165eeeac154d2617932301b74c6d3ff"
}
```

Ubersidad expects the token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token=mytoken`

<aside class="notice">
You must replace <code>mytoken</code> with your personal token which you can obtain using the request above.
</aside>

# Campuses

## Get All Campuses

> The HTTP Request returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "campuses",
      "attributes": {
        "name": "Campus San Joaquín",
        "abbreviation": "CSJ"
      },
      "relationships": {
        "location": {
          "data": {
            "id": "1",
            "type": "locations"
          }
        }
      }
    },
    {
      "id": "2",
      "type": "campuses",
      "attributes": {
        "name": "Casa Central",
        "abbreviation": "CC"
      },
      "relationships": {
        "location": {
          "data": {
            "id": "2",
            "type": "locations"
          }
        }
      }
    }
  ],
  "included": [
    {
      "id": "1",
      "type": "locations",
      "attributes": {
        "latitude": -33.498022,
        "longitude": -70.615558
      }
    },
    {
      "id": "2",
      "type": "locations",
      "attributes": {
        "latitude": -33.44017,
        "longitude": -70.640731
      }
    }
  ]
}
```

This endpoint retrieves all campuses.
No authentication is required for this endpoint.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/campuses`

## Get a Specific Campus

> The HTTP Request returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "campuses",
    "attributes": {
      "name": "Campus San Joaquín",
      "abbreviation": "CSJ"
    },
    "relationships": {
      "location": {
        "data": {
          "id": "1",
          "type": "locations"
        }
      }
    }
  },
  "included": [
    {
      "id": "1",
      "type": "locations",
      "attributes": {
        "latitude": -33.498022,
        "longitude": -70.615558
      }
    }
  ]
}
```

This endpoint retrieves a specific campus.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/campuses/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the campus to retrieve


# Routes

## Get All Routes

> The HTTP Request returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "routes",
      "relationships": {
        "routes-locations": {
          "data": [
            {
              "id": "1",
              "type": "routes-locations"
            },
            {
              "id": "2",
              "type": "routes-locations"
            }
          ]
        }
      }
    },
    {
      "id": "2",
      "type": "routes",
      "relationships": {
        "routes-locations": {
          "data": [
            {
              "id": "3",
              "type": "routes-locations"
            },
            {
              "id": "4",
              "type": "routes-locations"
            },
            {
              "id": "5",
              "type": "routes-locations"
            },
            {
              "id": "6",
              "type": "routes-locations"
            }
          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "1",
      "type": "routes-locations",
      "attributes": {
        "order": 0,
        "latitude": -33.4545956,
        "longitude": -70.5828137
      }
    },
    {
      "id": "2",
      "type": "routes-locations",
      "attributes": {
        "order": 1,
        "latitude": -33.498022,
        "longitude": -70.615558
      }
    },
    {
      "id": "3",
      "type": "routes-locations",
      "attributes": {
        "order": 0,
        "latitude": -33.4187045,
        "longitude": -70.7919329
      }
    },
    {
      "id": "4",
      "type": "routes-locations",
      "attributes": {
        "order": 1,
        "latitude": -33.4418429,
        "longitude": -70.7397292
      }
    },
    {
      "id": "5",
      "type": "routes-locations",
      "attributes": {
        "order": 2,
        "latitude": -33.4053455,
        "longitude": -70.6512486
      }
    },
    {
      "id": "6",
      "type": "routes-locations",
      "attributes": {
        "order": 3,
        "latitude": -33.446673,
        "longitude": -70.594365
      }
    }
  ]
}
```

This endpoint retrieves all routes.
No authentication is required for this endpoint as routes are not associated with the driver or the passengers.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/routes`

## Get a Specific Route

> The HTTP Request returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "routes",
    "relationships": {
      "routes-locations": {
        "data": [
          {
            "id": "3",
            "type": "routes-locations"
          },
          {
            "id": "4",
            "type": "routes-locations"
          },
          {
            "id": "5",
            "type": "routes-locations"
          },
          {
            "id": "6",
            "type": "routes-locations"
          }
        ]
      }
    }
  },
  "included": [
    {
      "id": "3",
      "type": "routes-locations",
      "attributes": {
        "order": 0,
        "latitude": -33.4187045,
        "longitude": -70.7919329
      }
    },
    {
      "id": "4",
      "type": "routes-locations",
      "attributes": {
        "order": 1,
        "latitude": -33.4418429,
        "longitude": -70.7397292
      }
    },
    {
      "id": "5",
      "type": "routes-locations",
      "attributes": {
        "order": 2,
        "latitude": -33.4053455,
        "longitude": -70.6512486
      }
    },
    {
      "id": "6",
      "type": "routes-locations",
      "attributes": {
        "order": 3,
        "latitude": -33.446673,
        "longitude": -70.594365
      }
    }
  ]
}
```

This endpoint retrieves a specific route.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/routes/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the route to retrieve


# Notifications

## Get All Notifications for a User

> The HTTP Request returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "notifies",
      "attributes": {
        "timestamp": "2016-11-28T18:21:05.899-03:00"
      },
      "relationships": {
        "notification": {
          "data": {
            "id": "1",
            "type": "notifications"
          }
        },
        "trigger-user": {
          "data": {
            "id": "1",
            "type": "users"
          }
        },
        "recipient-user": {
          "data": {
            "id": "2",
            "type": "users"
          }
        },
        "trip": {
          "data": {
            "id": "2",
            "type": "trips"
          }
        },
        "take": {
          "data": {
            "id": "1",
            "type": "takes"
          }
        }
      }
    }
  ],
  "included": [
    {
      "id": "1",
      "type": "notifications",
      "attributes": {
        "notification-type": "take_request"
      }
    },
    {
      "id": "1",
      "type": "users",
      "attributes": {
        "first-name": "Camila",
        "last-names": "Parra"
      }
    },
    {
      "id": "2",
      "type": "users",
      "attributes": {
        "first-name": "Javier",
        "last-names": "Romero Rojas"
      }
    },
    {
      "id": "2",
      "type": "trips",
      "attributes": {
        "summary": "Ida a Campus Oriente",
        "route-id": 2,
        "driver-id": 2,
        "vehicle-id": 2,
        "departure-datetime": "2016-11-28T19:14:00.000-03:00",
        "arrival-datetime": "2016-11-28T20:14:00.000-03:00"
      }
    },
    {
      "id": "1",
      "type": "takes",
      "attributes": {
        "trip-id": 2,
        "user-id": 1
      }
    }
  ]
}
```

This endpoint retrieves all notifications for the user associated with the token provided in the header.
Authentication is required for this endpoint.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/notifies`


# Trips

## Get All Trips

> The HTTP Request returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "trips",
      "attributes": {
        "status": "Activo",
        "route-id": 1,
        "summary": "Ida a Campus San Joaquín",
        "departure-datetime": "2016-11-29T18:00:00.000-03:00",
        "arrival-datetime": "2016-11-29T19:00:00.000-03:00",
        "vehicle-id": 1
      },
      "relationships": {
        "driver": {
          "data": {
            "id": "1",
            "type": "users"
          }
        },
        "passengers": {
          "data": []
        }
      }
    },
    {
      "id": "2",
      "type": "trips",
      "attributes": {
        "status": "Activo",
        "route-id": 2,
        "summary": "Ida a Campus Oriente",
        "departure-datetime": "2016-11-28T19:14:00.000-03:00",
        "arrival-datetime": "2016-11-28T20:14:00.000-03:00",
        "vehicle-id": 2
      },
      "relationships": {
        "driver": {
          "data": {
            "id": "2",
            "type": "users"
          }
        },
        "passengers": {
          "data": [
            {
              "id": "1",
              "type": "users"
            }
          ]
        }
      }
    },
    {
      "id": "3",
      "type": "trips",
      "attributes": {
        "status": "Activo",
        "route-id": 3,
        "summary": "Ida a Campus San Joaquín",
        "departure-datetime": "2016-11-28T18:38:00.000-03:00",
        "arrival-datetime": "2016-11-28T18:38:00.000-03:00",
        "vehicle-id": 1
      },
      "relationships": {
        "driver": {
          "data": {
            "id": "1",
            "type": "users"
          }
        },
        "passengers": {
          "data": []
        }
      }
    }
  ],
  "included": [
    {
      "id": "1",
      "type": "users",
      "attributes": {
        "first-name": "Camila",
        "last-names": "Parra"
      }
    },
    {
      "id": "2",
      "type": "users",
      "attributes": {
        "first-name": "Javier",
        "last-names": "Romero Rojas"
      }
    }
  ]
}
```

This endpoint retrieves all trips from all users.
Authentication is required for this endpoint as it includes information about specific drivers.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/trips`

## Get a Specific Trip

> The HTTP Request returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "trips",
    "attributes": {
      "status": "Activo",
      "route-id": 2,
      "summary": "Ida a Campus Oriente",
      "departure-datetime": "2016-11-28T19:14:00.000-03:00",
      "arrival-datetime": "2016-11-28T20:14:00.000-03:00",
      "vehicle-id": 2
    },
    "relationships": {
      "driver": {
        "data": {
          "id": "2",
          "type": "users"
        }
      },
      "passengers": {
        "data": [
          {
            "id": "1",
            "type": "users"
          }
        ]
      }
    }
  },
  "included": [
    {
      "id": "2",
      "type": "users",
      "attributes": {
        "first-name": "Javier",
        "last-names": "Romero Rojas"
      }
    },
    {
      "id": "1",
      "type": "users",
      "attributes": {
        "first-name": "Camila",
        "last-names": "Parra"
      }
    }
  ]
}
```

This endpoint retrieves a specific trip.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/trips/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the trip to retrieve



# Takes

## Get All Takes

> The HTTP Request returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "takes",
      "attributes": {
        "status": "Pendiente",
        "pickup-datetime": "2016-11-28T19:14:00.000-03:00",
        "trip-id": 2,
        "pickup-location": 3,
        "passenger-id": 1
      },
      "relationships": {
        "user": {
          "data": {
            "id": "1",
            "type": "users"
          }
        },
        "trip": {
          "data": {
            "id": "2",
            "type": "trips"
          }
        }
      }
    }
  ],
  "included": [
    {
      "id": "1",
      "type": "users",
      "attributes": {
        "first-name": "Camila",
        "last-names": "Parra"
      }
    },
    {
      "id": "2",
      "type": "trips",
      "attributes": {
        "status": "Activo",
        "summary": "Ida a Campus Oriente",
        "route-id": 2,
        "driver-id": 2,
        "vehicle-id": 2,
        "departure-datetime": "2016-11-28T19:14:00.000-03:00",
        "arrival-datetime": "2016-11-28T20:14:00.000-03:00"
      }
    }
  ]
}
```

This endpoint retrieves all takes for the user associated with the token provided in the header.
Authentication is required for this endpoint.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/takes`

## Get a Specific Take

> The HTTP Request returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "takes",
    "attributes": {
      "status": "Pendiente",
      "pickup-datetime": "2016-11-29T18:00:00.000-03:00",
      "trip-id": 1,
      "pickup-location": 5,
      "passenger-id": 2
    },
    "relationships": {
      "user": {
        "data": {
          "id": "2",
          "type": "users"
        }
      },
      "trip": {
        "data": {
          "id": "1",
          "type": "trips"
        }
      }
    }
  },
  "included": [
    {
      "id": "2",
      "type": "users",
      "attributes": {
        "first-name": "Javier",
        "last-names": "Romero Rojas"
      }
    },
    {
      "id": "1",
      "type": "trips",
      "attributes": {
        "status": "Activo",
        "summary": "Ida a Campus San Joaquín",
        "route-id": 1,
        "driver-id": 1,
        "vehicle-id": 1,
        "departure-datetime": "2016-11-29T18:00:00.000-03:00",
        "arrival-datetime": "2016-11-29T19:00:00.000-03:00"
      }
    }
  ]
}
```

This endpoint retrieves a specific take (both the user who is the passenger in the take and the driver of the take can access it).
Authentication is required for this endpoint.

### HTTP Request

`GET http://ubersidad.herokuapp.com/api/v1/takes/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the take to retrieve
