# Services
(*services()*)

## Overview

### Available Operations

* [create](#create) - Create Service
* [update](#update) - Update Service
* [delete](#delete) - Delete Service ⚡

## create

Create a new service.


### Example Usage

<!-- UsageSnippet language="java" operationID="service_create_api" method="post" path="/api/service/create" -->
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

        ServiceCreateApiRequest req = ServiceCreateApiRequest.builder()
                .serviceName("My service")
                .issuer("https://my-service.example.com")
                .clientIdAliasEnabled(true)
                .supportedGrantTypes(List.of(
                    ServiceCreateApiSupportedGrantTypeRequest.AUTHORIZATION_CODE,
                    ServiceCreateApiSupportedGrantTypeRequest.REFRESH_TOKEN))
                .supportedResponseTypes(List.of(
                    ServiceCreateApiSupportedResponseTypeRequest.CODE))
                .authorizationEndpoint("https://my-service.example.com/authz")
                .pkceRequired(true)
                .tokenEndpoint("https://my-service.example.com/token")
                .supportedTokenAuthMethods(List.of(
                    ServiceCreateApiSupportedTokenAuthMethodRequest.CLIENT_SECRET_BASIC))
                .revocationEndpoint("https://my-service.example.com/revocation")
                .supportedRevocationAuthMethods(List.of(
                    ServiceCreateApiSupportedRevocationAuthMethodRequest.CLIENT_SECRET_BASIC))
                .introspectionEndpoint("https://my-service.example.com/introspection")
                .supportedIntrospectionAuthMethods(List.of(
                    ServiceCreateApiSupportedIntrospectionAuthMethodRequest.CLIENT_SECRET_BASIC))
                .accessTokenType("Bearer")
                .accessTokenDuration(3600L)
                .refreshTokenDuration(3600L)
                .supportedScopes(List.of(
                    ServiceCreateApiSupportedScopeRequest.builder()
                        .name("timeline.read")
                        .defaultEntry(false)
                        .description("A permission to read your timeline.")
                        .build(),
                    ServiceCreateApiSupportedScopeRequest.builder()
                        .name("history.read")
                        .defaultEntry(false)
                        .description("A permission to read your history.")
                        .build()))
                .attributes(List.of(
                    ServiceCreateApiAttributeRequest.builder()
                        .key("attribute1-key")
                        .value("attribute1-value")
                        .build(),
                    ServiceCreateApiAttributeRequest.builder()
                        .key("attribute2-key")
                        .value("attribute2-value")
                        .build()))
                .build();

        ServiceCreateApiResponse res = sdk.services().create()
                .request(req)
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `request`                                                                     | [ServiceCreateApiRequest](../../models/operations/ServiceCreateApiRequest.md) | :heavy_check_mark:                                                            | The request object to use for the request.                                    |
| `serverURL`                                                                   | *String*                                                                      | :heavy_minus_sign:                                                            | An optional server URL to use.                                                |

### Response

**[ServiceCreateApiResponse](../../models/operations/ServiceCreateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## update

Update a service.


### Example Usage

<!-- UsageSnippet language="java" operationID="service_update_api" method="post" path="/api/{serviceId}/service/update" -->
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

        ServiceUpdateApiResponse res = sdk.services().update()
                .serviceId("<id>")
                .requestBody(ServiceUpdateApiRequestBody.builder()
                    .serviceName("My updated service")
                    .issuer("https://my-service.example.com")
                    .clientIdAliasEnabled(true)
                    .supportedGrantTypes(List.of(
                        ServiceUpdateApiSupportedGrantTypeRequest.AUTHORIZATION_CODE,
                        ServiceUpdateApiSupportedGrantTypeRequest.REFRESH_TOKEN))
                    .supportedResponseTypes(List.of(
                        ServiceUpdateApiSupportedResponseTypeRequest.CODE))
                    .errorDescriptionOmitted(false)
                    .errorUriOmitted(false)
                    .authorizationEndpoint("https://my-service.example.com/authz")
                    .directAuthorizationEndpointEnabled(false)
                    .supportedDisplays(List.of(
                        ServiceUpdateApiSupportedDisplayRequest.PAGE))
                    .pkceRequired(true)
                    .pkceS256Required(false)
                    .authorizationResponseDuration(0L)
                    .tokenEndpoint("https://my-service.example.com/token")
                    .directTokenEndpointEnabled(false)
                    .supportedTokenAuthMethods(List.of(
                        ServiceUpdateApiSupportedTokenAuthMethodRequest.CLIENT_SECRET_BASIC))
                    .missingClientIdAllowed(false)
                    .revocationEndpoint("https://my-service.example.com/revocation")
                    .directRevocationEndpointEnabled(false)
                    .supportedRevocationAuthMethods(List.of(
                        ServiceUpdateApiSupportedRevocationAuthMethodRequest.CLIENT_SECRET_BASIC))
                    .introspectionEndpoint("https://my-service.example.com/introspection")
                    .directIntrospectionEndpointEnabled(false)
                    .supportedIntrospectionAuthMethods(List.of(
                        ServiceUpdateApiSupportedIntrospectionAuthMethodRequest.CLIENT_SECRET_BASIC))
                    .pushedAuthReqDuration(0L)
                    .parRequired(false)
                    .requestObjectRequired(false)
                    .traditionalRequestObjectProcessingApplied(false)
                    .mutualTlsValidatePkiCertChain(false)
                    .accessTokenType("Bearer")
                    .tlsClientCertificateBoundAccessTokens(false)
                    .accessTokenDuration(3600L)
                    .singleAccessTokenPerSubject(false)
                    .refreshTokenDuration(3600L)
                    .refreshTokenDurationKept(false)
                    .refreshTokenDurationReset(false)
                    .refreshTokenKept(false)
                    .supportedScopes(List.of(
                        ServiceUpdateApiSupportedScopeRequest.builder()
                            .name("history.read")
                            .defaultEntry(false)
                            .description("A permission to read your history.")
                            .build(),
                        ServiceUpdateApiSupportedScopeRequest.builder()
                            .name("timeline.read")
                            .defaultEntry(false)
                            .description("A permission to read your timeline.")
                            .build()))
                    .scopeRequired(false)
                    .idTokenDuration(0L)
                    .allowableClockSkew(0)
                    .supportedClaimTypes(List.of(
                        ServiceUpdateApiSupportedClaimTypeRequest.NORMAL))
                    .claimShortcutRestrictive(false)
                    .directJwksEndpointEnabled(false)
                    .directUserInfoEndpointEnabled(false)
                    .dynamicRegistrationSupported(false)
                    .backchannelAuthReqIdDuration(0)
                    .backchannelPollingInterval(0)
                    .backchannelUserCodeParameterSupported(false)
                    .backchannelBindingMessageRequiredInFapi(false)
                    .deviceFlowCodeDuration(0)
                    .deviceFlowPollingInterval(0)
                    .userCodeLength(0)
                    .attributes(List.of(
                        ServiceUpdateApiAttributeRequest.builder()
                            .key("attribute1-key")
                            .value("attribute1-value")
                            .build(),
                        ServiceUpdateApiAttributeRequest.builder()
                            .key("attribute2-key")
                            .value("attribute2-value")
                            .build()))
                    .nbfOptional(false)
                    .issSuppressed(false)
                    .tokenExpirationLinked(false)
                    .frontChannelRequestObjectEncryptionRequired(false)
                    .requestObjectEncryptionAlgMatchRequired(false)
                    .requestObjectEncryptionEncMatchRequired(false)
                    .hsmEnabled(false)
                    .grantManagementActionRequired(false)
                    .unauthorizedOnClientConfigSupported(false)
                    .dcrScopeUsedAsRequestable(false)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `serviceId`                                                                                      | *String*                                                                                         | :heavy_check_mark:                                                                               | A service ID.                                                                                    |
| `requestBody`                                                                                    | [Optional\<ServiceUpdateApiRequestBody>](../../models/operations/ServiceUpdateApiRequestBody.md) | :heavy_minus_sign:                                                                               | N/A                                                                                              |
| `serverURL`                                                                                      | *String*                                                                                         | :heavy_minus_sign:                                                                               | An optional server URL to use.                                                                   |

### Response

**[ServiceUpdateApiResponse](../../models/operations/ServiceUpdateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## delete

Delete a service.


### Example Usage

<!-- UsageSnippet language="java" operationID="service_delete_api" method="delete" path="/api/{serviceId}/service/delete" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ServiceDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceDeleteApiResponse res = sdk.services().delete()
                .serviceId("<id>")
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                      | Type                           | Required                       | Description                    |
| ------------------------------ | ------------------------------ | ------------------------------ | ------------------------------ |
| `serviceId`                    | *String*                       | :heavy_check_mark:             | A service ID.                  |
| `serverURL`                    | *String*                       | :heavy_minus_sign:             | An optional server URL to use. |

### Response

**[ServiceDeleteApiResponse](../../models/operations/ServiceDeleteApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |