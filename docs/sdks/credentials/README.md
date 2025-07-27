# Credentials
(*credentials()*)

## Overview

### Available Operations

* [issueJwt](#issuejwt) - /api/{serviceId}/vci/jwtissuer API
* [issueJwtForm](#issuejwtform) - /api/{serviceId}/vci/jwtissuer API
* [issueBatch](#issuebatch) - /api/{serviceId}/vci/batch/issue API

## issueJwt

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciJwtissuerApiRequestBody;
import org.openapis.openapi.models.operations.VciJwtissuerApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciJwtissuerApiResponse](../../models/operations/VciJwtissuerApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## issueJwtForm

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1vci1jwtissuerPostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciJwtissuerApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciJwtissuerApiFormResponse res = sdk.credentials().issueJwtForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1vci1jwtissuerPostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1vci1jwtissuerPostRequestBodyContentApplication1jsonSchema.builder()
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

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                           | *String*                                                                                                                                                                                                              | :heavy_check_mark:                                                                                                                                                                                                    | A service ID.                                                                                                                                                                                                         |
| `1api1Percent7BserviceIdPercent7D1vci1jwtissuerPostRequestBodyContentApplication1jsonSchema`                                                                                                                          | [1api1Percent7BserviceIdPercent7D1vci1jwtissuerPostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1vci1jwtissuerPostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                   |

### Response

**[VciJwtissuerApiFormResponse](../../models/operations/VciJwtissuerApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## issueBatch

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciBatchIssueApiRequestBody;
import org.openapis.openapi.models.operations.VciBatchIssueApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciBatchIssueApiResponse](../../models/operations/VciBatchIssueApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |