# FakeStoreAPI – Postman Testing

This project contains an API testing suite for the **FakeStoreAPI** using **Postman** and JavaScript test scripts.

The collection covers basic e-commerce scenarios such as viewing products, filtering by category, creating, updating, and deleting products.



# Tech Stack

- Postman (Collections & Environments)
- JavaScript test scripts (pm API, Chai assertions)
- FakeStoreAPI (https://fakestoreapi.com)



# Covered Endpoints

# Products

- *GET /products
  - Status code is 200
  - Products list is not empty

- *GET /products/1
  - Status code is 200
  - Product id is 1
  - Product has required fields: title, price, category

- *GET `/products/categories`**
  - Status code is 200
  - Categories list is not empty
  - Categories contain "jewelery"

- *GET /products/category/jewelery
  - Status code is 200
  - At least one product is returned
  - All products belong to the `jewelery` category

# Negative Scenarios

- *GET /products/9999 (invalid id)
  - Status code is 200
  - Response body is empty (no product returned)

- **GET /products/category/invalidcat (invalid category)
  - Status code is 200
  - Response is an empty list

#  Create / Update / Delete

- *POST `/products` – Create Product**
  - Status code is 201
  - Response contains generated `id`
  - Product fields (title, price, category) match the request

- PUT /products/{id} – Update Product
  - Status code is 200
  -  API bug detected: the response body only contains "id" and does return updated fields such as title or price.

- DELETE `/products/{id}` – Delete Product
  - Status code is 200



# How to Run the Tests

1. Import the collection:
   - `FakeStoreAPI.postman_collection.json`
2. Import the environment:
   - `FakeStoreAPIENV.postman_environment.json`
3. Select the **FakeStoreAPIENV** environment in Postman.
4. Open **Collection Runner**, select the collection, and run all requests.
5. Check the **Test Results** tab to see passed/failed tests.



 Notes

- This project demonstrates:
  - Positive and negative API tests
  - Usage of environment variables
  - Automated verification of responses using Postman test scripts
  - Detection of real API issues (e.g. incorrect PUT response in FakeStoreAPI)

