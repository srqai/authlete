# DynamicClientRegistration
(*dynamicClientRegistration()*)

## Overview

### Available Operations

* [delete](#delete) - Delete Client
* [deleteForm](#deleteform) - Delete Client

## delete

Delete a dynamically registered client. This API is supposed to be used to implement a client
registration management endpoint that complies with [RFC 7592](https://datatracker.ietf.org/doc/html/rfc7592)
(OAuth 2.0 Dynamic Registration Management).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the client registration
management endpoint of the authorization server. The authorization server implementation should
retrieve the value of `action` from the response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client or developer, it is an error on the server side.
Therefore, the authorization server implementation should generate a response with "500 Internal
Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client or developer since
"500 Internal Server Error" is not required by the specification.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client or developer
was wrong.

The authorization server implementation should generate a response with "400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the registration access token used by
the client configuration request (RFC 7592) is invalid, or the client application which the token
is tied to does not exist any longer or is invalid.

The HTTP status of the response returned to the client application must be "401 Unauthorized" and
the content type must be `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the endpoint implementation should generate and return
to the client application.

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

NOTE: The `UNAUTHORIZED` value was added in October, 2021. See the description of
`Service.unauthorizedOnClientConfigSupported` for details.

**DELETED**

When the value of `action` is `DELETED`, it means that the request from the client or developer is
valid.

The authorization server implementation should generate a response to the client or developer with
"204 No Content".

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 204 No Content
Cache-Control: no-store
Pragma: no-cache
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="client_registration_delete_api" method="post" path="/api/{serviceId}/client/registration/delete" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientRegistrationDeleteApiRequestBody;
import org.openapis.openapi.models.operations.ClientRegistrationDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientRegistrationDeleteApiResponse res = sdk.dynamicClientRegistration().delete()
                .serviceId("<id>")
                .requestBody(ClientRegistrationDeleteApiRequestBody.builder()
                    .clientId("26837717140341")
                    .token("qs4Tu5TV7qqDYT93bFs6ISyhTByMF9o-54GY4JU5vTA")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                   | Type                                                                                                        | Required                                                                                                    | Description                                                                                                 |
| ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                 | *String*                                                                                                    | :heavy_check_mark:                                                                                          | A service ID.                                                                                               |
| `requestBody`                                                                                               | [ClientRegistrationDeleteApiRequestBody](../../models/operations/ClientRegistrationDeleteApiRequestBody.md) | :heavy_check_mark:                                                                                          | N/A                                                                                                         |
| `serverURL`                                                                                                 | *String*                                                                                                    | :heavy_minus_sign:                                                                                          | An optional server URL to use.                                                                              |

### Response

**[ClientRegistrationDeleteApiResponse](../../models/operations/ClientRegistrationDeleteApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## deleteForm

Delete a dynamically registered client. This API is supposed to be used to implement a client
registration management endpoint that complies with [RFC 7592](https://datatracker.ietf.org/doc/html/rfc7592)
(OAuth 2.0 Dynamic Registration Management).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the client registration
management endpoint of the authorization server. The authorization server implementation should
retrieve the value of `action` from the response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client or developer, it is an error on the server side.
Therefore, the authorization server implementation should generate a response with "500 Internal
Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client or developer since
"500 Internal Server Error" is not required by the specification.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client or developer
was wrong.

The authorization server implementation should generate a response with "400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the registration access token used by
the client configuration request (RFC 7592) is invalid, or the client application which the token
is tied to does not exist any longer or is invalid.

The HTTP status of the response returned to the client application must be "401 Unauthorized" and
the content type must be `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the endpoint implementation should generate and return
to the client application.

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

NOTE: The `UNAUTHORIZED` value was added in October, 2021. See the description of
`Service.unauthorizedOnClientConfigSupported` for details.

**DELETED**

When the value of `action` is `DELETED`, it means that the request from the client or developer is
valid.

The authorization server implementation should generate a response to the client or developer with
"204 No Content".

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 204 No Content
Cache-Control: no-store
Pragma: no-cache
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="client_registration_delete_api_form" method="post" path="/api/{serviceId}/client/registration/delete" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientRegistrationDeleteApiFormRequestBody;
import org.openapis.openapi.models.operations.ClientRegistrationDeleteApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientRegistrationDeleteApiFormResponse res = sdk.dynamicClientRegistration().deleteForm()
                .serviceId("<id>")
                .requestBody(ClientRegistrationDeleteApiFormRequestBody.builder()
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

| Parameter                                                                                                           | Type                                                                                                                | Required                                                                                                            | Description                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                         | *String*                                                                                                            | :heavy_check_mark:                                                                                                  | A service ID.                                                                                                       |
| `requestBody`                                                                                                       | [ClientRegistrationDeleteApiFormRequestBody](../../models/operations/ClientRegistrationDeleteApiFormRequestBody.md) | :heavy_check_mark:                                                                                                  | N/A                                                                                                                 |
| `serverURL`                                                                                                         | *String*                                                                                                            | :heavy_minus_sign:                                                                                                  | An optional server URL to use.                                                                                      |

### Response

**[ClientRegistrationDeleteApiFormResponse](../../models/operations/ClientRegistrationDeleteApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |