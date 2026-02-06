---
layout: default
title: Postman_APIs
---

# Testing Public APIs Using Postman

APIs are used to transfer data between two applications. To test and create accurate APIs, use applications like Postman to create an accurate JSON or XML API request with a GET, POST, PUT, or DELETE data operation. In this topic, we are testing public APIs like the REST Countries' API.

1. From the [Postman website](https://www.postman.com/), download and configure the Postman desktop application.

    <div class="note">
    <strong>Note</strong>
    While configuring the desktop application, follow the wizard instructions to create your account.
    </div>

2. On the Postman desktop application, perform the following steps:

    ![Postman UI](/images/Postman_UI.jpg)

    1. Click **New** > **HTTP Request**.

    2. From the list, select the HTTP method.

        In this example, we choose **GET**.

    3. In the HTTP Request box, enter the following API query to retrieve information about the country of Japan:

        ```
        https://restcountries.com/v3.1/name/japan
        ```
    4. Click **Send**.

    The results comprising details about the country of Japan appear in JSON format with a **200 OK** response.

    ![Postman Response](/images/postman_response.jpg)

# Sources

- [Postman documentation overview](https://learning.postman.com/docs/introduction/overview)