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

```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ServiceCreateApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceInput req = ServiceInput.builder()
                .serviceName("My service")
                .issuer("https://my-service.example.com")
                .clientIdAliasEnabled(true)
                .supportedGrantTypes(List.of(
                    GrantType.AUTHORIZATION_CODE,
                    GrantType.REFRESH_TOKEN))
                .supportedResponseTypes(List.of(
                    ResponseType.CODE))
                .authorizationEndpoint("https://my-service.example.com/authz")
                .pkceRequired(true)
                .tokenEndpoint("https://my-service.example.com/token")
                .supportedTokenAuthMethods(List.of(
                    ClientAuthenticationMethod.CLIENT_SECRET_BASIC))
                .revocationEndpoint("https://my-service.example.com/revocation")
                .supportedRevocationAuthMethods(List.of(
                    ClientAuthenticationMethod.CLIENT_SECRET_BASIC))
                .introspectionEndpoint("https://my-service.example.com/introspection")
                .supportedIntrospectionAuthMethods(List.of(
                    ClientAuthenticationMethod.CLIENT_SECRET_BASIC))
                .accessTokenType("Bearer")
                .accessTokenDuration(3600L)
                .refreshTokenDuration(3600L)
                .supportedScopes(List.of(
                    Scope.builder()
                        .name("timeline.read")
                        .defaultEntry(false)
                        .description("A permission to read your timeline.")
                        .build(),
                    Scope.builder()
                        .name("history.read")
                        .defaultEntry(false)
                        .description("A permission to read your history.")
                        .build()))
                .attributes(List.of(
                    Pair.builder()
                        .key("attribute1-key")
                        .value("attribute1-value")
                        .build(),
                    Pair.builder()
                        .key("attribute2-key")
                        .value("attribute2-value")
                        .build()))
                .build();

        ServiceCreateApiResponse res = sdk.services().create()
                .request(req)
                .call();

        if (res.service().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                           | Type                                                | Required                                            | Description                                         |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `request`                                           | [ServiceInput](../../models/shared/ServiceInput.md) | :heavy_check_mark:                                  | The request object to use for the request.          |

### Response

**[ServiceCreateApiResponse](../../models/operations/ServiceCreateApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## update

Update a service.


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ServiceUpdateApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceUpdateApiResponse res = sdk.services().update()
                .serviceId("<id>")
                .service(ServiceInput.builder()
                    .serviceName("My updated service")
                    .issuer("https://my-service.example.com")
                    .clientIdAliasEnabled(true)
                    .supportedGrantTypes(List.of(
                        GrantType.AUTHORIZATION_CODE,
                        GrantType.REFRESH_TOKEN))
                    .supportedResponseTypes(List.of(
                        ResponseType.CODE))
                    .errorDescriptionOmitted(false)
                    .errorUriOmitted(false)
                    .authorizationEndpoint("https://my-service.example.com/authz")
                    .directAuthorizationEndpointEnabled(false)
                    .supportedDisplays(List.of(
                        Display.PAGE))
                    .pkceRequired(true)
                    .pkceS256Required(false)
                    .authorizationResponseDuration(0L)
                    .tokenEndpoint("https://my-service.example.com/token")
                    .directTokenEndpointEnabled(false)
                    .supportedTokenAuthMethods(List.of(
                        ClientAuthenticationMethod.CLIENT_SECRET_BASIC))
                    .missingClientIdAllowed(false)
                    .revocationEndpoint("https://my-service.example.com/revocation")
                    .directRevocationEndpointEnabled(false)
                    .supportedRevocationAuthMethods(List.of(
                        ClientAuthenticationMethod.CLIENT_SECRET_BASIC))
                    .introspectionEndpoint("https://my-service.example.com/introspection")
                    .directIntrospectionEndpointEnabled(false)
                    .supportedIntrospectionAuthMethods(List.of(
                        ClientAuthenticationMethod.CLIENT_SECRET_BASIC))
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
                        Scope.builder()
                            .name("history.read")
                            .defaultEntry(false)
                            .description("A permission to read your history.")
                            .build(),
                        Scope.builder()
                            .name("timeline.read")
                            .defaultEntry(false)
                            .description("A permission to read your timeline.")
                            .build()))
                    .scopeRequired(false)
                    .idTokenDuration(0L)
                    .allowableClockSkew(0)
                    .supportedClaimTypes(List.of(
                        ClaimType.NORMAL))
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
                        Pair.builder()
                            .key("attribute1-key")
                            .value("attribute1-value")
                            .build(),
                        Pair.builder()
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

        if (res.service().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                          | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `serviceId`                                                        | *String*                                                           | :heavy_check_mark:                                                 | A service ID.                                                      |
| `service`                                                          | [Optional\<ServiceInput>](../../models/components/ServiceInput.md) | :heavy_minus_sign:                                                 | N/A                                                                |

### Response

**[ServiceUpdateApiResponse](../../models/operations/ServiceUpdateApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## delete

Delete a service.


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ServiceDeleteApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `serviceId`        | *String*           | :heavy_check_mark: | A service ID.      |

### Response

**[ServiceDeleteApiResponse](../../models/operations/ServiceDeleteApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |