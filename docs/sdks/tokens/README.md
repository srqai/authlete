# Tokens
(*tokens()*)

## Overview

### Available Operations

* [fail](#fail) - Fail Token Request
* [failForm](#failform) - Fail Token Request
* [revoke](#revoke) - Process Revocation Request
* [revokeForm](#revokeform) - Process Revocation Request
* [reissueId](#reissueid) - Reissue ID Token
* [list](#list) - List Issued Tokens
* [create](#create) - Create Access Token
* [createForm](#createform) - Create Access Token
* [update](#update) - Update Access Token
* [updateForm](#updateform) - Update Access Token

## fail

This API generates a content of an error token response that the authorization server implementation
returns to the client application.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the token endpoint of the service
in order to generate an error response to the client application.

The description of the `/auth/token` API describes the timing when this API should be called. See
the description for the case of `action=PASSWORD`.

The response from `/auth/token/fail` API has some parameters. Among them, it is `action` parameter
that the authorization server implementation should check first because it denotes the next action
that the authorization server implementation should take. According to the value of `action`, the
authorization server implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from the viewpoint of the client application, it is an error on the server side.
Therefore, the service implementation should generate a response to the client application with
HTTP status of "500 Internal Server Error".

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client application
since "500 Internal Server Error" is not required by OAuth 2.0.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that Authlete's `/auth/token/fail` API successfully
generated an error response for the client application.

The HTTP status of the response returned to the client application must be "400 Bad Request" and
the content type must be `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_fail_api" method="post" path="/api/{serviceId}/auth/token/fail" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.*;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenFailApiResponse res = sdk.tokens().fail()
                .serviceId("<id>")
                .requestBody(AuthTokenFailApiRequestBody.builder()
                    .ticket("83BNqKIhGMyrkvop_7jQjv2Z1612LNdGSQKkvkrf47c")
                    .reason(AuthTokenFailApiReason.INVALID_RESOURCE_OWNER_CREDENTIALS)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `serviceId`                                                                           | *String*                                                                              | :heavy_check_mark:                                                                    | A service ID.                                                                         |
| `requestBody`                                                                         | [AuthTokenFailApiRequestBody](../../models/operations/AuthTokenFailApiRequestBody.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `serverURL`                                                                           | *String*                                                                              | :heavy_minus_sign:                                                                    | An optional server URL to use.                                                        |

### Response

**[AuthTokenFailApiResponse](../../models/operations/AuthTokenFailApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## failForm

This API generates a content of an error token response that the authorization server implementation
returns to the client application.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the token endpoint of the service
in order to generate an error response to the client application.

The description of the `/auth/token` API describes the timing when this API should be called. See
the description for the case of `action=PASSWORD`.

The response from `/auth/token/fail` API has some parameters. Among them, it is `action` parameter
that the authorization server implementation should check first because it denotes the next action
that the authorization server implementation should take. According to the value of `action`, the
authorization server implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from the viewpoint of the client application, it is an error on the server side.
Therefore, the service implementation should generate a response to the client application with
HTTP status of "500 Internal Server Error".

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client application
since "500 Internal Server Error" is not required by OAuth 2.0.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that Authlete's `/auth/token/fail` API successfully
generated an error response for the client application.

The HTTP status of the response returned to the client application must be "400 Bad Request" and
the content type must be `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_fail_api_form" method="post" path="/api/{serviceId}/auth/token/fail" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthTokenFailApiFormRequestBody;
import org.openapis.openapi.models.operations.AuthTokenFailApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenFailApiFormResponse res = sdk.tokens().failForm()
                .serviceId("<id>")
                .requestBody(AuthTokenFailApiFormRequestBody.builder()
                    .clientLocked(true)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                   | *String*                                                                                      | :heavy_check_mark:                                                                            | A service ID.                                                                                 |
| `requestBody`                                                                                 | [AuthTokenFailApiFormRequestBody](../../models/operations/AuthTokenFailApiFormRequestBody.md) | :heavy_check_mark:                                                                            | N/A                                                                                           |
| `serverURL`                                                                                   | *String*                                                                                      | :heavy_minus_sign:                                                                            | An optional server URL to use.                                                                |

### Response

**[AuthTokenFailApiFormResponse](../../models/operations/AuthTokenFailApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## revoke

This API revokes access tokens and refresh tokens.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the revocation endpoint ([RFC
7009](tools.ietf.org/html/rfc7009)) of the authorization server implementation in order to revoke
access tokens and refresh tokens.

The response from `/auth/revocation` API has some parameters. Among them, it is `action` parameter
that the authorization server implementation should check first because it denotes the next action
that the authorization server implementation should take. According to the value of `action`, the
authorization server implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete.
In either case, from the viewpoint of the client application, it is an error on the server side.
Therefore, the service implementation should generate a response to the client application with
HTTP status of "500 Internal Server Error".

The value of `responseContent` is a JSON string which describes the error, so it can be
used as the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**INVALID_CLIENT**

When the value of `action` is `INVALID_CLIENT`, it means that authentication of the client failed.
In this case, the HTTP status of the response to the client application is either "400 Bad Request"
or "401 Unauthorized". The description about `invalid_client` shown below is an excerpt from [RFC
6749](https://datatracker.ietf.org/doc/html/rfc6749).

`invalid_client`

> Client authentication failed (e.g., unknown client, no client authentication included, or unsupported
authentication method). The authorization server MAY return an HTTP 401 (Unauthorized) status code
to indicate which HTTP authentication schemes are supported. If the client attempted to authenticate
via the `Authorization` request header field, the authorization server MUST respond with an HTTP
401 (Unauthorized) status code and include the `WWW-Authenticate` response header field matching
the authentication scheme used by the client.

In either case, the value of `responseContent` is a JSON string which can be used as the entity
body of the response to the client application.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

<br>

```
HTTP/1.1 401 Unauthorized
WWW-Authenticate: {challenge}
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
is invalid.

The HTTP status of the response returned to the client application must be "400 Bad Request" and
the content type must be `application/json`. [RFC 7009](https://datatracker.ietf.org/doc/html/rfc7009),
[2.2.1. Error Respons](https://datatracker.ietf.org/doc/html/rfc7009#section-2.2.1) states "The
error presentation conforms to the definition in [Section 5.2](https://datatracker.ietf.org/doc/html/rfc6749#section-5.2)
of [[RFC 6749](https://datatracker.ietf.org/doc/html/rfc6749)]."

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**OK**

When the value of `action` is `OK`, it means that the request from the client application is valid
and the presented token has been revoked successfully or if the client submitted an invalid token.
Note that invalid tokens do not cause an error. See [2.2. Revocation Response](https://datatracker.ietf.org/doc/html/rfc7009#section-2.2) for details.

The HTTP status of the response returned to the client application must be 200 OK.

If the original request from the client application contains callback request parameter and its
value is not empty, the content type should be `application/javascript` and the content should be
a JavaScript snippet for JSONP.

The value of `responseContent` is JavaScript snippet if the original request from the client application
contains callback request parameter and its value is not empty. Otherwise, the value of `responseContent`
is `null`.

```
HTTP/1.1 200 OK
Content-Type: application/javascript
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_revocation_api" method="post" path="/api/{serviceId}/auth/revocation" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthRevocationApiRequestBody;
import org.openapis.openapi.models.operations.AuthRevocationApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthRevocationApiResponse res = sdk.tokens().revoke()
                .serviceId("<id>")
                .requestBody(AuthRevocationApiRequestBody.builder()
                    .parameters("VFGsNK-5sXiqterdaR7b5QbRX9VTwVCQB87jbr2_xAI&token_type_hint=access_token")
                    .clientId("26478243745571")
                    .clientSecret("gXz97ISgLs4HuXwOZWch8GEmgL4YMvUJwu3er_kDVVGcA0UOhA9avLPbEmoeZdagi9yC_-tEiT2BdRyH9dbrQQ")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `serviceId`                                                                             | *String*                                                                                | :heavy_check_mark:                                                                      | A service ID.                                                                           |
| `requestBody`                                                                           | [AuthRevocationApiRequestBody](../../models/operations/AuthRevocationApiRequestBody.md) | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `serverURL`                                                                             | *String*                                                                                | :heavy_minus_sign:                                                                      | An optional server URL to use.                                                          |

### Response

**[AuthRevocationApiResponse](../../models/operations/AuthRevocationApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## revokeForm

This API revokes access tokens and refresh tokens.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the revocation endpoint ([RFC
7009](tools.ietf.org/html/rfc7009)) of the authorization server implementation in order to revoke
access tokens and refresh tokens.

The response from `/auth/revocation` API has some parameters. Among them, it is `action` parameter
that the authorization server implementation should check first because it denotes the next action
that the authorization server implementation should take. According to the value of `action`, the
authorization server implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete.
In either case, from the viewpoint of the client application, it is an error on the server side.
Therefore, the service implementation should generate a response to the client application with
HTTP status of "500 Internal Server Error".

The value of `responseContent` is a JSON string which describes the error, so it can be
used as the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**INVALID_CLIENT**

When the value of `action` is `INVALID_CLIENT`, it means that authentication of the client failed.
In this case, the HTTP status of the response to the client application is either "400 Bad Request"
or "401 Unauthorized". The description about `invalid_client` shown below is an excerpt from [RFC
6749](https://datatracker.ietf.org/doc/html/rfc6749).

`invalid_client`

> Client authentication failed (e.g., unknown client, no client authentication included, or unsupported
authentication method). The authorization server MAY return an HTTP 401 (Unauthorized) status code
to indicate which HTTP authentication schemes are supported. If the client attempted to authenticate
via the `Authorization` request header field, the authorization server MUST respond with an HTTP
401 (Unauthorized) status code and include the `WWW-Authenticate` response header field matching
the authentication scheme used by the client.

In either case, the value of `responseContent` is a JSON string which can be used as the entity
body of the response to the client application.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

<br>

```
HTTP/1.1 401 Unauthorized
WWW-Authenticate: {challenge}
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
is invalid.

The HTTP status of the response returned to the client application must be "400 Bad Request" and
the content type must be `application/json`. [RFC 7009](https://datatracker.ietf.org/doc/html/rfc7009),
[2.2.1. Error Respons](https://datatracker.ietf.org/doc/html/rfc7009#section-2.2.1) states "The
error presentation conforms to the definition in [Section 5.2](https://datatracker.ietf.org/doc/html/rfc6749#section-5.2)
of [[RFC 6749](https://datatracker.ietf.org/doc/html/rfc6749)]."

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**OK**

When the value of `action` is `OK`, it means that the request from the client application is valid
and the presented token has been revoked successfully or if the client submitted an invalid token.
Note that invalid tokens do not cause an error. See [2.2. Revocation Response](https://datatracker.ietf.org/doc/html/rfc7009#section-2.2) for details.

The HTTP status of the response returned to the client application must be 200 OK.

If the original request from the client application contains callback request parameter and its
value is not empty, the content type should be `application/javascript` and the content should be
a JavaScript snippet for JSONP.

The value of `responseContent` is JavaScript snippet if the original request from the client application
contains callback request parameter and its value is not empty. Otherwise, the value of `responseContent`
is `null`.

```
HTTP/1.1 200 OK
Content-Type: application/javascript
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_revocation_api_form" method="post" path="/api/{serviceId}/auth/revocation" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthRevocationApiFormRequestBody;
import org.openapis.openapi.models.operations.AuthRevocationApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthRevocationApiFormResponse res = sdk.tokens().revokeForm()
                .serviceId("<id>")
                .requestBody(AuthRevocationApiFormRequestBody.builder()
                    .clientLocked(false)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                     | *String*                                                                                        | :heavy_check_mark:                                                                              | A service ID.                                                                                   |
| `requestBody`                                                                                   | [AuthRevocationApiFormRequestBody](../../models/operations/AuthRevocationApiFormRequestBody.md) | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `serverURL`                                                                                     | *String*                                                                                        | :heavy_minus_sign:                                                                              | An optional server URL to use.                                                                  |

### Response

**[AuthRevocationApiFormResponse](../../models/operations/AuthRevocationApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## reissueId

The API is expected to be called only when the value of the `action`
parameter in a response from the `/auth/token` API is [ID_TOKEN_REISSUABLE](https://authlete.github.io/authlete-java-common/com/authlete/common/dto/TokenResponse.Action.html#ID_TOKEN_REISSUABLE). The purpose
of the `/idtoken/reissue` API is to generate a token response that
includes a new ID token together with a new access token and a refresh
token.


### Example Usage

<!-- UsageSnippet language="java" operationID="idtoken_reissue_api" method="post" path="/api/{serviceId}/idtoken/reissue" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.IdtokenReissueApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        IdtokenReissueApiResponse res = sdk.tokens().reissueId()
                .serviceId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                        | *String*                                                                                           | :heavy_check_mark:                                                                                 | A service ID.                                                                                      |
| `requestBody`                                                                                      | [Optional\<IdtokenReissueApiRequestBody>](../../models/operations/IdtokenReissueApiRequestBody.md) | :heavy_minus_sign:                                                                                 | N/A                                                                                                |
| `serverURL`                                                                                        | *String*                                                                                           | :heavy_minus_sign:                                                                                 | An optional server URL to use.                                                                     |

### Response

**[IdtokenReissueApiResponse](../../models/operations/IdtokenReissueApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## list

Get the list of access tokens that are associated with the service.


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_get_list_api" method="get" path="/api/{serviceId}/auth/token/get/list" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthTokenGetListApiRequest;
import org.openapis.openapi.models.operations.AuthTokenGetListApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenGetListApiRequest req = AuthTokenGetListApiRequest.builder()
                .serviceId("<id>")
                .build();

        AuthTokenGetListApiResponse res = sdk.tokens().list()
                .request(req)
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `request`                                                                           | [AuthTokenGetListApiRequest](../../models/operations/AuthTokenGetListApiRequest.md) | :heavy_check_mark:                                                                  | The request object to use for the request.                                          |
| `serverURL`                                                                         | *String*                                                                            | :heavy_minus_sign:                                                                  | An optional server URL to use.                                                      |

### Response

**[AuthTokenGetListApiResponse](../../models/operations/AuthTokenGetListApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## create

Create an access token.


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_create_api" method="post" path="/api/{serviceId}/auth/token/create" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.*;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenCreateApiResponse res = sdk.tokens().create()
                .serviceId("<id>")
                .requestBody(AuthTokenCreateApiRequestBody.builder()
                    .grantType(AuthTokenCreateApiGrantType.AUTHORIZATION_CODE)
                    .clientId(26888344961664L)
                    .subject("john")
                    .scopes(List.of(
                        "history.read",
                        "timeline.read"))
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `serviceId`                                                                               | *String*                                                                                  | :heavy_check_mark:                                                                        | A service ID.                                                                             |
| `requestBody`                                                                             | [AuthTokenCreateApiRequestBody](../../models/operations/AuthTokenCreateApiRequestBody.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |
| `serverURL`                                                                               | *String*                                                                                  | :heavy_minus_sign:                                                                        | An optional server URL to use.                                                            |

### Response

**[AuthTokenCreateApiResponse](../../models/operations/AuthTokenCreateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## createForm

Create an access token.


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_create_api_form" method="post" path="/api/{serviceId}/auth/token/create" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthTokenCreateApiFormRequestBody;
import org.openapis.openapi.models.operations.AuthTokenCreateApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenCreateApiFormResponse res = sdk.tokens().createForm()
                .serviceId("<id>")
                .requestBody(AuthTokenCreateApiFormRequestBody.builder()
                    .clientLocked(false)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                       | *String*                                                                                          | :heavy_check_mark:                                                                                | A service ID.                                                                                     |
| `requestBody`                                                                                     | [AuthTokenCreateApiFormRequestBody](../../models/operations/AuthTokenCreateApiFormRequestBody.md) | :heavy_check_mark:                                                                                | N/A                                                                                               |
| `serverURL`                                                                                       | *String*                                                                                          | :heavy_minus_sign:                                                                                | An optional server URL to use.                                                                    |

### Response

**[AuthTokenCreateApiFormResponse](../../models/operations/AuthTokenCreateApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## update

Update an access token.


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_update_api" method="post" path="/api/{serviceId}/auth/token/update" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthTokenUpdateApiRequestBody;
import org.openapis.openapi.models.operations.AuthTokenUpdateApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenUpdateApiResponse res = sdk.tokens().update()
                .serviceId("<id>")
                .requestBody(AuthTokenUpdateApiRequestBody.builder()
                    .accessToken("Z5a40U6dWvw2gMoCOAFbZcM85q4HC0Z--0YKD9-Nf6Q")
                    .scopes(List.of(
                        "history.read"))
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `serviceId`                                                                               | *String*                                                                                  | :heavy_check_mark:                                                                        | A service ID.                                                                             |
| `requestBody`                                                                             | [AuthTokenUpdateApiRequestBody](../../models/operations/AuthTokenUpdateApiRequestBody.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |
| `serverURL`                                                                               | *String*                                                                                  | :heavy_minus_sign:                                                                        | An optional server URL to use.                                                            |

### Response

**[AuthTokenUpdateApiResponse](../../models/operations/AuthTokenUpdateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateForm

Update an access token.


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_update_api_form" method="post" path="/api/{serviceId}/auth/token/update" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthTokenUpdateApiFormRequestBody;
import org.openapis.openapi.models.operations.AuthTokenUpdateApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenUpdateApiFormResponse res = sdk.tokens().updateForm()
                .serviceId("<id>")
                .requestBody(AuthTokenUpdateApiFormRequestBody.builder()
                    .clientLocked(true)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                       | *String*                                                                                          | :heavy_check_mark:                                                                                | A service ID.                                                                                     |
| `requestBody`                                                                                     | [AuthTokenUpdateApiFormRequestBody](../../models/operations/AuthTokenUpdateApiFormRequestBody.md) | :heavy_check_mark:                                                                                | N/A                                                                                               |
| `serverURL`                                                                                       | *String*                                                                                          | :heavy_minus_sign:                                                                                | An optional server URL to use.                                                                    |

### Response

**[AuthTokenUpdateApiFormResponse](../../models/operations/AuthTokenUpdateApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |