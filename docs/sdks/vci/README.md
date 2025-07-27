# Vci
(*vci()*)

## Overview

### Available Operations

* [parseSingle](#parsesingle) - /api/{serviceId}/vci/single/parse API
* [parseSingleForm](#parsesingleform) - /api/{serviceId}/vci/single/parse API

## parseSingle

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciSingleParseApiRequestBody;
import org.openapis.openapi.models.operations.VciSingleParseApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciSingleParseApiResponse](../../models/operations/VciSingleParseApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## parseSingleForm

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1vci1single1parsePostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciSingleParseApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciSingleParseApiFormResponse res = sdk.vci().parseSingleForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1vci1single1parsePostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1vci1single1parsePostRequestBodyContentApplication1jsonSchema.builder()
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                   | Type                                                                                                                                                                                                                        | Required                                                                                                                                                                                                                    | Description                                                                                                                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                                 | *String*                                                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                                          | A service ID.                                                                                                                                                                                                               |
| `1api1Percent7BserviceIdPercent7D1vci1single1parsePostRequestBodyContentApplication1jsonSchema`                                                                                                                             | [1api1Percent7BserviceIdPercent7D1vci1single1parsePostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1vci1single1parsePostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                          | N/A                                                                                                                                                                                                                         |

### Response

**[VciSingleParseApiFormResponse](../../models/operations/VciSingleParseApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |