---
layout: default
title: Postman_APIs
---

<div class="reader-note">
<strong>Note to the Reader</strong>
This page lists the steps to integrate two applications using Postman. I would change the title, introduction, and conclusion to better communicate the purpose of the procedure on this page.
</div>

# Using APIs to Integrate Applications and Websites

APIs are the basis on which the entire world’s applications talk to each other and enable people to seamlessly perform actions on the internet.

As a web developer, you will use APIs to connect standalone applications when information and processes must flow between them. Using APIs enables you to work securely without exposing code and protected data, while also bridging the gap between different stand-alone applications.

Several API clients are available for development and testing, such as Postman. Applications such as Postman act as clients communicating with the API server during a website or application testing phase, so you can ensure the endpoint is working correctly and returning the required data. You must test the API to ensure that the following requirements are met:

- The correct headers, credentials, and parameters are included in the API request.

- The required data is received via the API response.

- The response is in the format you desire.

For example, a weather app on your phone would connect with the National Weather Service to display real-time weather data. In this case, the weather application connects to the National Weather Service API to provide real-time weather updates based on your selection.

To connect an application or a website to an API service, web developers perform the following steps:

1. Identify the API service to fetch data from.  
    
    In this example, fetch data from the Countries’ REST API, which is a public API that does not require authentication credentials.

2. On the website, create dynamic fields with JavaScript, and note the API calls from the website page.

3. To test the API calls from an application like Postman, perform the following steps:

    1. From the [Postman website](https://www.postman.com/), download and configure the Postman desktop application.

    <div class="note">
    <strong>Note</strong>
    While configuring the desktop application, follow the wizard instructions to create your account.
    </div>

    2. Test the API and ensure that the correct headers, credentials, and parameters are sent with the API request, that the required data is returned in the API response, and that the response is in the desired format.

    3. Click **New** > **HTTP Request**.

    4.  From the list, select the HTTP method.

        In this example, we choose **GET**.

    5. In the HTTP Request box, enter the following API query to retrieve information about the country of Japan:

        ```
        https://restcountries.com/v3.1/name/japan
        ```

        ![Postman UI](/images/Postman_UI.jpg)

    6. Click Send.

        The results, including details about Japan, are returned in JSON format with a **200 OK** response

        ![Postman Response](/images/postman_response.jpg)

    7. If the results are not satisfactory, modify the API call parameters and inputs.

4. Reuse the modified API calls in the website’s JavaScript.

5. Design the website so that the user inputs in the dynamic fields match the inputs in the API query.

In conclusion, while it may seem that data travels seamlessly between websites, you must take additional steps, such as testing APIs, to ensure accurate integration between applications.

# Sources

- [Postman documentation overview](https://learning.postman.com/docs/introduction/overview)