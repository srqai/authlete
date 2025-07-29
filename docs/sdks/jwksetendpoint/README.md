# JwkSetEndpoint
(*jwkSetEndpoint()*)

## Overview

### Available Operations

* [get](#get) - Get JWK Set

## get

This API gathers JWK Set information for a service so that its client applications can verify
signatures by the service and encrypt their requests to the service.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the jwk set endpoint of the
service where the service that supports OpenID Connect must expose its JWK Set information so that
client applications can verify signatures by the service and encrypt their requests to the service.
The URI of the endpoint can be found as the value of `jwks_uri` in [OpenID Provider Metadata](https://openid.net/specs/openid-connect-discovery-1_0.html#ProviderMetadata)
if the service supports [OpenID Connect Discovery 1.0](https://openid.net/specs/openid-connect-discovery-1_0.html).

</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="service_jwks_get_api" method="get" path="/api/{serviceId}/service/jwks/get" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ServiceJwksGetApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceJwksGetApiResponse res = sdk.jwkSetEndpoint().get()
                .serviceId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                         | Type                                                                                                                                                                                                              | Required                                                                                                                                                                                                          | Description                                                                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `includePrivateKeys`                                                                                                                                                                                              | *Optional\<Boolean>*                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                | The boolean value that indicates whether the response should include the private keys associated with the service or not. If `true`, the private keys are included in the response. The default value is `false`. |
| `pretty`                                                                                                                                                                                                          | *Optional\<Boolean>*                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                | This boolean value indicates whether the JSON in the response should be formatted or not. If `true`, the JSON in the response is pretty-formatted. The default value is `false`.                                  |
| `serviceId`                                                                                                                                                                                                       | *String*                                                                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                                | A service ID.                                                                                                                                                                                                     |
| `serverURL`                                                                                                                                                                                                       | *String*                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                | An optional server URL to use.                                                                                                                                                                                    |

### Response

**[ServiceJwksGetApiResponse](../../models/operations/ServiceJwksGetApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |