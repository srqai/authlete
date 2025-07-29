# ClientManagement
(*clientManagement()*)

## Overview

### Available Operations

* [list](#list) - List Clients
* [create](#create) - Create Client
* [update](#update) - Update Client
* [delete](#delete) - Delete Client ⚡

## list

Get a list of clients on a service.

If the access token can view a full service (including an admin), all clients within the
service are returned. Otherwise, only clients that the access token can view within the
service are returned.
- ViewClient: []


### Example Usage

<!-- UsageSnippet language="java" operationID="client_get_list_api" method="get" path="/api/{serviceId}/client/get/list" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientGetListApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientGetListApiResponse res = sdk.clientManagement().list()
                .serviceId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                         | Type                                                                                                                                                                                                                                              | Required                                                                                                                                                                                                                                          | Description                                                                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `developer`                                                                                                                                                                                                                                       | *Optional\<String>*                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                | The developer of client applications. The default value is null. If this parameter is not set<br/>to `null`, client application of the specified developer are returned. Otherwise, all client<br/>applications that belong to the service are returned.<br/> |
| `start`                                                                                                                                                                                                                                           | *Optional\<Integer>*                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                | Start index (inclusive) of the result set. The default value is 0. Must not be a negative number.                                                                                                                                                 |
| `end`                                                                                                                                                                                                                                             | *Optional\<Integer>*                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                | End index (exclusive) of the result set. The default value is 5. Must not be a negative number.                                                                                                                                                   |
| `serviceId`                                                                                                                                                                                                                                       | *String*                                                                                                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                                                                | A service ID.                                                                                                                                                                                                                                     |
| `serverURL`                                                                                                                                                                                                                                       | *String*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                | An optional server URL to use.                                                                                                                                                                                                                    |

### Response

**[ClientGetListApiResponse](../../models/operations/ClientGetListApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## create

Create a new client.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_create_api" method="post" path="/api/{serviceId}/client/create" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
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

        ClientCreateApiResponse res = sdk.clientManagement().create()
                .serviceId("<id>")
                .requestBody(ClientCreateApiRequestBody.builder()
                    .clientName("My Client")
                    .clientIdAlias("my-client")
                    .clientIdAliasEnabled(true)
                    .clientType(ClientCreateApiClientTypeRequest.CONFIDENTIAL)
                    .applicationType(ClientCreateApiApplicationTypeRequest.WEB)
                    .grantTypes(List.of(
                        ClientCreateApiGrantTypeRequest.AUTHORIZATION_CODE,
                        ClientCreateApiGrantTypeRequest.REFRESH_TOKEN))
                    .responseTypes(List.of(
                        ClientCreateApiResponseTypeRequest.CODE,
                        ClientCreateApiResponseTypeRequest.TOKEN))
                    .redirectUris(List.of(
                        "https://my-client.example.com/cb1",
                        "https://my-client.example.com/cb2"))
                    .tokenAuthMethod(ClientCreateApiTokenAuthMethodRequest.CLIENT_SECRET_BASIC)
                    .attributes(List.of(
                        ClientCreateApiAttributeRequest.builder()
                            .key("attribute1-key")
                            .value("attribute1-value")
                            .build(),
                        ClientCreateApiAttributeRequest.builder()
                            .key("attribute2-key")
                            .value("attribute2-value")
                            .build()))
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                    | *String*                                                                                       | :heavy_check_mark:                                                                             | A service ID.                                                                                  |
| `requestBody`                                                                                  | [Optional\<ClientCreateApiRequestBody>](../../models/operations/ClientCreateApiRequestBody.md) | :heavy_minus_sign:                                                                             | N/A                                                                                            |
| `serverURL`                                                                                    | *String*                                                                                       | :heavy_minus_sign:                                                                             | An optional server URL to use.                                                                 |

### Response

**[ClientCreateApiResponse](../../models/operations/ClientCreateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## update

Update a client.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_update_api" method="post" path="/api/{serviceId}/client/update/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
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

        ClientUpdateApiResponse res = sdk.clientManagement().update()
                .serviceId("<id>")
                .clientId("<id>")
                .requestBody(ClientUpdateApiRequestBody.builder()
                    .clientName("My updated client")
                    .clientIdAlias("my-client")
                    .clientIdAliasEnabled(true)
                    .clientType(ClientUpdateApiClientTypeRequest.CONFIDENTIAL)
                    .applicationType(ClientUpdateApiApplicationTypeRequest.WEB)
                    .tlsClientCertificateBoundAccessTokens(false)
                    .grantTypes(List.of(
                        ClientUpdateApiGrantTypeRequest.AUTHORIZATION_CODE,
                        ClientUpdateApiGrantTypeRequest.REFRESH_TOKEN))
                    .responseTypes(List.of(
                        ClientUpdateApiResponseTypeRequest.CODE,
                        ClientUpdateApiResponseTypeRequest.TOKEN))
                    .redirectUris(List.of(
                        "https://my-client.example.com/cb1",
                        "https://my-client.example.com/cb2"))
                    .tokenAuthMethod(ClientUpdateApiTokenAuthMethodRequest.CLIENT_SECRET_BASIC)
                    .parRequired(false)
                    .requestObjectRequired(false)
                    .defaultMaxAge(0)
                    .idTokenSignAlg(ClientUpdateApiIdTokenSignAlgRequest.RS256)
                    .authTimeRequired(false)
                    .subjectType(ClientUpdateApiSubjectTypeRequest.PUBLIC)
                    .bcUserCodeRequired(false)
                    .attributes(List.of(
                        ClientUpdateApiAttributeRequest.builder()
                            .key("attribute1-key")
                            .value("attribute1-value")
                            .build(),
                        ClientUpdateApiAttributeRequest.builder()
                            .key("attribute2-key")
                            .value("attribute2-value")
                            .build()))
                    .frontChannelRequestObjectEncryptionRequired(false)
                    .requestObjectEncryptionAlgMatchRequired(false)
                    .requestObjectEncryptionEncMatchRequired(false)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                    | *String*                                                                                       | :heavy_check_mark:                                                                             | A service ID.                                                                                  |
| `clientId`                                                                                     | *String*                                                                                       | :heavy_check_mark:                                                                             | A client ID.                                                                                   |
| `requestBody`                                                                                  | [Optional\<ClientUpdateApiRequestBody>](../../models/operations/ClientUpdateApiRequestBody.md) | :heavy_minus_sign:                                                                             | N/A                                                                                            |
| `serverURL`                                                                                    | *String*                                                                                       | :heavy_minus_sign:                                                                             | An optional server URL to use.                                                                 |

### Response

**[ClientUpdateApiResponse](../../models/operations/ClientUpdateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## delete

Delete a client.


### Example Usage

<!-- UsageSnippet language="java" operationID="client_delete_api" method="delete" path="/api/{serviceId}/client/delete/{clientId}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ClientDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientDeleteApiResponse res = sdk.clientManagement().delete()
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
| `clientId`                     | *String*                       | :heavy_check_mark:             | The client ID.                 |
| `serverURL`                    | *String*                       | :heavy_minus_sign:             | An optional server URL to use. |

### Response

**[ClientDeleteApiResponse](../../models/operations/ClientDeleteApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |