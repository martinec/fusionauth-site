---
layout: article
title: Webapp OAuth login using resource owner password credentials grant
subtitle: Using sessions and refresh tokens
description: An explanation of webapp login using a native login form that submits to the application backend and uses server-side sessions plus refresh tokens in cookies
image: articles/login-types-share-image.jpg
---

{% capture intro %}
{% include_relative _native-intro.md %}
{% endcapture %}
{{ intro | markdownify }}

## Diagram

**Legend**

```text
() --> indicate request/response bodies
{} --> indicate request parameters
[] --> indicate cookies
```

{% plantuml _diagrams/logins/webapp/oauth-resource-owners-grant-sessions-refresh-tokens-cookies.plantuml %}

## Explanation

{% capture steps %}
{% include_relative _oauth-password-login-store.md %}
{% include_relative _create-session.md %}
{% include_relative _shopping-cart-session-refresh-redirect.md %}
{% include_relative _shopping-cart-session-refresh-load.md %}
{% include_relative _shopping-cart-session-refresh-refresh.md %}
{% include_relative _shopping-cart-session-refresh-relogin.md %}
{% include_relative _oauth-password-login-forums.md %}
{% include_relative _create-session.md %}
{% include_relative _forums-session-refresh-redirect.md %}
{% include_relative _forums-session-refresh-load.md %}
{% include_relative _stolen-session-refresh-token.md %}
{% include_relative _stolen-session-id.md %}
{% endcapture %}
{{ steps | markdownify }}

## Security considerations

This workflow is one of the more secure methods of authenticating users. One downside is that the application backend receives passwords from the browser. While this isn't an issue if TLS is used and the passwords are not stored by the application backend, developers that do not want to be part of the password chain of responsibility should consider other workflows.

## APIs used

Here are the FusionAuth APIs used in this example:

* [/oauth2/token (grant)](/docs/v1/tech/oauth/endpoints#resource-owner-credentials-grant-request)
* [/api/jwt/refresh](/docs/v1/tech/apis/jwt#refresh-a-jwt)
* [/oauth2/token](/docs/v1/tech/oauth/endpoints#refresh-token-grant-request)

[_View All Types_](/articles/logins/types-of-logins-authentication-workflows)
