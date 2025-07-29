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

<!-- UsageSnippet language="java" operationID="auth_token_delete_api" method="delete" path="/api/{serviceId}/auth/token/delete/{accessTokenIdentifier}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthTokenDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

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
| `serverURL`                                                                                                                                | *String*                                                                                                                                   | :heavy_minus_sign:                                                                                                                         | An optional server URL to use.                                                                                                             |

### Response

**[AuthTokenDeleteApiResponse](../../models/operations/AuthTokenDeleteApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## revoke

Revoke an access token.


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_revoke_api" method="post" path="/api/{serviceId}/auth/token/revoke" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthTokenRevokeApiRequestBody;
import org.openapis.openapi.models.operations.AuthTokenRevokeApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

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
| `serverURL`                                                                               | *String*                                                                                  | :heavy_minus_sign:                                                                        | An optional server URL to use.                                                            |

### Response

**[AuthTokenRevokeApiResponse](../../models/operations/AuthTokenRevokeApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## revokeForm

Revoke an access token.


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_token_revoke_api_form" method="post" path="/api/{serviceId}/auth/token/revoke" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthTokenRevokeApiFormRequestBody;
import org.openapis.openapi.models.operations.AuthTokenRevokeApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthTokenRevokeApiFormResponse res = sdk.tokenOperations().revokeForm()
                .serviceId("<id>")
                .requestBody(AuthTokenRevokeApiFormRequestBody.builder()
                    .clientLocked(false)
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
| `requestBody`                                                                                     | [AuthTokenRevokeApiFormRequestBody](../../models/operations/AuthTokenRevokeApiFormRequestBody.md) | :heavy_check_mark:                                                                                | N/A                                                                                               |
| `serverURL`                                                                                       | *String*                                                                                          | :heavy_minus_sign:                                                                                | An optional server URL to use.                                                                    |

### Response

**[AuthTokenRevokeApiFormResponse](../../models/operations/AuthTokenRevokeApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |