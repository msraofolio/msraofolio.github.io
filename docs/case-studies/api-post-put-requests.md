---
layout: default
title: POST and PUT Requests
---

# POST and PUT Requests: Creating and Updating Data

While GET requests retrieve data, POST and PUT requests modify data on the server. These methods are essential for creating new resources and updating existing ones.

---

## POST vs PUT: Understanding the Difference

| Feature | POST | PUT |
|---------|------|-----|
| **Purpose** | Create a new resource | Update an existing resource (or create if it does not exist) |
| **Idempotent** | No. Sending the same request twice creates two resources. | Yes. Sending the same request twice produces the same result. |
| **Request Body** | Contains the data for the new resource | Contains the complete updated resource |
| **Typical Response** | 201 Created | 200 OK or 204 No Content |
| **URL Pattern** | `POST /api/countries` | `PUT /api/countries/{id}` |

<div class="note">
<strong>Note</strong>
The REST Countries API is a public, read-only API that supports only GET requests. The POST and PUT examples in this topic use a simulated API structure to demonstrate how these methods work in a real-world development scenario.
</div>

---

## POST Requests: Creating New Resources

A POST request sends data to the server to create a new resource. The request body contains the data for the new resource in JSON format.

### Example 1: Create a New Country Record

**Endpoint:**

```
POST https://api.example.com/v1/countries
```

**Request Headers:**

```
Content-Type: application/json
Authorization: Bearer your-api-key-here
```

**Request Body:**

```json
{
  "name": {
    "common": "Wakanda",
    "official": "Kingdom of Wakanda"
  },
  "capital": ["Birnin Zana"],
  "region": "Africa",
  "subregion": "Eastern Africa",
  "population": 6000000,
  "currencies": {
    "VBR": {
      "name": "Vibranium Credit",
      "symbol": "V"
    }
  },
  "languages": {
    "wkn": "Wakandan",
    "eng": "English"
  }
}
```

**Response (201 Created):**

```json
{
  "id": "WKD",
  "name": {
    "common": "Wakanda",
    "official": "Kingdom of Wakanda"
  },
  "capital": ["Birnin Zana"],
  "region": "Africa",
  "createdAt": "2025-02-12T10:30:00Z",
  "message": "Country record created successfully."
}
```

<div class="tip">
<strong>Tip</strong>
When a POST request is successful, the server typically returns a 201 Created status code along with the newly created resource, including a unique identifier (ID) assigned by the server.
</div>

### Example 2: Submit Country Data with Validation

APIs often validate the data sent in POST requests. If the request body contains invalid data, the server returns an error.

**Request Body (Invalid - Missing Required Fields):**

```json
{
  "name": {
    "common": "Testland"
  }
}
```

**Response (422 Unprocessable Entity):**

```json
{
  "error": "Validation failed",
  "details": [
    {
      "field": "region",
      "message": "Region is required."
    },
    {
      "field": "capital",
      "message": "At least one capital city is required."
    }
  ]
}
```

<div class="warning">
<strong>Warning</strong>
Always validate your request body before sending a POST request. Missing required fields or incorrect data types result in validation errors that prevent the resource from being created.
</div>

---

## PUT Requests: Updating Existing Resources

A PUT request replaces an existing resource with the data provided in the request body. The request must include **all fields** for the resource, not just the fields you want to change.

### Example 3: Update a Country Record

**Endpoint:**

```
PUT https://api.example.com/v1/countries/WKD
```

**Request Headers:**

```
Content-Type: application/json
Authorization: Bearer your-api-key-here
```

**Request Body:**

```json
{
  "name": {
    "common": "Wakanda",
    "official": "United Kingdom of Wakanda"
  },
  "capital": ["Birnin Zana", "The Golden City"],
  "region": "Africa",
  "subregion": "Eastern Africa",
  "population": 6500000,
  "currencies": {
    "VBR": {
      "name": "Vibranium Credit",
      "symbol": "V"
    }
  },
  "languages": {
    "wkn": "Wakandan",
    "eng": "English",
    "xho": "Xhosa"
  }
}
```

**Response (200 OK):**

```json
{
  "id": "WKD",
  "name": {
    "common": "Wakanda",
    "official": "United Kingdom of Wakanda"
  },
  "capital": ["Birnin Zana", "The Golden City"],
  "population": 6500000,
  "updatedAt": "2025-02-12T14:45:00Z",
  "message": "Country record updated successfully."
}
```

<div class="important">
<strong>Important</strong>
PUT requests replace the entire resource. If you omit a field from the request body, that field is removed from the resource. To update only specific fields without affecting others, use a PATCH request instead.
</div>

---

## POST and PUT: Common Status Codes

| Status Code | Method | Description |
|------------|--------|-------------|
| **200 OK** | PUT | The resource was updated successfully. |
| **201 Created** | POST | The resource was created successfully. |
| **204 No Content** | PUT | The resource was updated, but no content is returned in the response. |
| **400 Bad Request** | Both | The request body is malformed or contains invalid JSON. |
| **401 Unauthorized** | Both | Authentication credentials are missing or invalid. |
| **403 Forbidden** | Both | The authenticated user does not have permission to perform this action. |
| **409 Conflict** | POST | A resource with the same identifier already exists. |
| **422 Unprocessable Entity** | Both | The request body contains valid JSON but fails validation rules. |

---

## Testing POST and PUT Requests in Postman

### Sending a POST Request

1. Open Postman and click **New** > **HTTP Request**.
2. Select **POST** from the HTTP method dropdown.
3. Enter the API endpoint URL.
4. Click the **Headers** tab and add:
   - `Content-Type`: `application/json`
   - `Authorization`: `Bearer your-api-key-here`
5. Click the **Body** tab, select **raw**, and choose **JSON** from the dropdown.
6. Enter the JSON request body.
7. Click **Send**.

### Sending a PUT Request

1. Follow the same steps as for POST, but select **PUT** from the HTTP method dropdown.
2. Include the resource identifier in the URL (for example, `/countries/WKD`).
3. Include **all fields** in the request body, even the ones that have not changed.
4. Click **Send**.

---

## Best Practices for POST and PUT Requests

- **Always include Content-Type headers** to specify the format of the request body.
- **Validate data on the client side** before sending the request to reduce server-side errors.
- **Use POST for creating resources** and **PUT for replacing resources** to follow REST conventions.
- **Handle duplicate entries** by checking if a resource already exists before sending a POST request.
- **Log API responses** for debugging and audit purposes, especially for operations that modify data.

---

# Sources

- [MDN Web Docs: HTTP POST Method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST)
- [MDN Web Docs: HTTP PUT Method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PUT)
- [RESTful API Design: POST vs PUT](https://restfulapi.net/rest-put-vs-post/)
