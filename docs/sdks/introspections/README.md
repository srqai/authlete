# Introspections
(*introspections()*)

## Overview

### Available Operations

* [process](#process) - Process OAuth 2.0 Introspection Request
* [processForm](#processform) - Process OAuth 2.0 Introspection Request

## process

This API exists to help your authorization server provide its own introspection API which complies
with [RFC 7662](https://tools.ietf.org/html/rfc7662) (OAuth 2.0 Token Introspection).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementations of the introspection endpoint
of your service. The authorization server implementation should retrieve the value of `action` from
the response and take the following steps according to the value.

In general, a client application accesses a protected resource endpoint of a service with an access
token, and the implementation of the endpoint checks whether the presented access token has enough
privileges (= scopes) to access the protected resource before returning the protected resource to
the client application. To achieve this flow, the endpoint implementation has to know detailed
information about the access token. Authlete `/auth/introspection` API can be used to get such information.

The response from `/auth/introspection` API has some parameters. Among them, it is `action` parameter
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
as the entity body of the response if you want. Note that, however, [RFC 7662](https://datatracker.ietf.org/doc/html/rfc7662) does not mention anything about the response
body of error responses.

The following illustrates an example response which the introspection endpoint of the authorization
server implementation generates and returns to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{responseContent}
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
is invalid. This happens when the request from the client did not include the token request parameter.
See "[2.1. Introspection Request](https://datatracker.ietf.org/doc/html/rfc7662#section-2.1)" in
RFC 7662 for details about requirements for introspection requests.

The HTTP status of the response returned to the client application should be "400 Bad Request".

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response if you want. Note that, however, [RFC 7662](https://datatracker.ietf.org/doc/html/rfc7662)
does not mention anything about the response body of error responses.

The following illustrates an example response which the introspection endpoint of the authorization
server implementation generates and returns to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{responseContent}
```

**OK**

When the value of `action` is `OK`, the request from the client application is valid.

The HTTP status of the response returned to the client application must be "200 OK" and its content
type must be `application/json`.

The value of `responseContent` is a JSON string which complies with the introspection response
defined in "2.2. Introspection Response" in RFC7662.

The following illustrates the response which the introspection endpoint of your authorization server
implementation should generate and return to the client application.

```
HTTP/1.1 200 OK
Content-Type: application/json

{responseContent}
```

Note that RFC 7662 says _"To prevent token scanning attacks, **the endpoint MUST also require some
form of authorization to access this endpoint**"_. This means that you have to protect your introspection
endpoint in some way or other. Authlete does not care about how your introspection endpoint is protected.
In most cases, as mentioned in RFC 7662, "401 Unauthorized" is a proper response when an introspection
request does not satisfy authorization requirements imposed by your introspection endpoint.

</details>


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.AuthIntrospectionStandardApiRequestBody;
import org.openapis.openapi.models.operations.AuthIntrospectionStandardApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthIntrospectionStandardApiResponse res = sdk.introspections().process()
                .serviceId("<id>")
                .requestBody(AuthIntrospectionStandardApiRequestBody.builder()
                    .parameters("token=VFGsNK-5sXiqterdaR7b5QbRX9VTwVCQB87jbr2_xAI&token_type_hint=access_token")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                     | Type                                                                                                          | Required                                                                                                      | Description                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                   | *String*                                                                                                      | :heavy_check_mark:                                                                                            | A service ID.                                                                                                 |
| `requestBody`                                                                                                 | [AuthIntrospectionStandardApiRequestBody](../../models/operations/AuthIntrospectionStandardApiRequestBody.md) | :heavy_check_mark:                                                                                            | N/A                                                                                                           |

### Response

**[AuthIntrospectionStandardApiResponse](../../models/operations/AuthIntrospectionStandardApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## processForm

This API exists to help your authorization server provide its own introspection API which complies
with [RFC 7662](https://tools.ietf.org/html/rfc7662) (OAuth 2.0 Token Introspection).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementations of the introspection endpoint
of your service. The authorization server implementation should retrieve the value of `action` from
the response and take the following steps according to the value.

In general, a client application accesses a protected resource endpoint of a service with an access
token, and the implementation of the endpoint checks whether the presented access token has enough
privileges (= scopes) to access the protected resource before returning the protected resource to
the client application. To achieve this flow, the endpoint implementation has to know detailed
information about the access token. Authlete `/auth/introspection` API can be used to get such information.

The response from `/auth/introspection` API has some parameters. Among them, it is `action` parameter
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
as the entity body of the response if you want. Note that, however, [RFC 7662](https://datatracker.ietf.org/doc/html/rfc7662) does not mention anything about the response
body of error responses.

The following illustrates an example response which the introspection endpoint of the authorization
server implementation generates and returns to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{responseContent}
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
is invalid. This happens when the request from the client did not include the token request parameter.
See "[2.1. Introspection Request](https://datatracker.ietf.org/doc/html/rfc7662#section-2.1)" in
RFC 7662 for details about requirements for introspection requests.

The HTTP status of the response returned to the client application should be "400 Bad Request".

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response if you want. Note that, however, [RFC 7662](https://datatracker.ietf.org/doc/html/rfc7662)
does not mention anything about the response body of error responses.

The following illustrates an example response which the introspection endpoint of the authorization
server implementation generates and returns to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{responseContent}
```

**OK**

When the value of `action` is `OK`, the request from the client application is valid.

The HTTP status of the response returned to the client application must be "200 OK" and its content
type must be `application/json`.

The value of `responseContent` is a JSON string which complies with the introspection response
defined in "2.2. Introspection Response" in RFC7662.

The following illustrates the response which the introspection endpoint of your authorization server
implementation should generate and return to the client application.

```
HTTP/1.1 200 OK
Content-Type: application/json

{responseContent}
```

Note that RFC 7662 says _"To prevent token scanning attacks, **the endpoint MUST also require some
form of authorization to access this endpoint**"_. This means that you have to protect your introspection
endpoint in some way or other. Authlete does not care about how your introspection endpoint is protected.
In most cases, as mentioned in RFC 7662, "401 Unauthorized" is a proper response when an introspection
request does not satisfy authorization requirements imposed by your introspection endpoint.

</details>


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1auth1introspection1standardPostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.AuthIntrospectionStandardApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthIntrospectionStandardApiFormResponse res = sdk.introspections().processForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1auth1introspection1standardPostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1auth1introspection1standardPostRequestBodyContentApplication1jsonSchema.builder()
                    .parameters("<value>")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                         | Type                                                                                                                                                                                                                                              | Required                                                                                                                                                                                                                                          | Description                                                                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                                                       | *String*                                                                                                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                                                                | A service ID.                                                                                                                                                                                                                                     |
| `1api1Percent7BserviceIdPercent7D1auth1introspection1standardPostRequestBodyContentApplication1jsonSchema`                                                                                                                                        | [1api1Percent7BserviceIdPercent7D1auth1introspection1standardPostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1auth1introspection1standardPostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                                                | N/A                                                                                                                                                                                                                                               |

### Response

**[AuthIntrospectionStandardApiFormResponse](../../models/operations/AuthIntrospectionStandardApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |