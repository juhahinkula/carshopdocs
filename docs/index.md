# General

## Car Shop REST API Documentation

The Car Shop API is a RESTful web service designed to manage the car stock of a car shop. It provides the ability to create, read, update, and delete (CRUD) car records in the car shop's database.

Overview:

The API is structured around one main resource: [**Cars**](cars.md)

The car table in the backend database contains the following fields:

- `id`: A unique identifier for each car (integer).
- `brand`: The manufacturer of the car (string).
- `model`: The model of the car (string).
- `color`: The color of the car (string).
- `fuel`: The fuel type of the car (string).
- `modelYear`: The year the car was manufactured (integer).
- `price`: The price of the car (number).

## Base URL
```
https://carrestservice-carshop.rahtiapp.fi/
```

## Reset Database
To reset database you can use the following request that deletes all data from the database and re-populate it with the original demo data. 

```
POST https://carrestservice-carshop.rahtiapp.fi/reset
```
Response:

Upon successful reset, the API will return a 200 OK status code and the response body contains text: **DB reset done**. If the reset operation fails for any reason, the API will return an appropriate error status code and message.
