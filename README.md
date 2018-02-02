# Table reservation backend API

Table reservation is an application to help the restaurant owner manage tables. A table is created by posting a name to
the backend. Tables can be queried from the backend and guests can submit times suitable for them to make a reservation.

The application needs to persist data between launches and should be written in Java and Spring Boot. You can choose the
architectural design and patterns freely.

Some guidelines:
- Your solution should be able to scale for a larger purpose. Thus imagine the app being extended to cover a larger API
 and/or a bigger feature set.
- Showcase your abilities, and use the task to demonstrate your idea of best practices, regarding coding style, project
 structure, frameworks, patterns, design, testing etc.
- There is no right or wrong solution, as long as it is your solution.
- Be prepared to describe your work in detail.

## Create a table

Endpoint: `/api/v1/table`

### Request

Method: `POST`

Body:

```
{
  "name": "Table with a view to the mountains"
}
```

### Response

Body:
```
{
  "id": 0
}
```

## Make a reservation for a table

Endpoint: `/api/v1/table/{id}/reservation`

### Request

Method: `POST`

Body:

```
{
  "timeslot": {
    "from": "2018-01-04T18:00:00.000Z",
    "to": "2018-01-04T20:00:00.000Z"
  } 
}
```

### Response

Return the response status depending whether the reservation was successful or not. For example, if the tables is
already reserved at the mentioned time slot, then the status should be `CONFLICT`.

## Show a table

Endpoint: `/api/v1/table/{id}`

### Request

Method: `GET`

### Response

Body:
```
{
  "id": 0,
  "name": "Table with a view to the mountains",
  "reservations": [
    {
      "from": "2018-01-04T18:00:00.000Z",
      "to": "2018-01-04T20:00:00.000Z"
    },
    {
      "from": "2018-01-04T20:00:00.000Z",
      "to": "2018-01-04T21:00:00.000Z"
    }
  ]
}
```
