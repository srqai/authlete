# GrantManagementEndpoints
(*grantManagementEndpoints()*)

## Overview

### Available Operations

* [processRequest](#processrequest) - Process Grant Management Request

## processRequest

The API is for the implementation of the grant management endpoint which is
defined in "<a href="https://openid.net/specs/fapi-grant-management.html">Grant Management for OAuth 2.0</a>".


### Example Usage

<!-- UsageSnippet language="java" operationID="grant_m_api" method="post" path="/api/{serviceId}/gm" -->
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

        GrantMApiResponse res = sdk.grantManagementEndpoints().processRequest()
                .serviceId("<id>")
                .requestBody(GrantMApiRequestBody.builder()
                    .accessToken("eyJhbGciOiJFUzI1NiJ9.eyJleHAiOjE1NTk4MTE3NTAsImlzcyI6IjU3Mjk3NDA4ODY3In0K.csmdholMVcmjqHe59YWgLGNvm7I5Whp4phQCoGxyrlRGMnTgsfxtwyxBgMXQqEPD5q5k9FaEWNk37K8uAtSwrA")
                    .subject("123457884")
                    .gmAction(GrantMApiGmAction.REVOKE)
                    .grantId("57297408867")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `serviceId`                                                             | *String*                                                                | :heavy_check_mark:                                                      | A service ID.                                                           |
| `requestBody`                                                           | [GrantMApiRequestBody](../../models/operations/GrantMApiRequestBody.md) | :heavy_check_mark:                                                      | N/A                                                                     |
| `serverURL`                                                             | *String*                                                                | :heavy_minus_sign:                                                      | An optional server URL to use.                                          |

### Response

**[GrantMApiResponse](../../models/operations/GrantMApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |