# Cars

## Base URL
```
https://carrestservice-carshop.rahtiapp.fi/
```
## Endpoints

### Get All Cars
To retrieve all cars , you can use the `GET /cars` endpoint.

Request:

No parameters are required for this endpoint.

Response:

The response is a JSON object with a `_embedded` field containing an array of cars. Each car object includes the following fields:

- `brand`: The manufacturer of the car (string).
- `model`: The model of the car (string).
- `color`: The color of the car (string).
- `fuel`: The fuel type of the car (string).
- `modelYear`: The year the car was manufactured (integer).
- `price`: The price of the car (number).
- `_links`: A set of links related to the customer. Each link object includes:
    - `self`: A link to the car's own information. (string)
    - `car`: A link to the car's information. (string)

Example Response
```json
{
  "_embedded" : {
    "cars" : [ {
      "brand" : "Volvo",
      "model" : "XC60",
      "color" : "Black",
      "fuel" : "E95",
      "modelYear" : 2023,
      "price" : 59000,
      "_links" : {
        "self" : {
          "href" : "https://carrestservice-carshop.rahtiapp.fi/cars/8041"
        },
        "car" : {
          "href" : "https://carrestservice-carshop.rahtiapp.fi/cars/8041"
        }
      }
    }, {
      "brand" : "Nissan",
      "model" : "X-Trail",
      "color" : "Silver",
      "fuel" : "Diesel",
      "modelYear" : 2012,
      "price" : 19000,
      "_links" : {
        "self" : {
          "href" : "https://carrestservice-carshop.rahtiapp.fi/cars/8042"
        },
        "car" : {
          "href" : "https://carrestservice-carshop.rahtiapp.fi/cars/8042"
        }
      }
    }
}
```

### Get Car by Id
To retrieve a specific car's details, you can use the `GET /cars/{id}` endpoint, where `{id}` is the unique identifier of the car.

Request:

- The request does not require a request body, only the car's id as a path parameter.

Path Parameters:

- `id` (required): The unique identifier of the car. This is an integer.

Example Request:
```
GET /cars/123
```

### Create New Car
To create a new car you can use `POST /cars` endpoint.

Request:

This endpoint requires a JSON object in the request body with the following fields:

- `brand`: The manufacturer of the car (string).
- `model`: The model of the car (string).
- `color`: The color of the car (string).
- `fuel`: The fuel type of the car (string).
- `modelYear`: The year the car was manufactured (integer).
- `price`: The price of the car (number).

Headers:

 `'Content-Type': 'application/json'`.

Example Request:
```json
POST /cars
Content-Type: application/json

{ 
  "brand": "BWM", 
  "model": "3", 
  "color": "Red", 
  "fuel": "Hybrid", 
  "year": "2024", 
  "price": "48000" 
} 
```

### Update Car

To update a specific car's details, you can use the `PUT /cars/{id}` endpoint, where `{id}` is the unique identifier of the car.

Request:

The request requires the car's id as a path parameter and the updated car details in the request body as a JSON string.

Headers:

`Content-Type: 'application/json'`

Path Parameters:

`id` (required): The unique identifier of the car. This is an integer.

Request Body:
The request body should be a JSON object containing the updated car details. All fields are optional, and only the provided fields will be updated.

- `brand`: The manufacturer of the car (string).
- `model`: The model of the car (string).
- `color`: The color of the car (string).
- `fuel`: The fuel type of the car (string).
- `modelYear`: The year the car was manufactured (integer).
- `price`: The price of the car (number).

Example Request:
```json
PUT /cars/123
Content-Type: application/json

{ 
  "brand": "BWM", 
  "model": "3", 
  "color": "White", 
  "fuel": "Hybrid", 
  "year": "2024", 
  "price": "48000" 
} 

```
### Delete Car

To delete a specific car, you can use the `DELETE /cars/{id}` endpoint, where `{id}` is the unique identifier of the car.

Request:

The request does not require a request body, only the car's `id` as a path parameter.

Path Parameters:

`id` (required): The unique identifier of the car. This is an integer.

Response:

Upon successful deletion, the API will return a 204 No Content status code. If the car with the provided id does not exist, the API will return a 404 Not Found status code.
