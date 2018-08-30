# Table of Contents
* API Routes
    * [Customer Samples](#customer-sample-routes)
    * [Projects](#project-routes)
    * [Scenarios](#scenario-routes)
    * [Simulations](#simulation-routes)
* Objects
    * [Customer Sample](#customer-sample-object)
    * [Project](#project-object)
    * [Scenario](#scenario-object)
    * [Bundle](#bundle-object)
    * [Product](#product-object)
    * [Customer](#customer-object)

# Customer Sample Routes

## `GET /api/customers`

**_Purpose_**: Returns a list of all customer samples visible to the user  
**_Request Parameters_**: None  
**_Response Format_**:
* HTTP status code on success: `200 OK`
* On success, an array of [customer sample objects](#customer-sample-object) is returned in the response body.

## `POST /api/customers` \*\***_ADMIN ONLY_**\*\*

**_Purpose_**: Inserts a new customer sample  
**_Request Parameters_**:

| Body Parameter | VALUE TYPE   | VALUE              |
| -------------- | ------------ | ------------------ |
| description   | string        | _Optional_. A short description of the customer sample |
| name          | string        | _Required_. The name of the customer sample |
| customers_number | integer    | _Required_. The desired number of simulated customers in the sample |
| market_size   | integer       | _Optional_. The size of the real-world market for this sample |
| origin        | string        | _Required_. The method from which the customer sample was created (ex: Expert Opinion) |
| products      | An array of [product objects](#product-object) | _Required_. The list of all products included in the sample |
| product_wtps  | An array of floats | _Required_. A WTP for each product |

**_Response Format_**:
* HTTP status code on success: `201 CREATED`
* On success, the project_key is returned in the response body: `{"customer_sample_key": "1234"}`

## `GET /api/customers/<id>`

**_Purpose_**: Returns the [customer sample objects](#customer-sample-object) specified by the given `id`  
**_Request Parameters_**:

| Path Parameter | VALUE              |
| -------------- | ------------------ |
| id             | The id of the desired customer sample |

**_Response Format_**:
* HTTP status code on success: `200 OK`
* On success, a [customer sample objects](#customer-sample-object) is returned in the response body.

## `PUT /api/customers/<id>` \*\***_ADMIN ONLY_**\*\*

**_Purpose_**: Updates data of a customer sample specified by the given `id`  
**_Request Parameters_**:

| Path Parameter | VALUE              |
| -------------- | ------------------ |
| id             | The id of the desired project |

| Body Parameter | VALUE TYPE   | VALUE              |
| -------------- | ------------ | ------------------ |
| description   | string        | _Optional_. A short description of the customer sample |
| name          | string        | _Optional_. The name of the customer sample |
| customers_number | integer    | _Optional_. The desired number of simulated customers in the sample |
| market_size   | integer       | _Optional_. The size of the real-world market for this sample |
| origin        | string        | _Optional_. The method from which the customer sample was created (ex: Expert Opinion) |
| products      | An array of [product objects](#product-object) | _Optional_. The list of all products included in the sample |
| product_wtps  | An array of floats | _Optional_. A WTP for each product |

**_Response Format_**:
* HTTP status code on success: `204 NO CONTENT`
* On success, nothing is returned.

## `DELETE /api/customers/<id>`

**_Purpose_**: Deletes a customer sample specified by the given `id`  
**_Request Parameters_**:  
    * Path: `id` the desired customer sample's id
**_Response Format_**:
* HTTP status code on success: `204 NO CONTENT`
* On success, nothing is returned.

# Project Routes

## `GET /api/projects`

**_Purpose_**: Returns a list of all projects visible to the user  
**_Request Parameters_**: None  
**_Response Format_**:
* HTTP status code on success: `200 OK`
* On success, an array of [project objects](#project-object) is returned in the response body.

## `POST /api/projects`

**_Purpose_**: Inserts a new project  
**_Request Parameters_**:

| Body Parameter | VALUE TYPE    | VALUE              |
| -------------- | ------------- | ------------------ |
| country        | string        | _Optional_. The relevant country for the project. |
| customer_key   | string        | _Optional_. The key for a desired customer sample. |
| description    | string        | _Optional_. A description of the project. |
| industry       | string        | _Optional_. The relevant industry for the project. |
| name           | string        | _Required_. The name of the project. |

**_Response Format_**:
* HTTP status code on success: `201 CREATED`
* On success, the project_key is returned in the response body: `{"project_key": "1234"}`

## `GET /api/projects<id>`

**_Purpose_**: Returns the [project object](#project-object) specified by the given `id`  
**_Request Parameters_**:

| Path Parameter | VALUE              |
| -------------- | ------------------ |
| id             | The id of the desired project |

**_Response Format_**:
* HTTP status code on success: `200 OK`
* On success, a [project object](#project-object) is returned in the response body.

## `PUT /api/projects/<id>`

**_Purpose_**: Updates data of a project specified by the given `id`  
**_Request Parameters_**:

| Path Parameter | VALUE              |
| -------------- | ------------------ |
| id             | The id of the desired project |

| Body Parameter | VALUE TYPE    | VALUE              |
| -------------- | ------------- | ------------------ |
| country        | string        | _Optional_. The relevant country for the project. |
| customer_key   | string        | _Optional_. The key for a desired customer sample. |
| description    | string        | _Optional_. A description of the project. |
| industry       | string        | _Optional_. The relevant industry for the project. |
| name           | string        | _Optional_. The name of the project. |

**_Response Format_**:
* HTTP status code on success: `204 NO CONTENT`
* On success, nothing is returned.

## `DELETE /api/projects/<id>`

**_Purpose_**: Deletes a project specified by the given `id`  
**_Request Parameters_**:  
    * Path: `id` the desired project's id
**_Response Format_**:
* HTTP status code on success: `204 NO CONTENT`
* On success, nothing is returned.

# Scenario Routes

## `GET /api/scenarios`

**_Purpose_**: Returns a list of all scenarios visible to the user  
**_Request Parameters_**: None  
**_Response Format_**:
* HTTP status code on success: `200 OK`
* On success, an array of [scenario objects](#scenario-object) is returned in the response body.

## `POST /api/scenarios`

**_Purpose_**: Inserts a new scenario  
**_Request Parameters_**:

| Body Parameter | VALUE TYPE    | VALUE              |
| -------------- | ------------- | ------------------ |
| bundles       | An array of [bundles objects](#bundle-object) | _Optional_. All 'bundles' created for the scenario's offer |
| description   | string        | _Optional_. A short description of the project |
| market_size   | integer       | _Optional_. The size of the real-world market for this scenario |
| name          | string        | _Required_. The name of the project |
| products      | An array of [product objects](#product-object) | The list of all products from the scenario's [customer sample](#customer-sample-object) |
| project_key   | string        | _Required_. The key of the scenario's [project](#project-object) |

**_Response Format_**:
* HTTP status code on success: `201 CREATED`
* On success, the scenario_key is returned in the response body: `{"scenario_key": "1234"}`

## `GET /api/scenarios<id>`

**_Purpose_**: Returns the [scenario object](#scenario-object) specified by the given `id`  
**_Request Parameters_**:

| Path Parameter | VALUE              |
| -------------- | ------------------ |
| id             | The id of the desired scenario |

**_Response Format_**:
* HTTP status code on success: `200 OK`
* On success, a [scenario object](#scenario-object) is returned in the response body.

## `PUT /api/scenarios/<id>`

**_Purpose_**: Updates data of a scenario specified by the given `id`  
**_Request Parameters_**:

| Path Parameter | VALUE              |
| -------------- | ------------------ |
| id             | The id of the desired scenario |

| Body Parameter | VALUE TYPE    | VALUE              |
| -------------- | ------------- | ------------------ |
| bundles       | An array of [bundles objects](#bundle-object) | _Optional_. All 'bundles' created for the scenario's offer |
| description   | string        | _Optional_. A short description of the project |
| market_size   | integer       | _Optional_. The size of the real-world market for this scenario |
| name          | string        | _Optional_. The name of the project |
| products      | An array of [product objects](#product-object) | The list of all products from the scenario's [customer sample](#customer-sample-object) |
| project_key   | string        | _Optional_. The key of the scenario's [project](#project-object) |

**_Response Format_**:
* HTTP status code on success: `204 NO CONTENT`
* On success, nothing is returned.

## `DELETE /api/scenarios/<id>`

**_Purpose_**: Deletes a scenario specified by the given `id`  
**_Request Parameters_**:  
    * Path: `id` the desired scenario's id
**_Response Format_**:
* HTTP status code on success: `204 NO CONTENT`
* On success, nothing is returned.

# Simulation Routes

## `GET /api/simulate/<id>`

**_Purpose_**: Runs the simulation for the scenario specified by the given `id` 
**_Request Parameters_**:

| Path Parameter | VALUE              |
| -------------- | ------------------ |
| id             | The id of the desired scenario |

**_Response Format_**:
* HTTP status code on success: `200 OK`
* On success, an object containing the simulation results is returned in the response body.

## `GET /api/results/<id>`

**_Purpose_**: Returns the simulation results for the scenario specified by the given `id` 
**_Request Parameters_**:

| Path Parameter | VALUE              |
| -------------- | ------------------ |
| id             | The id of the desired scenario |

**_Response Format_**:
* HTTP status code on success: `200 OK`
* On success, an object containing the simulation results is returned in the response body.

# Object Documentation

## Customer Sample Object

| KEY           | VALUE TYPE    | VALUE DESCRIPTION  |
| ------------- | ------------- | ------------------ |
| customers     | A dictionary of [customer objects](#customer-object) | Contains all _simulated_ customer details |
| description   | string        | A short description of the customer sample |
| last_edit     | integer       | The time (in seconds from 01/01/1970) since last edit |
| name          | string        | The name of the customer sample |
| market_size   | integer       | The size of the real-world market for this sample |
| origin        | string        | The method from which the customer sample was created (ex: Expert Opinion) |
| products      | An array of [product objects](#product-object) | The list of all products included in the sample |

## Project Object

| KEY           | VALUE TYPE    | VALUE DESCRIPTION  |
| ------------- | ------------- | ------------------ |
| country       | string        | The country to which the project pertains (_can be null_) |
| customer_key  | string        | The key of the project's [customer sample](#customer-sample-object) (_can be null_) |
| description   | string        | A short description of the project |
| industry      | string        | The industry to which the project pertains (_can be null_) |
| last_edit     | integer       | The time (in seconds from 01/01/1970) since last edit |
| name          | string        | The name of the project |
| user_id       | string        | The id of the project owner |

## Scenario Object

| KEY           | VALUE TYPE    | VALUE DESCRIPTION  |
| ------------- | ------------- | ------------------ |
| bundles       | An array of [bundles objects](#bundle-object) | All 'bundles' created for the scenario's offer |
| description   | string        | A short description of the project |
| last_edit     | integer       | The time (in seconds from 01/01/1970) since last edit |
| market_size   | integer       | The size of the real-world market for this scenario |
| name          | string        | The name of the project |
| products      | An array of [product objects](#product-object) | The list of all products from the scenario's [customer sample](#customer-sample-object) |
| project_key   | string        | The key of the scenario's [project](#project-object) |
| simulation_data | A dictionary | Contains the simulation output data |

## Bundle Object

| KEY           | VALUE TYPE    | VALUE DESCRIPTION  |
| ------------- | ------------- | ------------------ |
| cost          | float         | The sum of all product costs |
| name          | string        | The name of the project |
| is_competition | integer      | Set to 1 when the bundle is that of a competitor, else 0  |
| is_included   | integer       | Set to 1 when the bundle is to be included in the simulation, else 0 |
| price_points  | An array of floats | The list of all potentail price points to try in the simulation |
| products      | An array of [product objects](#product-object) | The list of all products included in the bundle [customer sample](#customer-sample-object) |

## Product Object

| KEY           | VALUE TYPE    | VALUE DESCRIPTION  |
| ------------- | ------------- | ------------------ |
| category      | String        | The product category. Set to 'None' if no category |
| cost          | float         | The cost of the product |
| name          | string        | The name of the product |
| is_included   | integer       | Indicates whether or not to include a product in the Scenario **Only used in Scenario** |

## Customer Object

| KEY           | VALUE TYPE    | VALUE DESCRIPTION  |
| ------------- | ------------- | ------------------ |
| WTPs          | A dictionary of WTPs by product | Currently, the product name is the key and the value is the WTP \*\***NEED TO STOP USING PRODUCT NAMES AS KEYS**\*\* |
| **TBD**       | TBD           | In the future, further attributes will be given to simulated customers |
