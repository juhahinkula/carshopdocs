# Cars

## Base URL
```
https://car-rest-service-carshop.2.rahtiapp.fi/
```
## Endpoints

### Get All Cars
Retrieve all cars.

**Request:**

- HTTP Method: `GET`
- Endpoint: `/cars`
- Request parameters: None

Example Request:
```
GET /cars
```

**Response:**

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
Retrieve a specific car's details.

**Request:**

- HTTP Method: `GET`
- Endpoint: `/cars/{id}`
- Path parameters: `{id}` (integer, required): The unique identifier of the car.

Example Request:
```
GET /cars/123
```
**Response:**

- Body: JSON object with the car's details.

### Create New Car
Create a new car. 

**Request:**

- HTTP Method: `POST`
- Endpoint: `/cars`
- Request Headers:
    - `'Content-Type' : 'application/json'`
- Request body: JSON object with the following fields (all required)
    - `brand`: The manufacturer of the car (string).
    - `model`: The model of the car (string).
    - `color`: The color of the car (string).
    - `fuel`: The fuel type of the car (string).
    - `modelYear`: The year the car was manufactured (integer).
    - `price`: The price of the car (number).

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

Update a specific car's details. 

**Request:**

- HTTP Method: `PUT`
- Endpoint: `/cars/{id}`
- Path Parameters: `{id}` (integer, required): The unique identifier of the car.
- Request Headers:
    - `'Content-Type' : 'application/json'`
- Request body: JSON object with the following fields
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

Delete a specific car.

**Request:**

- HTTP Method: `DELETE`
- Endpoint: `/cars/{id}`
- Path parameters: `{id}` (integer, required): The unique identifier of the car.

**Response:**

Upon successful deletion, the API will return a 204 No Content status code. If the car with the provided id does not exist, the API will return a 404 Not Found status code.
