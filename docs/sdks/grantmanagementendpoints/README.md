# GrantManagementEndpoints
(*grantManagementEndpoints()*)

## Overview

### Available Operations

* [processRequest](#processrequest) - Process Grant Management Request

## processRequest

The API is for the implementation of the grant management endpoint which is
defined in "<a href="https://openid.net/specs/fapi-grant-management.html">Grant Management for OAuth 2.0</a>".


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

        GrantMApiResponse res = sdk.grantManagementEndpoints().processRequest()
                .serviceId("<id>")
                .requestBody(GrantMApiRequestBody.builder()
                    .accessToken("eyJhbGciOiJFUzI1NiJ9.eyJleHAiOjE1NTk4MTE3NTAsImlzcyI6IjU3Mjk3NDA4ODY3In0K.csmdholMVcmjqHe59YWgLGNvm7I5Whp4phQCoGxyrlRGMnTgsfxtwyxBgMXQqEPD5q5k9FaEWNk37K8uAtSwrA")
                    .subject("123457884")
                    .gmAction(GmAction.REVOKE)
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

### Response

**[GrantMApiResponse](../../models/operations/GrantMApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |