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

<!-- UsageSnippet language="java" operationID="federation_registration_api" method="post" path="/api/{serviceId}/federation/registration" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.FederationRegistrationApiRequestBody;
import org.openapis.openapi.models.operations.FederationRegistrationApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

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
| `serverURL`                                                                                             | *String*                                                                                                | :heavy_minus_sign:                                                                                      | An optional server URL to use.                                                                          |

### Response

**[FederationRegistrationApiResponse](../../models/operations/FederationRegistrationApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

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

<!-- UsageSnippet language="java" operationID="federation_registration_api_form" method="post" path="/api/{serviceId}/federation/registration" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.FederationRegistrationApiFormRequestBody;
import org.openapis.openapi.models.operations.FederationRegistrationApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        FederationRegistrationApiFormResponse res = sdk.federation().registerForm()
                .serviceId("<id>")
                .requestBody(FederationRegistrationApiFormRequestBody.builder()
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

| Parameter                                                                                                       | Type                                                                                                            | Required                                                                                                        | Description                                                                                                     |
| --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                     | *String*                                                                                                        | :heavy_check_mark:                                                                                              | A service ID.                                                                                                   |
| `requestBody`                                                                                                   | [FederationRegistrationApiFormRequestBody](../../models/operations/FederationRegistrationApiFormRequestBody.md) | :heavy_check_mark:                                                                                              | N/A                                                                                                             |
| `serverURL`                                                                                                     | *String*                                                                                                        | :heavy_minus_sign:                                                                                              | An optional server URL to use.                                                                                  |

### Response

**[FederationRegistrationApiFormResponse](../../models/operations/FederationRegistrationApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |