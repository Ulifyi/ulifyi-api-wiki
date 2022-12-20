---
description: Learn fast how the Ulifyi API works.
---

# Getting started

{% hint style="danger" %}
**Beta:** The Version 1 of the API is currently in beta. Functions might be not working or making errors.&#x20;
{% endhint %}

## How to start?

The first your a need a user token. You need to call the login API to get a **JWT token** with the life time of **7 days**. In this token are the information's of the user. Like this:

```json
{
  "username": "justin",
  "userId": "7256107008",
  "email": "justin@uli.fyi",
  "name": "justin",
  "created": "2022-12-04T23:00:00.000Z",
  "verified": "true",
  "iat": 1671386559,
  "exp": 1671991359
}
```

with this information's the API knows who you are. But for an API call you need the JWT token. This will you get on this API.

{% swagger method="post" path="/login" baseUrl="https://api.uli.fyi/api/v1" summary="Ulifyi API Login" %}
{% swagger-description %}
This API will get you a JWT token by entering username and password in the body of the request.
{% endswagger-description %}

{% swagger-parameter in="body" name="username" type="String" required="true" %}
\<your username of your Ulifyi Account>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="String" required="true" %}
\<your password of your Ulifyi Account>
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Logged in!" %}
```json
{
    "msg": "Logged in!",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="API Error" %}
<pre class="language-json"><code class="lang-json"><strong>{
</strong>    "msg": "An error, report this on https://github.com/Ulifyi/Bug-Reports"
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Username or password is incorrect!" %}
```json
{
    "msg": "Username or password is incorrect!"
}
```
{% endswagger-response %}
{% endswagger %}

This is the base of the Ulifyi Login. Now you have your token. But what can you do with the token?

## What can you do with the token?

Now you have a token that will **expire on 7 days**. But what can you do with them? That's very easy. You can update you account or get data from your account with this API's.

{% content-ref url="resources/users.md" %}
[users.md](resources/users.md)
{% endcontent-ref %}

