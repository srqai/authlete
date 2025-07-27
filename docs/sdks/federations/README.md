# Federations
(*federations()*)

## Overview

### Available Operations

* [postConfiguration](#postconfiguration) - Process Entity Configuration Request

## postConfiguration

This API gathers the federation configuration about a service.

The authorization server implementation should
retrieve the value of the <code>action</code>
response parameter from the API response and take the following steps
according to the value.

<h3><code>OK</code></h3>

When the value of the <code> action</code> response
parameter is <code>OK</code>, it means that Authlete
could prepare an entity configuration successfully.

In this case, the implementation of the entity configuration endpoint of the
authorization server should return an HTTP response to the client application
with the HTTP status code "`200 OK`" and the content type
"`application/entity-statement+jwt`". The message body (= an entity
configuration in the JWT format) of the response has been prepared by
Authlete's `/federation/configuration` API and it is available as the
<code>responseContent</code> response parameter.

The implementation of the entity configuration endpoint can construct an
HTTP response by doing like below.

<pre style="border: solid 1px black; padding: 0.5em;">
200 OK
Content-Type: application/entity-statement+jwt
(Other HTTP headers)

<i>(the value of the responseContent response parameter)</i></pre>

<h3><code>NOT_FOUND</code></h3>

When the value of the <code> action</code> response
parameter is <code>NOT_FOUND</code>, it means that
the service configuration has not enabled the feature of <a href=
"https://openid.net/specs/openid-connect-federation-1_0.html">OpenID Connect
Federation 1.0</a> and so the client application should have not access the
entity configuration endpoint.

In this case, the implementation of the entity configuration endpoint of the
authorization server should return an HTTP response to the client application
with the HTTP status code "`404 Not Found`" and the content type
"`application/json`". The message body (= error information in the JSON
format) of the response has been prepared by Authlete's
`/federation/configuration` API and it is available as the
<code>responseContent</code> response parameter.

The implementation of the entity configuration endpoint can construct an
HTTP response by doing like below.

<pre style="border: solid 1px black; padding: 0.5em;">
404 Not Found
Content-Type: application/json
(Other HTTP headers)

<i>(the value of the responseContent response parameter)</i></pre>

<h3><code>INTERNAL_SERVER_ERROR</code></h3>

could prepare an entity configuration successfully.

In this case, the implementation of the entity configuration endpoint of the
authorization server should return an HTTP response to the client application
with the HTTP status code "`200 OK`" and the content type
"`application/entity-statement+jwt`". The message body (= an entity
configuration in the JWT format) of the response has been prepared by
Authlete's `/federation/configuration` API and it is available as the
<code>responseContent</code> response parameter.

The implementation of the entity configuration endpoint can construct an
HTTP response by doing like below.

<pre style="border: solid 1px black; padding: 0.5em;">
200 OK
Content-Type: application/entity-statement+jwt
(Other HTTP headers)

<i>(the value of the responseContent response parameter)</i></pre>


</details>


### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.FederationConfigurationApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        FederationConfigurationApiResponse res = sdk.federations().postConfiguration()
                .serviceId("<id>")
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                            | Type                                                                                                                 | Required                                                                                                             | Description                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                          | *String*                                                                                                             | :heavy_check_mark:                                                                                                   | A service ID.                                                                                                        |
| `requestBody`                                                                                                        | [Optional\<FederationConfigurationApiRequestBody>](../../models/operations/FederationConfigurationApiRequestBody.md) | :heavy_minus_sign:                                                                                                   | N/A                                                                                                                  |

### Response

**[FederationConfigurationApiResponse](../../models/operations/FederationConfigurationApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |