# Authorization
(*authorization()*)

## Overview

### Available Operations

* [issue](#issue) - Issue Authorization Response
* [issueForm](#issueform) - Issue Authorization Response
* [processPushedRequest](#processpushedrequest) - Process Pushed Authorization Request
* [processPushedRequestForm](#processpushedrequestform) - Process Pushed Authorization Request
* [getTicketInfo](#getticketinfo) - Get Ticket Information

## issue

This API parses request parameters of an authorization request and returns necessary data for the
authorization server implementation to process the authorization request further.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the authorization endpoint of
the service in order to generate a successful response to the client application.

The description of the `/auth/authorization` API describes the timing when this API should be called
and the meaning of request parameters. See [ISSUE] in `NO_INTERACTION`.

The response from `/auth/authorization/issue` API has some parameters.
Among them, it is `action` parameter that the authorization server implementation should check first
because it denotes the next action that the authorization server implementation should take.
According to the value of `action`, the authorization server implementation must take the steps
described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete.
In either case, from the viewpoint of the client application, it is an error on the server side.
Therefore, the service implementation should generate a response to the client application with
HTTP status of "500 Internal Server Error".

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client application since
"500 Internal Server Error" is not required by OAuth 2.0.

**BAD_REQUEST**

When the value of "action" is `BAD_REQUEST`, it means that the ticket is no longer valid (deleted
or expired) and that the reason of the invalidity was probably due to the end-user's too-delayed
response to the authorization UI.

The HTTP status of the response returned to the client application should be "400 Bad Request"
and the content type should be `application/json` although OAuth 2.0 specification does not mention
the format of the error response.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client application since
"400 Bad Request" is not required by OAuth 2.0.

**LOCATION**

When the value of `action` is `LOCATION`, it means that the response to the client application
should be "302 Found" with `Location` header.

The value of `responseContent` is a redirect URI which contains (1) an authorization code, an ID
token and/or an access token (on success) or (2) an error code (on failure), so it can be used as
the value of `Location` header.

The following illustrates the response which the service implementation must generate and return
to the client application.

```
HTTP/1.1 302 Found
Location: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**FORM**

When the value of `action` is `FORM`, it means that the response to the client application should
be "200 OK" with an HTML which triggers redirection by JavaScript. This happens when the authorization
request from the client contains `response_mode=form_post` request parameter.

The value of `responseContent` is an HTML which satisfies the requirements of `response_mode=form_post`,
so it can be used as the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 200 OK
Content-Type: text/html;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_authorization_issue_api" method="post" path="/api/{serviceId}/auth/authorization/issue" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthAuthorizationIssueApiRequestBody;
import org.openapis.openapi.models.operations.AuthAuthorizationIssueApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthAuthorizationIssueApiResponse res = sdk.authorization().issue()
                .serviceId("<id>")
                .requestBody(AuthAuthorizationIssueApiRequestBody.builder()
                    .ticket("FFgB9gwb_WXh6g1u-UQ8ZI-d_k4B-o-cm7RkVzI8Vnc")
                    .subject("john")
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
| `requestBody`                                                                                           | [AuthAuthorizationIssueApiRequestBody](../../models/operations/AuthAuthorizationIssueApiRequestBody.md) | :heavy_check_mark:                                                                                      | N/A                                                                                                     |
| `serverURL`                                                                                             | *String*                                                                                                | :heavy_minus_sign:                                                                                      | An optional server URL to use.                                                                          |

### Response

**[AuthAuthorizationIssueApiResponse](../../models/operations/AuthAuthorizationIssueApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## issueForm

This API parses request parameters of an authorization request and returns necessary data for the
authorization server implementation to process the authorization request further.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the authorization endpoint of
the service in order to generate a successful response to the client application.

The description of the `/auth/authorization` API describes the timing when this API should be called
and the meaning of request parameters. See [ISSUE] in `NO_INTERACTION`.

The response from `/auth/authorization/issue` API has some parameters.
Among them, it is `action` parameter that the authorization server implementation should check first
because it denotes the next action that the authorization server implementation should take.
According to the value of `action`, the authorization server implementation must take the steps
described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete.
In either case, from the viewpoint of the client application, it is an error on the server side.
Therefore, the service implementation should generate a response to the client application with
HTTP status of "500 Internal Server Error".

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client application since
"500 Internal Server Error" is not required by OAuth 2.0.

**BAD_REQUEST**

When the value of "action" is `BAD_REQUEST`, it means that the ticket is no longer valid (deleted
or expired) and that the reason of the invalidity was probably due to the end-user's too-delayed
response to the authorization UI.

The HTTP status of the response returned to the client application should be "400 Bad Request"
and the content type should be `application/json` although OAuth 2.0 specification does not mention
the format of the error response.

The value of `responseContent` is a JSON string which describes the error, so it can be used as
the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 400 Bad Request
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```

The endpoint implementation may return another different response to the client application since
"400 Bad Request" is not required by OAuth 2.0.

**LOCATION**

When the value of `action` is `LOCATION`, it means that the response to the client application
should be "302 Found" with `Location` header.

The value of `responseContent` is a redirect URI which contains (1) an authorization code, an ID
token and/or an access token (on success) or (2) an error code (on failure), so it can be used as
the value of `Location` header.

The following illustrates the response which the service implementation must generate and return
to the client application.

```
HTTP/1.1 302 Found
Location: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**FORM**

When the value of `action` is `FORM`, it means that the response to the client application should
be "200 OK" with an HTML which triggers redirection by JavaScript. This happens when the authorization
request from the client contains `response_mode=form_post` request parameter.

The value of `responseContent` is an HTML which satisfies the requirements of `response_mode=form_post`,
so it can be used as the entity body of the response.

The following illustrates the response which the service implementation should generate and return
to the client application.

```
HTTP/1.1 200 OK
Content-Type: text/html;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{responseContent}
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_authorization_issue_api_form" method="post" path="/api/{serviceId}/auth/authorization/issue" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthAuthorizationIssueApiFormRequestBody;
import org.openapis.openapi.models.operations.AuthAuthorizationIssueApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthAuthorizationIssueApiFormResponse res = sdk.authorization().issueForm()
                .serviceId("<id>")
                .requestBody(AuthAuthorizationIssueApiFormRequestBody.builder()
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

| Parameter                                                                                                       | Type                                                                                                            | Required                                                                                                        | Description                                                                                                     |
| --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                     | *String*                                                                                                        | :heavy_check_mark:                                                                                              | A service ID.                                                                                                   |
| `requestBody`                                                                                                   | [AuthAuthorizationIssueApiFormRequestBody](../../models/operations/AuthAuthorizationIssueApiFormRequestBody.md) | :heavy_check_mark:                                                                                              | N/A                                                                                                             |
| `serverURL`                                                                                                     | *String*                                                                                                        | :heavy_minus_sign:                                                                                              | An optional server URL to use.                                                                                  |

### Response

**[AuthAuthorizationIssueApiFormResponse](../../models/operations/AuthAuthorizationIssueApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## processPushedRequest

This API creates a pushed request authorization. It authenticates the client and creates a authorization_uri to be returned by the authorization server.


### Example Usage

<!-- UsageSnippet language="java" operationID="pushed_auth_req_api" method="post" path="/api/{serviceId}/pushed_auth_req" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.PushedAuthReqApiRequestBody;
import org.openapis.openapi.models.operations.PushedAuthReqApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        PushedAuthReqApiResponse res = sdk.authorization().processPushedRequest()
                .serviceId("<id>")
                .requestBody(PushedAuthReqApiRequestBody.builder()
                    .parameters("response_type=code%20id_token&client_id=5921531358155430&redirect_uri=https%3A%2F%2Fserver.example.com%2Fcb&state=SOME_VALUE_ABLE_TO_PREVENT_CSRF&scope=openid&nonce=SOME_VALUE_ABLE_TO_PREVENT_REPLAY_ATTACK&code_challenge=5ZWDQJiryK3eaLtSeFV8y1XySMCWtyITxICLaTwvK8g&code_challenge_method=S256")
                    .clientId("5921531358155430")
                    .clientSecret("P_FouxWlI7zcOep_9vBwR9qMAVJQiCiUiK1HrAP4GziOyezHQpqY0f5dHXK4JT4tnvI51OkbWVoEM9GnOyJViA")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `serviceId`                                                                           | *String*                                                                              | :heavy_check_mark:                                                                    | A service ID.                                                                         |
| `requestBody`                                                                         | [PushedAuthReqApiRequestBody](../../models/operations/PushedAuthReqApiRequestBody.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `serverURL`                                                                           | *String*                                                                              | :heavy_minus_sign:                                                                    | An optional server URL to use.                                                        |

### Response

**[PushedAuthReqApiResponse](../../models/operations/PushedAuthReqApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## processPushedRequestForm

This API creates a pushed request authorization. It authenticates the client and creates a authorization_uri to be returned by the authorization server.


### Example Usage

<!-- UsageSnippet language="java" operationID="pushed_auth_req_api_form" method="post" path="/api/{serviceId}/pushed_auth_req" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.PushedAuthReqApiFormRequestBody;
import org.openapis.openapi.models.operations.PushedAuthReqApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        PushedAuthReqApiFormResponse res = sdk.authorization().processPushedRequestForm()
                .serviceId("<id>")
                .requestBody(PushedAuthReqApiFormRequestBody.builder()
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

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                   | *String*                                                                                      | :heavy_check_mark:                                                                            | A service ID.                                                                                 |
| `requestBody`                                                                                 | [PushedAuthReqApiFormRequestBody](../../models/operations/PushedAuthReqApiFormRequestBody.md) | :heavy_check_mark:                                                                            | N/A                                                                                           |
| `serverURL`                                                                                   | *String*                                                                                      | :heavy_minus_sign:                                                                            | An optional server URL to use.                                                                |

### Response

**[PushedAuthReqApiFormResponse](../../models/operations/PushedAuthReqApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## getTicketInfo

Get Ticket Information

### Example Usage

<!-- UsageSnippet language="java" operationID="get_/api/{serviceId}/auth/authorization/ticket/info" method="get" path="/api/{serviceId}/auth/authorization/ticket/info" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetApiServiceIdAuthAuthorizationTicketInfoResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        GetApiServiceIdAuthAuthorizationTicketInfoResponse res = sdk.authorization().getTicketInfo()
                .serviceId("<id>")
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
| `serviceId`                    | *String*                       | :heavy_check_mark:             | N/A                            |
| `serverURL`                    | *String*                       | :heavy_minus_sign:             | An optional server URL to use. |

### Response

**[GetApiServiceIdAuthAuthorizationTicketInfoResponse](../../models/operations/GetApiServiceIdAuthAuthorizationTicketInfoResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |