---
layout: default
title: Incomplete API Specifications
description: Enriching the Swagger Petstore OpenAPI spec
---

# Troubleshooting: Incomplete API Specifications

Many API consumers or developers don't read reference docs. They consume the OpenAPI JSON directly: Postman imports it, code generators turn it into SDKs, and AI agents and MCP servers read it to learn how to call the API. Whatever the spec says, every downstream tool repeats.

The Swagger Petstore spec is a widely used sample, and it shows the typical gaps: one-line descriptions, no request or response examples, error responses with no body, and boilerplate such as "successful operation." A developer or an agent reading it can call the API but can't predict what will go wrong.

![Swagger PET APIs](/images/swagger_pet_api.jpg)

This troubleshooting guide helps you to make the JSON itself the documentation, without changing the API contract.

## Prerequisites

* Export the Swagger PET APIs in JSON format and open it using Visual Studio Code.
* Install the Spectral Linter extension on Visual Studio Code to audit and highlight problems in the API specification.
* Install Postman to test the APIs.

## Symptom 1: Missing Success Response
Only a 405 response is listed, which stands for **Method Not Allowed**. At least one successful response in the 2xx or 3xx range must be listed.

### Cause
Specs are often generated from code annotations that don’t include descriptions or every status code.

### Solution
Run the operation in Postman to verify that a successful 200 response exists.

![Post Pet 200 Response](/images/swagger_pet_api_200_response.jpg)

According to the API response, a 200 OK response exists, so update the API specification to include 200 OK.

![Add 200 Response](/images/add_200_OK_response.jpg)

### Result

All the success responses with their appropriate descriptions are listed in the API specification.

## Symptom 2: Incomplete Descriptions or Blank Descriptions
The documentation lives inside the JSON. If a field says "description": "status", every downstream tool inherits that weak description.

![Empty description field](/images/empty_description_PET_API.jpg)

### Cause

Specs are often generated from code annotations that don’t include descriptions or every status code.

### Solution

Manually enter a an accurate description, verified with the engineer.

![Updated description field](/images/updated_description_PET_API.jpg)

### Result

The API specification is enriched with applicable descriptions.
