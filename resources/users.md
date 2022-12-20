---
description: >-
  This is the users API. This API made changes on your account with your JWT
  token.
---

# Users

## Connection Service List

This list shows all services that can be requested by the connection API. The first column of the table is the service name, the second column of the table is the label how it names in the API.

<table><thead><tr><th>Connection Service</th><th>Label (Name in API)</th><th data-hidden></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td>Discord</td><td>discord</td><td></td><td></td><td></td><td></td></tr><tr><td>Spotify</td><td>spotify</td><td></td><td></td><td></td><td></td></tr></tbody></table>

## Schema of the link

In the example are **3 Links**. This schema in the example can used in the API to add **3 blocks (Links)** to your account. If you want to add more of the blocks or if you went to change the text change the text in the block the same for the URL.

{% hint style="warning" %}
**Important:** Ulifyi Free user can only use **5** of this blocks.
{% endhint %}

{% tabs %}
{% tab title="JSON Example" %}
{% code lineNumbers="true" %}
```json
[
   // Link block 1
   {
      "text": "Test",
      "url": "https://test.com"
   },
   // Link block 2
   {
      "text": "Test",
      "url": "https://test.com"
   },
   // Link block 3
   {
      "text": "Test",
      "url": "https://test.com"
   } 
]
```
{% endcode %}
{% endtab %}

{% tab title="cURL Example" %}
```powershell
curl --location --request POST 'https://api.uli.fyi/api/v1/users/@me/updateLink' \
--header 'Authorization: Bearer <your token>' \
--header 'Content-Type: application/json' \
--data-raw '[
   {
      "text": "Test",
      "url": "https://test.com"
   },
   {
      "text": "Test",
      "url": "https://test.com"
   },
   {
      "text": "Test",
      "url": "https://test.com"
   } 
]'
```
{% endtab %}
{% endtabs %}

## Get requests

{% swagger method="get" path="/users/@me" baseUrl="https://api.uli.fyi/api/v1" summary="getMe" %}
{% swagger-description %}
This API will get you, your data in JSON.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
Bearer <your JWT token>
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="User data (Output example)" %}
```javascript
{
    "username": "justinn",
    "userId": "7256107008",
    "avatar": "0",
    "email": "justin@uli.fyi",
    "name": "justinn",
    "created": "2022-12-18T18:15:10.000Z",
    "verified": "true",
    "last_change": "2022-12-18T18:15:10.000Z"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="API Error" %}
```json
{
    "msg": "An error, report this on https://github.com/Ulifyi/Bug-Reports"
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid Token" %}
```json
{
    "msg": "Invalid token"
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="User not found" %}
```json
{
    "msg": "User not found"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/users/@me/getLink" baseUrl="https://api.uli.fyi/api/v1" summary="getLink" expanded="false" %}
{% swagger-description %}
This API will get your links from your account in JSON.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
Bearer <your JWT token>
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Link data (Output Example)" %}
```json
[
    {
        "text": "Link 1",
        "url": "https://example.uli.fyi/link-1"
    },
    {
        "text": "Link 2",
        "url": "https://example.uli.fyi/link-2"
    },
    {
        "text": "Link 3",
        "url": "https://example.uli.fyi/link-3"
    }
]
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="API Error" %}
```javascript
{
    "msg": "An error, report this on https://github.com/Ulifyi/Bug-Reports"
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid Token" %}
```json
{
    "msg": "Invalid Token"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/users/@me/getConnection" baseUrl="https://api.uli.fyi/api/v1" summary="getConnection" %}
{% swagger-description %}
This API will get connection data of the services from 

[#connection-service-list](users.md#connection-service-list "mention")

.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Bearer <your JWT token>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Service" type="String" required="true" %}
\<a service from

[ this list](users.md#connection-service-list)

\>
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Connection data found" %}
```json
{
    // Data from the api of the service
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No service provided" %}
```json
{
    "msg": "No service provided"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid service" %}
```json
{
    "msg": "Invalid service"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="API Error" %}
```json
{
   "msg": "An error, report this on https://github.com/Ulifyi/Bug-Reports"
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="No connection found" %}
```json
{
    "msg": "No connection found"
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid token" %}
```json
{
    "msg": "Invalid token"
}
```
{% endswagger-response %}
{% endswagger %}

## Delete requests

{% swagger method="delete" path="/users/@me/removeConnection" baseUrl="https://api.uli.fyi/api/v1" summary="removeConnection" %}
{% swagger-description %}
This API will remove connections of the user. Use the services of 

[#connection-service-list](users.md#connection-service-list "mention")


{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
Bearer <your JWT token>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Service" type="String" required="true" %}
\<a service from

[ this list](users.md#connection-service-list)

\>
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="Connection removed!" %}
```json
{
    "msg": "Connection removed!"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid service" %}
```json
{
    "msg": "Invalid service"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No service provided" %}
```json
{
    "msg": "No service provided"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="API Error" %}
```javascript
{
    "msg": "An error, report this on https://github.com/Ulifyi/Bug-Reports"
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid token" %}
```json
{
    "msg": "Invalid token"
}
```
{% endswagger-response %}
{% endswagger %}

## Post requests

{% swagger method="post" path="/users/@me/updateLink" baseUrl="https://api.uli.fyi/api/v1" summary="updateLink" %}
{% swagger-description %}
This will update your links.&#x20;

In the body must be a `raw` input with the json content of the link.

For an example see [#schema-of-the-link](users.md#schema-of-the-link "mention")

You can see an cURL example also on [#schema-of-the-link](users.md#schema-of-the-link "mention")
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Bearer <your JWT token>
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="Link updated!" %}
```json
{
    "msg": "Link updated!"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="API Error" %}
```json
{
    "msg": "An error, report this on https://github.com/Ulifyi/Bug-Reports"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No data provided" %}
```json
{
    "msg": "No data provided"
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid Token" %}
```json
{
    "msg": "Invalid token"
}
```
{% endswagger-response %}
{% endswagger %}
