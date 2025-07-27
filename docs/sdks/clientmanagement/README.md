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

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ClientGetListApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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
| `serviceId`                                                                                                                                                                                                                                       | *String*                                                                                                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                                                                | A service ID.                                                                                                                                                                                                                                     |
| `developer`                                                                                                                                                                                                                                       | *Optional\<String>*                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                | The developer of client applications. The default value is null. If this parameter is not set<br/>to `null`, client application of the specified developer are returned. Otherwise, all client<br/>applications that belong to the service are returned.<br/> |
| `start`                                                                                                                                                                                                                                           | *Optional\<Integer>*                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                | Start index (inclusive) of the result set. The default value is 0. Must not be a negative number.                                                                                                                                                 |
| `end`                                                                                                                                                                                                                                             | *Optional\<Integer>*                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                | End index (exclusive) of the result set. The default value is 5. Must not be a negative number.                                                                                                                                                   |

### Response

**[ClientGetListApiResponse](../../models/operations/ClientGetListApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## create

Create a new client.


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ClientCreateApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientCreateApiResponse res = sdk.clientManagement().create()
                .serviceId("<id>")
                .client(ClientInput.builder()
                    .clientName("My Client")
                    .clientIdAlias("my-client")
                    .clientIdAliasEnabled(true)
                    .clientType(ClientClientType.CONFIDENTIAL)
                    .applicationType(ApplicationType.WEB)
                    .grantTypes(List.of(
                        GrantType.AUTHORIZATION_CODE,
                        GrantType.REFRESH_TOKEN))
                    .responseTypes(List.of(
                        ResponseType.CODE,
                        ResponseType.TOKEN))
                    .redirectUris(List.of(
                        "https://my-client.example.com/cb1",
                        "https://my-client.example.com/cb2"))
                    .tokenAuthMethod(ClientAuthenticationMethod.CLIENT_SECRET_BASIC)
                    .attributes(List.of(
                        Pair.builder()
                            .key("attribute1-key")
                            .value("attribute1-value")
                            .build(),
                        Pair.builder()
                            .key("attribute2-key")
                            .value("attribute2-value")
                            .build()))
                    .build())
                .call();

        if (res.client().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                        | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `serviceId`                                                      | *String*                                                         | :heavy_check_mark:                                               | A service ID.                                                    |
| `client`                                                         | [Optional\<ClientInput>](../../models/components/ClientInput.md) | :heavy_minus_sign:                                               | N/A                                                              |

### Response

**[ClientCreateApiResponse](../../models/operations/ClientCreateApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## update

Update a client.


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ClientUpdateApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ClientUpdateApiResponse res = sdk.clientManagement().update()
                .serviceId("<id>")
                .clientId("<id>")
                .client(ClientInput.builder()
                    .clientName("My updated client")
                    .clientIdAlias("my-client")
                    .clientIdAliasEnabled(true)
                    .clientType(ClientClientType.CONFIDENTIAL)
                    .applicationType(ApplicationType.WEB)
                    .tlsClientCertificateBoundAccessTokens(false)
                    .grantTypes(List.of(
                        GrantType.AUTHORIZATION_CODE,
                        GrantType.REFRESH_TOKEN))
                    .responseTypes(List.of(
                        ResponseType.CODE,
                        ResponseType.TOKEN))
                    .redirectUris(List.of(
                        "https://my-client.example.com/cb1",
                        "https://my-client.example.com/cb2"))
                    .tokenAuthMethod(ClientAuthenticationMethod.CLIENT_SECRET_BASIC)
                    .parRequired(false)
                    .requestObjectRequired(false)
                    .defaultMaxAge(0)
                    .idTokenSignAlg(JwsAlg.RS256)
                    .authTimeRequired(false)
                    .subjectType(SubjectType.PUBLIC)
                    .bcUserCodeRequired(false)
                    .attributes(List.of(
                        Pair.builder()
                            .key("attribute1-key")
                            .value("attribute1-value")
                            .build(),
                        Pair.builder()
                            .key("attribute2-key")
                            .value("attribute2-value")
                            .build()))
                    .frontChannelRequestObjectEncryptionRequired(false)
                    .requestObjectEncryptionAlgMatchRequired(false)
                    .requestObjectEncryptionEncMatchRequired(false)
                    .build())
                .call();

        if (res.client().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                        | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `serviceId`                                                      | *String*                                                         | :heavy_check_mark:                                               | A service ID.                                                    |
| `clientId`                                                       | *String*                                                         | :heavy_check_mark:                                               | A client ID.                                                     |
| `client`                                                         | [Optional\<ClientInput>](../../models/components/ClientInput.md) | :heavy_minus_sign:                                               | N/A                                                              |

### Response

**[ClientUpdateApiResponse](../../models/operations/ClientUpdateApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## delete

Delete a client.


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ClientDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `serviceId`        | *String*           | :heavy_check_mark: | A service ID.      |
| `clientId`         | *String*           | :heavy_check_mark: | The client ID.     |

### Response

**[ClientDeleteApiResponse](../../models/operations/ClientDeleteApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |