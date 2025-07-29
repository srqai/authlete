# JoseObject
(*joseObject()*)

## Overview

### Available Operations

* [verify](#verify) - Verify JOSE
* [verifyForm](#verifyform) - Verify JOSE

## verify

This API verifies a JOSE object.


### Example Usage

<!-- UsageSnippet language="java" operationID="jose_verify_api" method="post" path="/api/{serviceId}/jose/verify" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.JoseVerifyApiRequestBody;
import org.openapis.openapi.models.operations.JoseVerifyApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        JoseVerifyApiResponse res = sdk.joseObject().verify()
                .serviceId("<id>")
                .requestBody(JoseVerifyApiRequestBody.builder()
                    .jose("eyJhbGciOiJFUzI1NiJ9.eyJleHAiOjE1NTk4MTE3NTAsImlzcyI6IjU3Mjk3NDA4ODY3In0K.csmdholMVcmjqHe59YWgLGNvm7I5Whp4phQCoGxyrlRGMnTgsfxtwyxBgMXQqEPD5q5k9FaEWNk37K8uAtSwrA")
                    .clockSkew(100)
                    .clientIdentifier("57297408867")
                    .signedByClient(true)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `serviceId`                                                                                | *String*                                                                                   | :heavy_check_mark:                                                                         | A service ID.                                                                              |
| `requestBody`                                                                              | [Optional\<JoseVerifyApiRequestBody>](../../models/operations/JoseVerifyApiRequestBody.md) | :heavy_minus_sign:                                                                         | N/A                                                                                        |
| `serverURL`                                                                                | *String*                                                                                   | :heavy_minus_sign:                                                                         | An optional server URL to use.                                                             |

### Response

**[JoseVerifyApiResponse](../../models/operations/JoseVerifyApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## verifyForm

This API verifies a JOSE object.


### Example Usage

<!-- UsageSnippet language="java" operationID="jose_verify_api_form" method="post" path="/api/{serviceId}/jose/verify" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.JoseVerifyApiFormRequestBody;
import org.openapis.openapi.models.operations.JoseVerifyApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        JoseVerifyApiFormResponse res = sdk.joseObject().verifyForm()
                .serviceId("<id>")
                .requestBody(JoseVerifyApiFormRequestBody.builder()
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

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                        | *String*                                                                                           | :heavy_check_mark:                                                                                 | A service ID.                                                                                      |
| `requestBody`                                                                                      | [Optional\<JoseVerifyApiFormRequestBody>](../../models/operations/JoseVerifyApiFormRequestBody.md) | :heavy_minus_sign:                                                                                 | N/A                                                                                                |
| `serverURL`                                                                                        | *String*                                                                                           | :heavy_minus_sign:                                                                                 | An optional server URL to use.                                                                     |

### Response

**[JoseVerifyApiFormResponse](../../models/operations/JoseVerifyApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |