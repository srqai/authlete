# TokenOperations
(*tokenOperations()*)

## Overview

### Available Operations

* [delete](#delete) - Delete Access Token
* [revoke](#revoke) - Revoke Access Token
* [revokeForm](#revokeform) - Revoke Access Token

## delete

Delete an access token.


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.AuthTokenDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenDeleteApiResponse res = sdk.tokenOperations().delete()
                .serviceId("<id>")
                .accessTokenIdentifier("<value>")
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                  | Type                                                                                                                                       | Required                                                                                                                                   | Description                                                                                                                                |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `serviceId`                                                                                                                                | *String*                                                                                                                                   | :heavy_check_mark:                                                                                                                         | A service ID.                                                                                                                              |
| `accessTokenIdentifier`                                                                                                                    | *String*                                                                                                                                   | :heavy_check_mark:                                                                                                                         | The identifier of an existing access token. The identifier is the value of the access token<br/>or the value of the hash of the access token.<br/> |

### Response

**[AuthTokenDeleteApiResponse](../../models/operations/AuthTokenDeleteApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## revoke

Revoke an access token.


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.AuthTokenRevokeApiRequestBody;
import org.openapis.openapi.models.operations.AuthTokenRevokeApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenRevokeApiResponse res = sdk.tokenOperations().revoke()
                .serviceId("<id>")
                .requestBody(AuthTokenRevokeApiRequestBody.builder()
                    .accessTokenIdentifier("Z5a40U6dWvw2gMoCOAFbZcM85q4HC0Z--0YKD9-Nf6Q")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `serviceId`                                                                               | *String*                                                                                  | :heavy_check_mark:                                                                        | A service ID.                                                                             |
| `requestBody`                                                                             | [AuthTokenRevokeApiRequestBody](../../models/operations/AuthTokenRevokeApiRequestBody.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |

### Response

**[AuthTokenRevokeApiResponse](../../models/operations/AuthTokenRevokeApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## revokeForm

Revoke an access token.


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.AuthTokenRevokeApiFormResponse;
import org.openapis.openapi.models.operations.AuthTokenRevokeForm;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenRevokeApiFormResponse res = sdk.tokenOperations().revokeForm()
                .serviceId("<id>")
                .requestBody(AuthTokenRevokeForm.builder()
                    .token("<value>")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `serviceId`                                                           | *String*                                                              | :heavy_check_mark:                                                    | A service ID.                                                         |
| `requestBody`                                                         | [AuthTokenRevokeForm](../../models/operations/AuthTokenRevokeForm.md) | :heavy_check_mark:                                                    | N/A                                                                   |

### Response

**[AuthTokenRevokeApiFormResponse](../../models/operations/AuthTokenRevokeApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |