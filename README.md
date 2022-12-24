# Intro

## How the Ulifyi API works?&#x20;

The Ulifyi API works very easy. The Ulifyi API based on a [Express JS](https://expressjs.com/en/starter/installing.html) Backend. So this means the API is a basic HTTPS/REST API for general operations. Every user get's a [JWT (JSON Web Token)](https://jwt.io/introduction) after the login. This JWT is main point for all API's of Ulifyi. The API need the token to find the user.&#x20;

## Basic knowledge

Ulifyi is using the API Version 1. The current API base URL is:&#x20;

{% embed url="https://api.uli.fyi/api/v1" %}

| Version | Status           | Default |
| ------- | ---------------- | ------- |
| 1       | Available (Beta) | Yes     |

## API error code

What is a UEID? A UEID is a Ulifyi Error ID, a short number that will tell the server what was the error.

#### List of all UEIDs

| Error Code                                                                     | Description                                                                                                                                                   |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <pre class="language-markup"><code class="lang-markup">UEID:1000
</code></pre> | This error occurs when certain things are not specified like an API token or a UserId. Means this error means that no required information has been provided. |
| <pre class="language-markup"><code class="lang-markup">UEID:1001
</code></pre> | This error occurs when an Auth token or API token is invalid.                                                                                                 |
| <pre class="language-markup"><code class="lang-markup">UEID:1002
</code></pre> | This error occurs when a request is sent where the information does not match the previous information.                                                       |
| <pre class="language-markup"><code class="lang-markup">UEID:2000
</code></pre> | This error occurs when the specified ones are too short.                                                                                                      |
| <pre class="language-markup"><code class="lang-markup">UEID:2001
</code></pre> | This error occurs when the specified are too long.                                                                                                            |
| <pre class="language-markup"><code class="lang-markup">UEID:2002
</code></pre> | This error occurs when the specified data is not allowed.                                                                                                     |
| <pre class="language-markup"><code class="lang-markup">UEID:2003
</code></pre> | This error occurs when the specified are already in use like usernames.                                                                                       |

## Want to learn more?

If you want to learn more how the Ulifyi API works then look at this page.

{% content-ref url="getting-started.md" %}
[getting-started.md](getting-started.md)
{% endcontent-ref %}

## Want to deep dive?

Dive a little deeper and start exploring our API reference to get an idea of everything that's possible with the API:

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}
