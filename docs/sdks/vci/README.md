# Vci
(*vci()*)

## Overview

### Available Operations

* [parseSingle](#parsesingle) - /api/{serviceId}/vci/single/parse API
* [parseSingleForm](#parsesingleform) - /api/{serviceId}/vci/single/parse API

## parseSingle

/api/{serviceId}/vci/single/parse API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_single_parse_api" method="post" path="/api/{serviceId}/vci/single/parse" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciSingleParseApiRequestBody;
import org.openapis.openapi.models.operations.VciSingleParseApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciSingleParseApiResponse res = sdk.vci().parseSingle()
                .serviceId("<id>")
                .requestBody(VciSingleParseApiRequestBody.builder()
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
| `requestBody`                                                                           | [VciSingleParseApiRequestBody](../../models/operations/VciSingleParseApiRequestBody.md) | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `serverURL`                                                                             | *String*                                                                                | :heavy_minus_sign:                                                                      | An optional server URL to use.                                                          |

### Response

**[VciSingleParseApiResponse](../../models/operations/VciSingleParseApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## parseSingleForm

/api/{serviceId}/vci/single/parse API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_single_parse_api_form" method="post" path="/api/{serviceId}/vci/single/parse" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciSingleParseApiFormRequestBody;
import org.openapis.openapi.models.operations.VciSingleParseApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciSingleParseApiFormResponse res = sdk.vci().parseSingleForm()
                .serviceId("<id>")
                .requestBody(VciSingleParseApiFormRequestBody.builder()
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

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                     | *String*                                                                                        | :heavy_check_mark:                                                                              | A service ID.                                                                                   |
| `requestBody`                                                                                   | [VciSingleParseApiFormRequestBody](../../models/operations/VciSingleParseApiFormRequestBody.md) | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `serverURL`                                                                                     | *String*                                                                                        | :heavy_minus_sign:                                                                              | An optional server URL to use.                                                                  |

### Response

**[VciSingleParseApiFormResponse](../../models/operations/VciSingleParseApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |