---
layout: default
title: About APIs
---

# About APIs

<div class="reader-note">
<strong>Note to the Reader</strong>
This section contains highly generic content about REST APIs. Based on the type of data and type of query, the API documentation will vary.
</div>

Application Programming Interfaces (APIs) are the basis on which the entire world’s applications talk to each other and enable people to seamlessly perform actions on the internet.

Well-documented APIs help developers in companies dealing with data and data-driven services connect stand-alone applications when information and processes must flow between them. Using APIs enables developers to work securely without exposing code or protected data, while also bridging the gap between stand-alone applications.

For example, a weather app on your phone would connect with the National Weather Service to display real-time weather data. In this case, the weather app APIs connect to the National Weather Service API server to provide real-time weather updates.

## API Operations

Using APIs, you can perform the following operations:

- **GET**: It requests data from a specified resource without modifying it.

- **POST**: It modifies data on the server by creating new resources.

- **PUT**: It modifies data on the server by updating existing resources.

- **DELETE**: removes a specified resource from the server.

## API Document Elements

A standard API document has to have the following sections:

- Introduction: A paragraph explaining the objective and context in which the API can be used.

- Permissions: The permissions required to execute the API query.

- Request: The structure of the request with the required API endpoint. The request can be in the following formats:

    - HTTP

    - JavaScript

    - Python

- Request Parameters: Request query parameters.

- Request Headers: Typically contains the Bearer Token.

- Request Body: If you need to supply additional parameters or data in the query, you can do so using a JSON or XML body.

- Response - List the success response code and error response code in this section.

- Response Parameters - List the response parameters if applicable.

- Example Request - Add an example with the request syntax, parameters, and headers.

- Example Response - Add an example with the response and any parameters.
