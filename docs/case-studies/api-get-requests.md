---
layout: default
title: GET Requests
---

# GET Requests: Retrieving Data from APIs

The GET method is the most commonly used HTTP method. It requests data from a specified resource without modifying it. GET requests are **idempotent**, meaning that making the same request multiple times produces the same result.

---

## How GET Requests Work

When you send a GET request, the following sequence occurs:

1. The client sends an HTTP GET request to the API endpoint.
2. The server processes the request and locates the requested resource.
3. The server returns the data in the response body, typically in JSON format.
4. The response includes a status code indicating the result.

<div class="note">
<strong>Note</strong>
GET requests should never modify data on the server. They are designed exclusively for retrieving information.
</div>

---

## Example 1: Retrieve Country by Name

Use the REST Countries API to retrieve detailed information about a specific country.

**Endpoint:**

```
GET https://restcountries.com/v3.1/name/{name}
```

**Request Example:**

```
GET https://restcountries.com/v3.1/name/japan
```

**Response (200 OK):**

```json
[
  {
    "name": {
      "common": "Japan",
      "official": "Japan",
      "nativeName": {
        "jpn": {
          "official": "\u65e5\u672c",
          "common": "\u65e5\u672c"
        }
      }
    },
    "capital": ["Tokyo"],
    "region": "Asia",
    "subregion": "Eastern Asia",
    "population": 125836021,
    "currencies": {
      "JPY": {
        "name": "Japanese yen",
        "symbol": "\u00a5"
      }
    },
    "languages": {
      "jpn": "Japanese"
    }
  }
]
```

### Key Response Fields

| Field | Description | Type |
|-------|-------------|------|
| `name.common` | Common name of the country | String |
| `name.official` | Official name of the country | String |
| `capital` | Capital city or cities | Array |
| `region` | Geographic region | String |
| `population` | Total population | Integer |
| `currencies` | Official currencies | Object |
| `languages` | Official languages | Object |

---

## Example 2: Retrieve Countries by Region

Retrieve a list of all countries in a specific geographic region.

**Endpoint:**

```
GET https://restcountries.com/v3.1/region/{region}
```

**Request Example:**

```
GET https://restcountries.com/v3.1/region/europe
```

**Response (200 OK):**

The response returns an array of country objects for all European countries. Each object contains the same fields as the single-country response.

<div class="tip">
<strong>Tip</strong>
Valid region values include: africa, americas, asia, europe, and oceania.
</div>

---

## Example 3: Filter Response Fields

To reduce the response payload, use the <code>fields</code> query parameter to retrieve only the data you need.

**Endpoint:**

```
GET https://restcountries.com/v3.1/all?fields=name,capital,population
```

**Response (200 OK):**

```json
[
  {
    "name": {
      "common": "Germany",
      "official": "Federal Republic of Germany"
    },
    "capital": ["Berlin"],
    "population": 83240525
  },
  {
    "name": {
      "common": "France",
      "official": "French Republic"
    },
    "capital": ["Paris"],
    "population": 67390000
  }
]
```

<div class="tip">
<strong>Tip</strong>
Filtering fields reduces the response size and improves API performance, especially when retrieving data for all countries.
</div>

---

## Common GET Request Status Codes

| Status Code | Description |
|------------|-------------|
| **200 OK** | The request was successful and the response contains the requested data. |
| **304 Not Modified** | The resource has not changed since the last request. The client can use the cached version. |
| **400 Bad Request** | The request was malformed or contains invalid parameters. |
| **404 Not Found** | The requested resource does not exist. For example, searching for a country name that does not match any record. |

---

## Best Practices for GET Requests

- **Use query parameters** to filter results and reduce response size.
- **Cache responses** when the data does not change frequently to minimize API calls.
- **Handle errors gracefully** by checking the status code before processing the response data.
- **Never include sensitive data** in GET request URLs, as URLs are logged in browser history and server logs.

<div class="warning">
<strong>Warning</strong>
Avoid sending sensitive information such as passwords or API keys as query parameters in GET requests. Use request headers instead.
</div>

---

## Testing GET Requests in Postman

1. Open Postman and click **New** > **HTTP Request**.
2. Select **GET** from the HTTP method dropdown.
3. Enter the API endpoint URL in the request bar.
4. Click **Send**.
5. Review the response body, status code, and response time in the lower panel.

---

# Sources

- [REST Countries API Documentation](https://restcountries.com/)
- [MDN Web Docs: HTTP GET Method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/GET)
