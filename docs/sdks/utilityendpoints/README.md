# UtilityEndpoints
(*utilityEndpoints()*)

## Overview

### Available Operations

* [getInfo](#getinfo) - Get Server Metadata
* [echo](#echo) - Echo

## getInfo

get the server version and enabled features


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.BadRequestException;
import org.openapis.openapi.models.operations.InfoApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        InfoApiResponse res = sdk.utilityEndpoints().getInfo()
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Response

**[InfoApiResponse](../../models/operations/InfoApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/BadRequestException                                            | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## echo

Echo test endpoint. Will return all path parameters in the request


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.operations.MiscEchoApiResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        MiscEchoApiResponse res = sdk.utilityEndpoints().echo()
                .call();

        // handle response
    }
}
```

### Response

**[MiscEchoApiResponse](../../models/operations/MiscEchoApiResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |