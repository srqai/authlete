# Credentials
(*credentials()*)

## Overview

### Available Operations

* [issueJwt](#issuejwt) - /api/{serviceId}/vci/jwtissuer API
* [issueJwtForm](#issuejwtform) - /api/{serviceId}/vci/jwtissuer API
* [issueBatch](#issuebatch) - /api/{serviceId}/vci/batch/issue API

## issueJwt

/api/{serviceId}/vci/jwtissuer API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_jwtissuer_api" method="post" path="/api/{serviceId}/vci/jwtissuer" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciJwtissuerApiRequestBody;
import org.openapis.openapi.models.operations.VciJwtissuerApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciJwtissuerApiResponse res = sdk.credentials().issueJwt()
                .serviceId("<id>")
                .requestBody(VciJwtissuerApiRequestBody.builder()
                    .pretty(true)
                    .build())
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
| `serviceId`                                                                         | *String*                                                                            | :heavy_check_mark:                                                                  | A service ID.                                                                       |
| `requestBody`                                                                       | [VciJwtissuerApiRequestBody](../../models/operations/VciJwtissuerApiRequestBody.md) | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `serverURL`                                                                         | *String*                                                                            | :heavy_minus_sign:                                                                  | An optional server URL to use.                                                      |

### Response

**[VciJwtissuerApiResponse](../../models/operations/VciJwtissuerApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## issueJwtForm

/api/{serviceId}/vci/jwtissuer API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_jwtissuer_api_form" method="post" path="/api/{serviceId}/vci/jwtissuer" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciJwtissuerApiFormRequestBody;
import org.openapis.openapi.models.operations.VciJwtissuerApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciJwtissuerApiFormResponse res = sdk.credentials().issueJwtForm()
                .serviceId("<id>")
                .requestBody(VciJwtissuerApiFormRequestBody.builder()
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

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                 | *String*                                                                                    | :heavy_check_mark:                                                                          | A service ID.                                                                               |
| `requestBody`                                                                               | [VciJwtissuerApiFormRequestBody](../../models/operations/VciJwtissuerApiFormRequestBody.md) | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `serverURL`                                                                                 | *String*                                                                                    | :heavy_minus_sign:                                                                          | An optional server URL to use.                                                              |

### Response

**[VciJwtissuerApiFormResponse](../../models/operations/VciJwtissuerApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## issueBatch

/api/{serviceId}/vci/batch/issue API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_batch_issue_api" method="post" path="/api/{serviceId}/vci/batch/issue" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciBatchIssueApiRequestBody;
import org.openapis.openapi.models.operations.VciBatchIssueApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciBatchIssueApiResponse res = sdk.credentials().issueBatch()
                .serviceId("<id>")
                .requestBody(VciBatchIssueApiRequestBody.builder()
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
| `requestBody`                                                                         | [VciBatchIssueApiRequestBody](../../models/operations/VciBatchIssueApiRequestBody.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `serverURL`                                                                           | *String*                                                                              | :heavy_minus_sign:                                                                    | An optional server URL to use.                                                        |

### Response

**[VciBatchIssueApiResponse](../../models/operations/VciBatchIssueApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |