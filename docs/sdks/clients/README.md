# Clients
(*clients()*)

## Overview

### Available Operations

* [getById](#getbyid) - Get Client
* [updateLock](#updatelock) - Update Client Lock
* [refreshSecret](#refreshsecret) - Rotate Client Secret
* [updateSecret](#updatesecret) - Update Client Secret
* [updateSecretForm](#updatesecretform) - Update Client Secret
* [getAuthorizedApplications](#getauthorizedapplications) - Get Authorized Applications
* [updateAuthorization](#updateauthorization) - Update Client Tokens
* [updateAuthorizationForm](#updateauthorizationform) - Update Client Tokens
* [deleteAuthorization](#deleteauthorization) - Delete Client Tokens
* [getGrantedScopes](#getgrantedscopes) - Get Granted Scopes
* [deleteGrantedScopes](#deletegrantedscopes) - Delete Granted Scopes
* [register](#register) - Register Client
* [registerForm](#registerform) - Register Client
* [get](#get) - Get Client
* [updateRegistration](#updateregistration) - Update Client
* [updateRegistrationForm](#updateregistrationform) - Update Client
* [getRequestableScopes](#getrequestablescopes) - Get Requestable Scopes
* [updateRequestableScopes](#updaterequestablescopes) - Update Requestable Scopes
* [deleteRequestableScopes](#deleterequestablescopes) - Delete Requestable Scopes

## getById

Get a client.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_get_api" method="get" path="/api/{serviceId}/client/get/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientGetApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientGetApiResponse res = sdk.clients().getById()
                .serviceId("<id>")
                .clientId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                      | Type                           | Required                       | Description                    |
| ------------------------------ | ------------------------------ | ------------------------------ | ------------------------------ |
| `serviceId`                    | *String*                       | :heavy_check_mark:             | A service ID.                  |
| `clientId`                     | *String*                       | :heavy_check_mark:             | A client ID.                   |
| `serverURL`                    | *String*                       | :heavy_minus_sign:             | An optional server URL to use. |

### Response

**[ClientGetApiResponse](../../models/operations/ClientGetApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateLock

Lock and unlock a client


### Example Usage

<!-- UsageSnippet language="java" operationID="client_flag_update_api" method="post" path="/api/{serviceId}/client/lock_flag/update/{clientIdentifier}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientFlagUpdateApiRequestBody;
import org.openapis.openapi.models.operations.ClientFlagUpdateApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientFlagUpdateApiResponse res = sdk.clients().updateLock()
                .serviceId("<id>")
                .clientIdentifier("<value>")
                .requestBody(ClientFlagUpdateApiRequestBody.builder()
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

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `serviceId`                                                                                            | *String*                                                                                               | :heavy_check_mark:                                                                                     | A service ID.                                                                                          |
| `clientIdentifier`                                                                                     | *String*                                                                                               | :heavy_check_mark:                                                                                     | A client ID.                                                                                           |
| `requestBody`                                                                                          | [Optional\<ClientFlagUpdateApiRequestBody>](../../models/operations/ClientFlagUpdateApiRequestBody.md) | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `serverURL`                                                                                            | *String*                                                                                               | :heavy_minus_sign:                                                                                     | An optional server URL to use.                                                                         |

### Response

**[ClientFlagUpdateApiResponse](../../models/operations/ClientFlagUpdateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## refreshSecret

Refresh the client secret of a client. A new value of the client secret will be generated by the
Authlete server.

If you want to specify a new value, use `/api/client/secret/update` API.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_secret_refresh_api" method="get" path="/api/{serviceId}/client/secret/refresh/{clientIdentifier}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientSecretRefreshApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientSecretRefreshApiResponse res = sdk.clients().refreshSecret()
                .serviceId("<id>")
                .clientIdentifier("<value>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                          | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `serviceId`                                        | *String*                                           | :heavy_check_mark:                                 | A service ID.                                      |
| `clientIdentifier`                                 | *String*                                           | :heavy_check_mark:                                 | The client ID or the client ID alias of a client.<br/> |
| `serverURL`                                        | *String*                                           | :heavy_minus_sign:                                 | An optional server URL to use.                     |

### Response

**[ClientSecretRefreshApiResponse](../../models/operations/ClientSecretRefreshApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateSecret

Update the client secret of a client.

If you want to have the Authlete server generate a new value of the client secret, use `/api/client/secret/refresh`
API.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_secret_update_api" method="post" path="/api/{serviceId}/client/secret/update/{clientIdentifier}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientSecretUpdateApiRequestBody;
import org.openapis.openapi.models.operations.ClientSecretUpdateApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientSecretUpdateApiResponse res = sdk.clients().updateSecret()
                .serviceId("<id>")
                .clientIdentifier("<value>")
                .requestBody(ClientSecretUpdateApiRequestBody.builder()
                    .clientSecret("my_updated_client_secret")
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
| `clientIdentifier`                                                                              | *String*                                                                                        | :heavy_check_mark:                                                                              | The client ID or the client ID alias of a client.<br/>                                          |
| `requestBody`                                                                                   | [ClientSecretUpdateApiRequestBody](../../models/operations/ClientSecretUpdateApiRequestBody.md) | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `serverURL`                                                                                     | *String*                                                                                        | :heavy_minus_sign:                                                                              | An optional server URL to use.                                                                  |

### Response

**[ClientSecretUpdateApiResponse](../../models/operations/ClientSecretUpdateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateSecretForm

Update the client secret of a client.

If you want to have the Authlete server generate a new value of the client secret, use `/api/client/secret/refresh`
API.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_secret_update_api_form" method="post" path="/api/{serviceId}/client/secret/update/{clientIdentifier}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientSecretUpdateApiFormRequestBody;
import org.openapis.openapi.models.operations.ClientSecretUpdateApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientSecretUpdateApiFormResponse res = sdk.clients().updateSecretForm()
                .serviceId("<id>")
                .clientIdentifier("<value>")
                .requestBody(ClientSecretUpdateApiFormRequestBody.builder()
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

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                             | *String*                                                                                                | :heavy_check_mark:                                                                                      | A service ID.                                                                                           |
| `clientIdentifier`                                                                                      | *String*                                                                                                | :heavy_check_mark:                                                                                      | The client ID or the client ID alias of a client.<br/>                                                  |
| `requestBody`                                                                                           | [ClientSecretUpdateApiFormRequestBody](../../models/operations/ClientSecretUpdateApiFormRequestBody.md) | :heavy_check_mark:                                                                                      | N/A                                                                                                     |
| `serverURL`                                                                                             | *String*                                                                                                | :heavy_minus_sign:                                                                                      | An optional server URL to use.                                                                          |

### Response

**[ClientSecretUpdateApiFormResponse](../../models/operations/ClientSecretUpdateApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## getAuthorizedApplications

Get a list of client applications that an end-user has authorized.

The subject parameter is required and can be provided either in the path or as a query parameter.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_authorization_get_list_api" method="get" path="/api/{serviceId}/client/authorization/get/list" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientAuthorizationGetListApiRequest;
import org.openapis.openapi.models.operations.ClientAuthorizationGetListApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientAuthorizationGetListApiRequest req = ClientAuthorizationGetListApiRequest.builder()
                .subject("<value>")
                .serviceId("<id>")
                .build();

        ClientAuthorizationGetListApiResponse res = sdk.clients().getAuthorizedApplications()
                .request(req)
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `request`                                                                                               | [ClientAuthorizationGetListApiRequest](../../models/operations/ClientAuthorizationGetListApiRequest.md) | :heavy_check_mark:                                                                                      | The request object to use for the request.                                                              |
| `serverURL`                                                                                             | *String*                                                                                                | :heavy_minus_sign:                                                                                      | An optional server URL to use.                                                                          |

### Response

**[ClientAuthorizationGetListApiResponse](../../models/operations/ClientAuthorizationGetListApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateAuthorization

Update attributes of all existing access tokens given to a client application.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_authorization_update_api" method="post" path="/api/{serviceId}/client/authorization/update/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientAuthorizationUpdateApiRequestBody;
import org.openapis.openapi.models.operations.ClientAuthorizationUpdateApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientAuthorizationUpdateApiResponse res = sdk.clients().updateAuthorization()
                .serviceId("<id>")
                .clientId("<id>")
                .requestBody(ClientAuthorizationUpdateApiRequestBody.builder()
                    .subject("john")
                    .scopes(List.of(
                        "history.read"))
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                | Type                                                                                                                     | Required                                                                                                                 | Description                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| `serviceId`                                                                                                              | *String*                                                                                                                 | :heavy_check_mark:                                                                                                       | A service ID.                                                                                                            |
| `clientId`                                                                                                               | *String*                                                                                                                 | :heavy_check_mark:                                                                                                       | A client ID.<br/>                                                                                                        |
| `requestBody`                                                                                                            | [Optional\<ClientAuthorizationUpdateApiRequestBody>](../../models/operations/ClientAuthorizationUpdateApiRequestBody.md) | :heavy_minus_sign:                                                                                                       | N/A                                                                                                                      |
| `serverURL`                                                                                                              | *String*                                                                                                                 | :heavy_minus_sign:                                                                                                       | An optional server URL to use.                                                                                           |

### Response

**[ClientAuthorizationUpdateApiResponse](../../models/operations/ClientAuthorizationUpdateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateAuthorizationForm

Update attributes of all existing access tokens given to a client application.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_authorization_update_api_form" method="post" path="/api/{serviceId}/client/authorization/update/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientAuthorizationUpdateApiFormRequestBody;
import org.openapis.openapi.models.operations.ClientAuthorizationUpdateApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientAuthorizationUpdateApiFormResponse res = sdk.clients().updateAuthorizationForm()
                .serviceId("<id>")
                .clientId("<id>")
                .requestBody(ClientAuthorizationUpdateApiFormRequestBody.builder()
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

| Parameter                                                                                                                        | Type                                                                                                                             | Required                                                                                                                         | Description                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                      | *String*                                                                                                                         | :heavy_check_mark:                                                                                                               | A service ID.                                                                                                                    |
| `clientId`                                                                                                                       | *String*                                                                                                                         | :heavy_check_mark:                                                                                                               | A client ID.<br/>                                                                                                                |
| `requestBody`                                                                                                                    | [Optional\<ClientAuthorizationUpdateApiFormRequestBody>](../../models/operations/ClientAuthorizationUpdateApiFormRequestBody.md) | :heavy_minus_sign:                                                                                                               | N/A                                                                                                                              |
| `serverURL`                                                                                                                      | *String*                                                                                                                         | :heavy_minus_sign:                                                                                                               | An optional server URL to use.                                                                                                   |

### Response

**[ClientAuthorizationUpdateApiFormResponse](../../models/operations/ClientAuthorizationUpdateApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## deleteAuthorization

Delete all existing access tokens issued to a client application by an end-user.

The subject parameter is required and can be provided either in the path or as a query parameter.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_authorization_delete_api" method="delete" path="/api/{serviceId}/client/authorization/delete/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientAuthorizationDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientAuthorizationDeleteApiResponse res = sdk.clients().deleteAuthorization()
                .subject("<value>")
                .serviceId("<id>")
                .clientId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                       | Type                            | Required                        | Description                     |
| ------------------------------- | ------------------------------- | ------------------------------- | ------------------------------- |
| `subject`                       | *String*                        | :heavy_check_mark:              | Unique user ID of an end-user.<br/> |
| `serviceId`                     | *String*                        | :heavy_check_mark:              | A service ID.                   |
| `clientId`                      | *String*                        | :heavy_check_mark:              | A client ID.<br/>               |
| `serverURL`                     | *String*                        | :heavy_minus_sign:              | An optional server URL to use.  |

### Response

**[ClientAuthorizationDeleteApiResponse](../../models/operations/ClientAuthorizationDeleteApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## getGrantedScopes

Get the set of scopes that a user has granted to a client application.

<br>
<details>
<summary>Description</summary>

Possible values for `requestableScopes` parameter in the response from this API are as follows.

**null**

The user has not granted authorization to the client application in the past, or records about the
combination of the user and the client application have been deleted from Authlete's DB.

**An empty set**

The user has granted authorization to the client application in the past, but no scopes are associated
with the authorization.

**A set with at least one element**

The user has granted authorization to the client application in the past and some scopes are associated
with the authorization. These scopes are returned.
Example: `[ "profile", "email" ]`

The subject parameter is required and can be provided either in the path or as a query parameter.
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="client_granted_scopes_get_api" method="get" path="/api/{serviceId}/client/granted_scopes/get/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientGrantedScopesGetApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientGrantedScopesGetApiResponse res = sdk.clients().getGrantedScopes()
                .subject("<value>")
                .serviceId("<id>")
                .clientId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                       | Type                            | Required                        | Description                     |
| ------------------------------- | ------------------------------- | ------------------------------- | ------------------------------- |
| `subject`                       | *String*                        | :heavy_check_mark:              | Unique user ID of an end-user.<br/> |
| `serviceId`                     | *String*                        | :heavy_check_mark:              | A service ID.                   |
| `clientId`                      | *String*                        | :heavy_check_mark:              | A client ID.<br/>               |
| `serverURL`                     | *String*                        | :heavy_minus_sign:              | An optional server URL to use.  |

### Response

**[ClientGrantedScopesGetApiResponse](../../models/operations/ClientGrantedScopesGetApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## deleteGrantedScopes

Delete the set of scopes that an end-user has granted to a client application.

<br>
<details>
<summary>Description</summary>

Even if records about granted scopes are deleted by calling this API, existing access tokens are
not deleted and scopes of existing access tokens are not changed.
</details>

The subject parameter is required and can be provided either in the path or as a query parameter.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_granted_scopes_delete_api" method="delete" path="/api/{serviceId}/client/granted_scopes/delete/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientGrantedScopesDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientGrantedScopesDeleteApiResponse res = sdk.clients().deleteGrantedScopes()
                .subject("<value>")
                .serviceId("<id>")
                .clientId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                       | Type                            | Required                        | Description                     |
| ------------------------------- | ------------------------------- | ------------------------------- | ------------------------------- |
| `subject`                       | *String*                        | :heavy_check_mark:              | Unique user ID of an end-user.<br/> |
| `serviceId`                     | *String*                        | :heavy_check_mark:              | A service ID.                   |
| `clientId`                      | *String*                        | :heavy_check_mark:              | A client ID.<br/>               |
| `serverURL`                     | *String*                        | :heavy_minus_sign:              | An optional server URL to use.  |

### Response

**[ClientGrantedScopesDeleteApiResponse](../../models/operations/ClientGrantedScopesDeleteApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## register

Register a client. This API is supposed to be used to implement a client registration endpoint that
complies with [RFC 7591](https://datatracker.ietf.org/doc/html/rfc7591) (OAuth 2.0 Dynamic Client
Registration Protocol).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the client registration
endpoint of the authorization server. The authorization server implementation should retrieve
the value of `action` from the response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client or developer, it is an error on the server side.
Therefore, the authorization server implementation should generate a response with "500 Internal
Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client or developer since
"500 Internal Server Error" is not required by the specification.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client or developer
was wrong.

The authorization server implementation should generate a response with "400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**CREATED**

When the value of `action` is `CREATED`, it means that the request from the client or developer is
valid.

The authorization server implementation should generate a response to the client or developer with
"201 CREATED" and `application/json`.

The `responseContent` a JSON string which can be used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 201 CREATED
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="client_registration_api" method="post" path="/api/{serviceId}/client/registration" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientRegistrationApiRequestBody;
import org.openapis.openapi.models.operations.ClientRegistrationApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientRegistrationApiResponse res = sdk.clients().register()
                .serviceId("<id>")
                .requestBody(ClientRegistrationApiRequestBody.builder()
                    .json("{ \"client_name\": \"My Dynamic Client\" }")
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
| `requestBody`                                                                                   | [ClientRegistrationApiRequestBody](../../models/operations/ClientRegistrationApiRequestBody.md) | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `serverURL`                                                                                     | *String*                                                                                        | :heavy_minus_sign:                                                                              | An optional server URL to use.                                                                  |

### Response

**[ClientRegistrationApiResponse](../../models/operations/ClientRegistrationApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## registerForm

Register a client. This API is supposed to be used to implement a client registration endpoint that
complies with [RFC 7591](https://datatracker.ietf.org/doc/html/rfc7591) (OAuth 2.0 Dynamic Client
Registration Protocol).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the client registration
endpoint of the authorization server. The authorization server implementation should retrieve
the value of `action` from the response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client or developer, it is an error on the server side.
Therefore, the authorization server implementation should generate a response with "500 Internal
Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client or developer since
"500 Internal Server Error" is not required by the specification.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client or developer
was wrong.

The authorization server implementation should generate a response with "400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used
as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**CREATED**

When the value of `action` is `CREATED`, it means that the request from the client or developer is
valid.

The authorization server implementation should generate a response to the client or developer with
"201 CREATED" and `application/json`.

The `responseContent` a JSON string which can be used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 201 CREATED
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="client_registration_api_form" method="post" path="/api/{serviceId}/client/registration" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientRegistrationApiFormRequestBody;
import org.openapis.openapi.models.operations.ClientRegistrationApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientRegistrationApiFormResponse res = sdk.clients().registerForm()
                .serviceId("<id>")
                .requestBody(ClientRegistrationApiFormRequestBody.builder()
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

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                             | *String*                                                                                                | :heavy_check_mark:                                                                                      | A service ID.                                                                                           |
| `requestBody`                                                                                           | [ClientRegistrationApiFormRequestBody](../../models/operations/ClientRegistrationApiFormRequestBody.md) | :heavy_check_mark:                                                                                      | N/A                                                                                                     |
| `serverURL`                                                                                             | *String*                                                                                                | :heavy_minus_sign:                                                                                      | An optional server URL to use.                                                                          |

### Response

**[ClientRegistrationApiFormResponse](../../models/operations/ClientRegistrationApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## get

Get a dynamically registered client. This API is supposed to be used to implement a client registration
management endpoint that complies with [RFC 7592](https://datatracker.ietf.org/doc/html/rfc7592)
(OAuth 2.0 Dynamic Registration Management).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the client registration
management endpoint of the authorization server. The authorization server implementation should
retrieve the value of `action` from the response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client or developer, it is an error on the server side.
Therefore, the authorization server implementation should generate a response to the client or developer
with "500 Internal Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client or developer since
"500 Internal Server Error" is not required by the specification.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client or developer
was wrong.

The authorization server implementation should generate a response to the client or developer with
"400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the registration access token used by
the client configuration request (RFC 7592) is invalid, or the client application which the token
is tied to does not exist any longer or is invalid.

The HTTP status of the response returned to the client application must be "401 Unauthorized" and
the content type must be `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the endpoint implementation should generate and return
to the client application.

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

NOTE: The `UNAUTHORIZED` value was added in October, 2021. See the description of
`Service.unauthorizedOnClientConfigSupported` for details.

**OK**

When the value of `action` is `OK`, it means that the request from the client or developer is valid.

The authorization server implementation should generate a response to the client or developer with
"200 OK" and `application/json`.

The `responseContent` a JSON string which can be used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="client_registration_get_api" method="post" path="/api/{serviceId}/client/registration/get" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientRegistrationGetApiRequestBody;
import org.openapis.openapi.models.operations.ClientRegistrationGetApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientRegistrationGetApiResponse res = sdk.clients().get()
                .serviceId("<id>")
                .requestBody(ClientRegistrationGetApiRequestBody.builder()
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

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                           | *String*                                                                                              | :heavy_check_mark:                                                                                    | A service ID.                                                                                         |
| `requestBody`                                                                                         | [ClientRegistrationGetApiRequestBody](../../models/operations/ClientRegistrationGetApiRequestBody.md) | :heavy_check_mark:                                                                                    | N/A                                                                                                   |
| `serverURL`                                                                                           | *String*                                                                                              | :heavy_minus_sign:                                                                                    | An optional server URL to use.                                                                        |

### Response

**[ClientRegistrationGetApiResponse](../../models/operations/ClientRegistrationGetApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateRegistration

Update a dynamically registered client. This API is supposed to be used to implement a client
registration management endpoint that complies with [RFC 7592](https://datatracker.ietf.org/doc/html/rfc7592)
(OAuth 2.0 Dynamic Registration Management).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the client registration
management endpoint of the authorization server. The authorization server implementation should
retrieve the value of `action` from the response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client or developer, it is an error on the server side.
Therefore, the authorization server implementation should generate a response with "500 Internal
Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client or developer since
"500 Internal Server Error" is not required by the specification.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client or developer
was wrong.

The authorization server implementation should generate a response with "400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the registration access token used by
the client configuration request (RFC 7592) is invalid, or the client application which the token
is tied to does not exist any longer or is invalid.

The HTTP status of the response returned to the client application must be "401 Unauthorized" and
the content type must be `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the endpoint implementation should generate and return
to the client application.

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

NOTE: The `UNAUTHORIZED` value was added in October, 2021. See the description of
`Service.unauthorizedOnClientConfigSupported` for details.

**UPDATED**

When the value of `action` is `UPDATED`, it means that the request from the client or developer is
valid.

The authorization server implementation should generate a response to the client or developer with
"200 OK" and `application/json`.

The `responseContent` a JSON string which can be used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="client_registration_update_api" method="post" path="/api/{serviceId}/client/registration/update" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientRegistrationUpdateApiRequestBody;
import org.openapis.openapi.models.operations.ClientRegistrationUpdateApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientRegistrationUpdateApiResponse res = sdk.clients().updateRegistration()
                .serviceId("<id>")
                .requestBody(ClientRegistrationUpdateApiRequestBody.builder()
                    .clientId("26837717140341")
                    .token("qs4Tu5TV7qqDYT93bFs6ISyhTByMF9o-54GY4JU5vTA")
                    .json("{\"client_name\":\"My Updated Dynamic Client\",\"default_max_age\":0,\"registration_client_uri\":\"https://my-service.example.com/dcr/register/26837717140341\",\"client_id\":\"26837717140341\",\"token_endpoint_auth_method\":\"client_secret_basic\",\"require_pushed_authorization_requests\":false,\"backchannel_user_code_parameter\":false,\"client_secret\":\"bMsjvZm2FE1_mqJgxhmYj_Wr8rA0Pia_A_j-V076qQm6-P1edKB055W579GBe7MSbOdxZ3dJKsKinCtdIFwxpw\",\"tls_client_certificate_bound_access_tokens\":false,\"id_token_signed_response_alg\":\"RS256\",\"subject_type\":\"public\",\"require_signed_request_object\":false}")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                   | Type                                                                                                        | Required                                                                                                    | Description                                                                                                 |
| ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                 | *String*                                                                                                    | :heavy_check_mark:                                                                                          | A service ID.                                                                                               |
| `requestBody`                                                                                               | [ClientRegistrationUpdateApiRequestBody](../../models/operations/ClientRegistrationUpdateApiRequestBody.md) | :heavy_check_mark:                                                                                          | N/A                                                                                                         |
| `serverURL`                                                                                                 | *String*                                                                                                    | :heavy_minus_sign:                                                                                          | An optional server URL to use.                                                                              |

### Response

**[ClientRegistrationUpdateApiResponse](../../models/operations/ClientRegistrationUpdateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateRegistrationForm

Update a dynamically registered client. This API is supposed to be used to implement a client
registration management endpoint that complies with [RFC 7592](https://datatracker.ietf.org/doc/html/rfc7592)
(OAuth 2.0 Dynamic Registration Management).

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from the within the implementation of the client registration
management endpoint of the authorization server. The authorization server implementation should
retrieve the value of `action` from the response and take the following steps according to the value.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the API call from the authorization
server implementation was wrong or that an error occurred in Authlete.

In either case, from a viewpoint of the client or developer, it is an error on the server side.
Therefore, the authorization server implementation should generate a response with "500 Internal
Server Error"s and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client or developer since
"500 Internal Server Error" is not required by the specification.

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client or developer
was wrong.

The authorization server implementation should generate a response with "400 Bad Request" and `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the registration access token used by
the client configuration request (RFC 7592) is invalid, or the client application which the token
is tied to does not exist any longer or is invalid.

The HTTP status of the response returned to the client application must be "401 Unauthorized" and
the content type must be `application/json`.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the endpoint implementation should generate and return
to the client application.

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

NOTE: The `UNAUTHORIZED` value was added in October, 2021. See the description of
`Service.unauthorizedOnClientConfigSupported` for details.

**UPDATED**

When the value of `action` is `UPDATED`, it means that the request from the client or developer is
valid.

The authorization server implementation should generate a response to the client or developer with
"200 OK" and `application/json`.

The `responseContent` a JSON string which can be used as the entity body of the response.

The following illustrates the response which the authorization server implementation should generate
and return to the client or developer.

```
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="client_registration_update_api_form" method="post" path="/api/{serviceId}/client/registration/update" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientRegistrationUpdateApiFormRequestBody;
import org.openapis.openapi.models.operations.ClientRegistrationUpdateApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientRegistrationUpdateApiFormResponse res = sdk.clients().updateRegistrationForm()
                .serviceId("<id>")
                .requestBody(ClientRegistrationUpdateApiFormRequestBody.builder()
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

| Parameter                                                                                                           | Type                                                                                                                | Required                                                                                                            | Description                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                         | *String*                                                                                                            | :heavy_check_mark:                                                                                                  | A service ID.                                                                                                       |
| `requestBody`                                                                                                       | [ClientRegistrationUpdateApiFormRequestBody](../../models/operations/ClientRegistrationUpdateApiFormRequestBody.md) | :heavy_check_mark:                                                                                                  | N/A                                                                                                                 |
| `serverURL`                                                                                                         | *String*                                                                                                            | :heavy_minus_sign:                                                                                                  | An optional server URL to use.                                                                                      |

### Response

**[ClientRegistrationUpdateApiFormResponse](../../models/operations/ClientRegistrationUpdateApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## getRequestableScopes

Get the requestable scopes per client


### Example Usage

<!-- UsageSnippet language="java" operationID="client_extension_requestables_scopes_get_api" method="get" path="/api/{serviceId}/client/extension/requestable_scopes/get/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientExtensionRequestablesScopesGetApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientExtensionRequestablesScopesGetApiResponse res = sdk.clients().getRequestableScopes()
                .serviceId("<id>")
                .clientId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                      | Type                           | Required                       | Description                    |
| ------------------------------ | ------------------------------ | ------------------------------ | ------------------------------ |
| `serviceId`                    | *String*                       | :heavy_check_mark:             | A service ID.                  |
| `clientId`                     | *String*                       | :heavy_check_mark:             | A client ID.<br/>              |
| `serverURL`                    | *String*                       | :heavy_minus_sign:             | An optional server URL to use. |

### Response

**[ClientExtensionRequestablesScopesGetApiResponse](../../models/operations/ClientExtensionRequestablesScopesGetApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## updateRequestableScopes

Update requestable scopes of a client


### Example Usage

<!-- UsageSnippet language="java" operationID="client_extension_requestables_scopes_update_api" method="put" path="/api/{serviceId}/client/extension/requestable_scopes/update/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientExtensionRequestablesScopesUpdateApiRequestBody;
import org.openapis.openapi.models.operations.ClientExtensionRequestablesScopesUpdateApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientExtensionRequestablesScopesUpdateApiResponse res = sdk.clients().updateRequestableScopes()
                .serviceId("<id>")
                .clientId("<id>")
                .requestBody(ClientExtensionRequestablesScopesUpdateApiRequestBody.builder()
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                 | Type                                                                                                                                      | Required                                                                                                                                  | Description                                                                                                                               |
| ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                               | *String*                                                                                                                                  | :heavy_check_mark:                                                                                                                        | A service ID.                                                                                                                             |
| `clientId`                                                                                                                                | *String*                                                                                                                                  | :heavy_check_mark:                                                                                                                        | A client ID.<br/>                                                                                                                         |
| `requestBody`                                                                                                                             | [ClientExtensionRequestablesScopesUpdateApiRequestBody](../../models/operations/ClientExtensionRequestablesScopesUpdateApiRequestBody.md) | :heavy_check_mark:                                                                                                                        | N/A                                                                                                                                       |
| `serverURL`                                                                                                                               | *String*                                                                                                                                  | :heavy_minus_sign:                                                                                                                        | An optional server URL to use.                                                                                                            |

### Response

**[ClientExtensionRequestablesScopesUpdateApiResponse](../../models/operations/ClientExtensionRequestablesScopesUpdateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## deleteRequestableScopes

Delete requestable scopes of a client


### Example Usage

<!-- UsageSnippet language="java" operationID="client_extension_requestables_scopes_delete_api" method="delete" path="/api/{serviceId}/client/extension/requestable_scopes/delete/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientExtensionRequestablesScopesDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientExtensionRequestablesScopesDeleteApiResponse res = sdk.clients().deleteRequestableScopes()
                .serviceId("<id>")
                .clientId("<id>")
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                      | Type                           | Required                       | Description                    |
| ------------------------------ | ------------------------------ | ------------------------------ | ------------------------------ |
| `serviceId`                    | *String*                       | :heavy_check_mark:             | A service ID.                  |
| `clientId`                     | *String*                       | :heavy_check_mark:             | A client ID.<br/>              |
| `serverURL`                    | *String*                       | :heavy_minus_sign:             | An optional server URL to use. |

### Response

**[ClientExtensionRequestablesScopesDeleteApiResponse](../../models/operations/ClientExtensionRequestablesScopesDeleteApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |