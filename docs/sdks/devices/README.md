# Devices
(*devices()*)

## Overview

### Available Operations

* [authorize](#authorize) - Process Device Authorization Request
* [authorizeForm](#authorizeform) - Process Device Authorization Request

## authorize

This API parses request parameters of a [device authorization request](https://datatracker.ietf.org/doc/html/rfc8628#section-3.1)
and returns necessary data for the authorization server implementation to process the device authorization
request further.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the device authorization
endpoint of the service. The service implementation should retrieve the value of `action` from the
response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client application, it is an error on the server side.
Therefore, the authorization server implementation should generate a response to the client application
with "500 Internal Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes t he error, so it can be
used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
is wrong.

The authorization server implementation should generate a response to the client application with
"400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that client authentication of the device authorization
request failed.

The authorization server implementation should generate a response to the client application with
"401 Unauthorized" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the service implementation must generate and return
to the client application.

```
HTTP/1.1 401 Unauthorized
WWW-Authenticate: (challenge)
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**OK**

When the value of `action` is `OK`, it means that the device authorization request from the client
application is valid.

The authorization server implementation should generate a response to the client application with
"200 OK" and `application/json`.

The `responseContent` is a JSON string which can be used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client application.
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="device_authorization_api" method="post" path="/api/{serviceId}/device/authorization" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeviceAuthorizationApiRequestBody;
import org.openapis.openapi.models.operations.DeviceAuthorizationApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        DeviceAuthorizationApiResponse res = sdk.devices().authorize()
                .serviceId("<id>")
                .requestBody(DeviceAuthorizationApiRequestBody.builder()
                    .parameters("client_id=26888344961664&scope=history.read")
                    .clientId("26888344961664")
                    .clientSecret("SfnYOLkJdofrb_66mTd6q03_SDoDEUnpXtvqFaE4k6L6UcpZzbdVJi2GpBj48AvGeDDllwsTruC62WYqQ_LGog")
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
| `requestBody`                                                                                     | [DeviceAuthorizationApiRequestBody](../../models/operations/DeviceAuthorizationApiRequestBody.md) | :heavy_check_mark:                                                                                | N/A                                                                                               |
| `serverURL`                                                                                       | *String*                                                                                          | :heavy_minus_sign:                                                                                | An optional server URL to use.                                                                    |

### Response

**[DeviceAuthorizationApiResponse](../../models/operations/DeviceAuthorizationApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## authorizeForm

This API parses request parameters of a [device authorization request](https://datatracker.ietf.org/doc/html/rfc8628#section-3.1)
and returns necessary data for the authorization server implementation to process the device authorization
request further.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the device authorization
endpoint of the service. The service implementation should retrieve the value of `action` from the
response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client application, it is an error on the server side.
Therefore, the authorization server implementation should generate a response to the client application
with "500 Internal Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes t he error, so it can be
used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
is wrong.

The authorization server implementation should generate a response to the client application with
"400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that client authentication of the device authorization
request failed.

The authorization server implementation should generate a response to the client application with
"401 Unauthorized" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the service implementation must generate and return
to the client application.

```
HTTP/1.1 401 Unauthorized
WWW-Authenticate: (challenge)
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**OK**

When the value of `action` is `OK`, it means that the device authorization request from the client
application is valid.

The authorization server implementation should generate a response to the client application with
"200 OK" and `application/json`.

The `responseContent` is a JSON string which can be used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client application.
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="device_authorization_api_form" method="post" path="/api/{serviceId}/device/authorization" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeviceAuthorizationApiFormRequestBody;
import org.openapis.openapi.models.operations.DeviceAuthorizationApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        DeviceAuthorizationApiFormResponse res = sdk.devices().authorizeForm()
                .serviceId("<id>")
                .requestBody(DeviceAuthorizationApiFormRequestBody.builder()
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

| Parameter                                                                                                 | Type                                                                                                      | Required                                                                                                  | Description                                                                                               |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                               | *String*                                                                                                  | :heavy_check_mark:                                                                                        | A service ID.                                                                                             |
| `requestBody`                                                                                             | [DeviceAuthorizationApiFormRequestBody](../../models/operations/DeviceAuthorizationApiFormRequestBody.md) | :heavy_check_mark:                                                                                        | N/A                                                                                                       |
| `serverURL`                                                                                               | *String*                                                                                                  | :heavy_minus_sign:                                                                                        | An optional server URL to use.                                                                            |

### Response

**[DeviceAuthorizationApiFormResponse](../../models/operations/DeviceAuthorizationApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |