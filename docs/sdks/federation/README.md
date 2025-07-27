# Federation
(*federation()*)

## Overview

### Available Operations

* [register](#register) - Process Federation Registration Request
* [registerForm](#registerform) - Process Federation Registration Request

## register

The Authlete API is for implementations of the <b>federation registration
endpoint</b> that accepts "explicit client registration". Its details are
defined in <a href="https://openid.net/specs/openid-connect-federation-1_0.html"
>OpenID Connect Federation 1.0</a>.
</p>

<p>
The endpoint accepts `POST` requests whose `Content-Type`
is either of the following.
</p>

<ol>
  <li>`application/entity-statement+jwt`
  <li>`application/trust-chain+json`
</ol>

<p>
When the `Content-Type` of a request is
`application/entity-statement+jwt`, the content of the request is
the entity configuration of a relying party that is to be registered.
In this case, the implementation of the federation registration endpoint
should call Authlete's `/federation/registration` API with the
entity configuration set to the `entityConfiguration` request
parameter.
</p>

<p>
On the other hand, when the `Content-Type` of a request is
`application/trust-chain+json`, the content of the request is a
JSON array that contains entity statements in JWT format. The sequence
of the entity statements composes the trust chain of a relying party
that is to be registered. In this case, the implementation of the
federation registration endpoint should call Authlete's
`/federation/registration` API with the trust chain set to the
`trustChain` request parameter.
</p>


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.FederationRegistrationApiRequestBody;
import org.openapis.openapi.models.operations.FederationRegistrationApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        FederationRegistrationApiResponse res = sdk.federation().register()
                .serviceId("<id>")
                .requestBody(FederationRegistrationApiRequestBody.builder()
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
| `requestBody`                                                                                           | [FederationRegistrationApiRequestBody](../../models/operations/FederationRegistrationApiRequestBody.md) | :heavy_check_mark:                                                                                      | N/A                                                                                                     |

### Response

**[FederationRegistrationApiResponse](../../models/operations/FederationRegistrationApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## registerForm

The Authlete API is for implementations of the <b>federation registration
endpoint</b> that accepts "explicit client registration". Its details are
defined in <a href="https://openid.net/specs/openid-connect-federation-1_0.html"
>OpenID Connect Federation 1.0</a>.
</p>

<p>
The endpoint accepts `POST` requests whose `Content-Type`
is either of the following.
</p>

<ol>
  <li>`application/entity-statement+jwt`
  <li>`application/trust-chain+json`
</ol>

<p>
When the `Content-Type` of a request is
`application/entity-statement+jwt`, the content of the request is
the entity configuration of a relying party that is to be registered.
In this case, the implementation of the federation registration endpoint
should call Authlete's `/federation/registration` API with the
entity configuration set to the `entityConfiguration` request
parameter.
</p>

<p>
On the other hand, when the `Content-Type` of a request is
`application/trust-chain+json`, the content of the request is a
JSON array that contains entity statements in JWT format. The sequence
of the entity statements composes the trust chain of a relying party
that is to be registered. In this case, the implementation of the
federation registration endpoint should call Authlete's
`/federation/registration` API with the trust chain set to the
`trustChain` request parameter.
</p>


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1federation1registrationPostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.FederationRegistrationApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        FederationRegistrationApiFormResponse res = sdk.federation().registerForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1federation1registrationPostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1federation1registrationPostRequestBodyContentApplication1jsonSchema.builder()
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                 | Type                                                                                                                                                                                                                                      | Required                                                                                                                                                                                                                                  | Description                                                                                                                                                                                                                               |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                                               | *String*                                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                                        | A service ID.                                                                                                                                                                                                                             |
| `1api1Percent7BserviceIdPercent7D1federation1registrationPostRequestBodyContentApplication1jsonSchema`                                                                                                                                    | [1api1Percent7BserviceIdPercent7D1federation1registrationPostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1federation1registrationPostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                                        | N/A                                                                                                                                                                                                                                       |

### Response

**[FederationRegistrationApiFormResponse](../../models/operations/FederationRegistrationApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |