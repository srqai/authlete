# AuthorizationEndpoints
(*authorizationEndpoints()*)

## Overview

### Available Operations

* [failAuthRequest](#failauthrequest) - Fail Authorization Request
* [failAuthRequestForm](#failauthrequestform) - Fail Authorization Request

## failAuthRequest

This API generates a content of an error authorization response that the authorization server implementation
returns to the client application.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the authorization endpoint of the service
in order to generate an error response to the client application.

The description of the `/auth/authorization` API describes the timing when this API should be called.

The response from `/auth/authorization/fail` API has some parameters.
Among them, it is `action` parameter that the authorization server implementation should check first because
it denotes the next action that the authorization server implementation should take.
According to the value of `action`, the authorization server implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from the viewpoint of the client application, it is an error on the server side.
Therefore, the service implementation should generate a response to the client application with
HTTP status of "500 Internal Server Error". Authlete recommends `application/json` as the content type.

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

The endpoint implementation may return another different response to the client application since
"500 Internal Server Error" is not required by OAuth 2.0.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the ticket is no longer valid (deleted
or expired) and that the reason of the invalidity was probably due to the end-user's too-delayed
response to the authorization UI.

A response with HTTP status of "400 Bad Request" should be returned to the client application and
Authlete recommends `application/json` as the content type.

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

The endpoint implementation may return another different response to the client application since
"400 Bad Request" is not required by OAuth 2.0.

**LOCATION**

When the value of `action` is `LOCATION`, it means that the response to the client application must
be "302 Found" with Location header.

The parameter responseContent contains a redirect URI with (1) an authorization code, an ID token
and/or an access token (on success) or (2) an error code (on failure), so it can be used as the
value of `Location` header.

The following illustrates the response which the service implementation must generate and return
to the client application.

```
HTTP/1.1 302 Found
Location: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**FORM**

When the value of `action` is `FORM`, it means that the response to the client application must be 200 OK
with an HTML which triggers redirection by JavaScript.
This happens when the authorization request from the client application contained `response_mode=form_post`.

The value of `responseContent` is an HTML which can be used as the entity body of the response.

The following illustrates the response which the service implementation must generate and return
to the client application.

```
HTTP/1.1 200 OK
Content-Type: text/html;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.*;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthAuthorizationFailApiResponse res = sdk.authorizationEndpoints().failAuthRequest()
                .serviceId("<id>")
                .requestBody(AuthAuthorizationFailApiRequestBody.builder()
                    .ticket("qA7wGybwArICpbUSutrf5Xc9-i1fHE0ySOHxR1eBoBQ")
                    .reason(AuthAuthorizationFailApiReason.NOT_AUTHENTICATED)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                           | *String*                                                                                              | :heavy_check_mark:                                                                                    | A service ID.                                                                                         |
| `requestBody`                                                                                         | [AuthAuthorizationFailApiRequestBody](../../models/operations/AuthAuthorizationFailApiRequestBody.md) | :heavy_check_mark:                                                                                    | N/A                                                                                                   |

### Response

**[AuthAuthorizationFailApiResponse](../../models/operations/AuthAuthorizationFailApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## failAuthRequestForm

This API generates a content of an error authorization response that the authorization server implementation
returns to the client application.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the authorization endpoint of the service
in order to generate an error response to the client application.

The description of the `/auth/authorization` API describes the timing when this API should be called.

The response from `/auth/authorization/fail` API has some parameters.
Among them, it is `action` parameter that the authorization server implementation should check first because
it denotes the next action that the authorization server implementation should take.
According to the value of `action`, the authorization server implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from the viewpoint of the client application, it is an error on the server side.
Therefore, the service implementation should generate a response to the client application with
HTTP status of "500 Internal Server Error". Authlete recommends `application/json` as the content type.

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

The endpoint implementation may return another different response to the client application since
"500 Internal Server Error" is not required by OAuth 2.0.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the ticket is no longer valid (deleted
or expired) and that the reason of the invalidity was probably due to the end-user's too-delayed
response to the authorization UI.

A response with HTTP status of "400 Bad Request" should be returned to the client application and
Authlete recommends `application/json` as the content type.

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

The endpoint implementation may return another different response to the client application since
"400 Bad Request" is not required by OAuth 2.0.

**LOCATION**

When the value of `action` is `LOCATION`, it means that the response to the client application must
be "302 Found" with Location header.

The parameter responseContent contains a redirect URI with (1) an authorization code, an ID token
and/or an access token (on success) or (2) an error code (on failure), so it can be used as the
value of `Location` header.

The following illustrates the response which the service implementation must generate and return
to the client application.

```
HTTP/1.1 302 Found
Location: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**FORM**

When the value of `action` is `FORM`, it means that the response to the client application must be 200 OK
with an HTML which triggers redirection by JavaScript.
This happens when the authorization request from the client application contained `response_mode=form_post`.

The value of `responseContent` is an HTML which can be used as the entity body of the response.

The following illustrates the response which the service implementation must generate and return
to the client application.

```
HTTP/1.1 200 OK
Content-Type: text/html;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.AuthAuthorizationFailApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthAuthorizationFailApiFormResponse res = sdk.authorizationEndpoints().failAuthRequestForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1auth1authorization1failPostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1auth1authorization1failPostRequestBodyContentApplication1jsonSchema.builder()
                    .ticket("<value>")
                    .reason(1api1Percent7BserviceIdPercent7D1auth1authorization1failPostRequestBodyContentApplication1jsonSchemaReason.NOT_AUTHENTICATED)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                 | Type                                                                                                                                                                                                                                      | Required                                                                                                                                                                                                                                  | Description                                                                                                                                                                                                                               |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                                               | *String*                                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                                        | A service ID.                                                                                                                                                                                                                             |
| `1api1Percent7BserviceIdPercent7D1auth1authorization1failPostRequestBodyContentApplication1jsonSchema`                                                                                                                                    | [1api1Percent7BserviceIdPercent7D1auth1authorization1failPostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1auth1authorization1failPostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                                        | N/A                                                                                                                                                                                                                                       |

### Response

**[AuthAuthorizationFailApiFormResponse](../../models/operations/AuthAuthorizationFailApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |