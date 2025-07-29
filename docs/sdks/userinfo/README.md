# Userinfo
(*userinfo()*)

## Overview

### Available Operations

* [get](#get) - Process UserInfo Request
* [getForm](#getform) - Process UserInfo Request
* [issue](#issue) - Issue UserInfo Response
* [issueForm](#issueform) - Issue UserInfo Response

## get

This API gathers information about a user.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the [userinfo endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo)
of the authorization server in order to get information about the user that is associated with
an access token.

The response from `/auth/userinfo` API has various parameters. Among them, it is `action` parameter
that the authorization server implementation should check first because it denotes the next action
that the authorization server implementation should take. According to the value of `action`, the
service implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete. In either case, from the
viewpoint of the client application, it is an error on the server side. Therefore, the service
implementation should generate a response to the client application with HTTP status of "500 Internal
Server Error".

The value of `responseContent` is a string which describes the error in the format of [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750)
(OAuth 2.0 Bearer Token Usage) so the userinfo endpoint implementation can use the value of `responseContent`
as the value of`WWW-Authenticate` header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 500 Internal Server Error
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
does not contain an access token (= the request from the authorization server implementation to
Authlete does not contain `token` parameter).

The value of `responseContent` is a string which describes the error in the format
of [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the
userinfo endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 400 Bad Request
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the access token does not exist, has
expired, or is not associated with any subject (= any user account).

The value of `responseContent` is a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 401 Unauthorized
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**FORBIDDEN**

When the value of `action` is `FORBIDDEN`, it means that the access token does not include the
`openid` scope.

The value of `responseContent` is a string which describes the error in the format of [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750)
(OAuth 2.0 Bearer Token Usage) so the userinfo endpoint implementation can use the value of `responseContent`
as the value of`WWW-Authenticate` header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 403 Forbidden
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**OK**

When the value of `action` is `OK`, it means that the access token which the client application
presented is valid. To be concrete, it means that the access token exists, has not expired, includes
the openid scope, and is associated with a subject (= a user account).

What the userinfo endpoint implementation should do next is to collect information about the subject
(user) from your database. The value of the `subject` is contained in the subject parameter in the
response from this API and the names of data, i.e., the claims names are contained in the claims
parameter in the response. For example, if the `subject` parameter is `joe123` and the claims
parameter is `[ "given_name", "email" ]`, you need to extract information about joe123's given name
and email from your database.

Then, call Authlete's `/auth/userinfo/issue` API with the collected information and the access token
in order to make Authlete generate an ID token.

If an error occurred during the above steps, generate an error response to the client. The response
should comply with [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750). For example, if the
subject associated with the access token does not exist in your database any longer, you may feel
like generating a response like below.

```
HTTP/1.1 400 Bad Request
WWW-Authenticate: Bearer error="invalid_token",
 error_description="The subject associated with the access token does not exist."
Cache-Control: no-store
Pragma: no-cache
```

Also, an error might occur on database access. If you treat the error as an internal server error,
then the response would be like the following.

```
HTTP/1.1 500 Internal Server Error
WWW-Authenticate: Bearer error="server_error",
 error_description="Failed to extract information about the subject from the database."
Cache-Control: no-store
Pragma: no-cache
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_userinfo_api" method="post" path="/api/{serviceId}/auth/userinfo" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthUserinfoApiRequestBody;
import org.openapis.openapi.models.operations.AuthUserinfoApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthUserinfoApiResponse res = sdk.userinfo().get()
                .serviceId("<id>")
                .requestBody(AuthUserinfoApiRequestBody.builder()
                    .token("Ntm9MDb8WXQAevqrBkd84KTTHbYHVQrTjgUZCOWqEUI")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `serviceId`                                                                         | *String*                                                                            | :heavy_check_mark:                                                                  | A service ID.                                                                       |
| `requestBody`                                                                       | [AuthUserinfoApiRequestBody](../../models/operations/AuthUserinfoApiRequestBody.md) | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `serverURL`                                                                         | *String*                                                                            | :heavy_minus_sign:                                                                  | An optional server URL to use.                                                      |

### Response

**[AuthUserinfoApiResponse](../../models/operations/AuthUserinfoApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## getForm

This API gathers information about a user.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the [userinfo endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo)
of the authorization server in order to get information about the user that is associated with
an access token.

The response from `/auth/userinfo` API has various parameters. Among them, it is `action` parameter
that the authorization server implementation should check first because it denotes the next action
that the authorization server implementation should take. According to the value of `action`, the
service implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete. In either case, from the
viewpoint of the client application, it is an error on the server side. Therefore, the service
implementation should generate a response to the client application with HTTP status of "500 Internal
Server Error".

The value of `responseContent` is a string which describes the error in the format of [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750)
(OAuth 2.0 Bearer Token Usage) so the userinfo endpoint implementation can use the value of `responseContent`
as the value of`WWW-Authenticate` header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 500 Internal Server Error
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
does not contain an access token (= the request from the authorization server implementation to
Authlete does not contain `token` parameter).

The value of `responseContent` is a string which describes the error in the format
of [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the
userinfo endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 400 Bad Request
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the access token does not exist, has
expired, or is not associated with any subject (= any user account).

The value of `responseContent` is a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 401 Unauthorized
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**FORBIDDEN**

When the value of `action` is `FORBIDDEN`, it means that the access token does not include the
`openid` scope.

The value of `responseContent` is a string which describes the error in the format of [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750)
(OAuth 2.0 Bearer Token Usage) so the userinfo endpoint implementation can use the value of `responseContent`
as the value of`WWW-Authenticate` header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 403 Forbidden
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**OK**

When the value of `action` is `OK`, it means that the access token which the client application
presented is valid. To be concrete, it means that the access token exists, has not expired, includes
the openid scope, and is associated with a subject (= a user account).

What the userinfo endpoint implementation should do next is to collect information about the subject
(user) from your database. The value of the `subject` is contained in the subject parameter in the
response from this API and the names of data, i.e., the claims names are contained in the claims
parameter in the response. For example, if the `subject` parameter is `joe123` and the claims
parameter is `[ "given_name", "email" ]`, you need to extract information about joe123's given name
and email from your database.

Then, call Authlete's `/auth/userinfo/issue` API with the collected information and the access token
in order to make Authlete generate an ID token.

If an error occurred during the above steps, generate an error response to the client. The response
should comply with [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750). For example, if the
subject associated with the access token does not exist in your database any longer, you may feel
like generating a response like below.

```
HTTP/1.1 400 Bad Request
WWW-Authenticate: Bearer error="invalid_token",
 error_description="The subject associated with the access token does not exist."
Cache-Control: no-store
Pragma: no-cache
```

Also, an error might occur on database access. If you treat the error as an internal server error,
then the response would be like the following.

```
HTTP/1.1 500 Internal Server Error
WWW-Authenticate: Bearer error="server_error",
 error_description="Failed to extract information about the subject from the database."
Cache-Control: no-store
Pragma: no-cache
```
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_userinfo_api_form" method="post" path="/api/{serviceId}/auth/userinfo" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthUserinfoApiFormRequestBody;
import org.openapis.openapi.models.operations.AuthUserinfoApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthUserinfoApiFormResponse res = sdk.userinfo().getForm()
                .serviceId("<id>")
                .requestBody(AuthUserinfoApiFormRequestBody.builder()
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

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                 | *String*                                                                                    | :heavy_check_mark:                                                                          | A service ID.                                                                               |
| `requestBody`                                                                               | [AuthUserinfoApiFormRequestBody](../../models/operations/AuthUserinfoApiFormRequestBody.md) | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `serverURL`                                                                                 | *String*                                                                                    | :heavy_minus_sign:                                                                          | An optional server URL to use.                                                              |

### Response

**[AuthUserinfoApiFormResponse](../../models/operations/AuthUserinfoApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## issue

This API generates an ID token.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the [userinfo endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo)
of the authorization server in order to generate an ID token. Before calling this API, a valid
response from `/auth/userinfo` API must be obtained. Then, call this API with the access token
contained in the response and the claims values of the user (subject) associated with the access
token. See **OK** written in the description of `/auth/userinfo` API for details.

The response from `/auth/userinfo/issue` API has various parameters. Among them, it is `action`
parameter that the authorization server implementation should check first because it denotes the
next action that the authorization server implementation should take. According to the value of
`action`, the service implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete. In either case, from the
viewpoint of the client application, it is an error on the server side. Therefore, the service
implementation should generate a response to the client application with HTTP status of "500 Internal
Server Error".

The parameter `responseContent` returns a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 500 Internal Server Error
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
does not contain an access token (= the request from the authorization server implementation to
Authlete does not contain `token` parameter).

The parameter `responseContent` returns a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 400 Bad Request
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the access token does not exist, has
expired, or is not associated with any subject (= any user account).

The parameter `responseContent` returns a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 401 Unauthorized
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**FORBIDDEN**

When the value of `action` is `FORBIDDEN`, it means that the access token does not include the
`openid` scope.

The parameter `responseContent` returns a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 403 Forbidden
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**JSON**

When the value of `action` is `JSON`, it means that the access token which the client application
presented is valid and an ID token was successfully generated in the format of JSON.

The userinfo endpoint implementation is expected to generate a response to the client application.
The content type of the response must be `application/json` and the response body must be an ID
token in JSON format.

The value of `responseContent` is the ID token in JSON format when `action` is `JSON`, so
a response to the client can be built like below.

```
HTTP/1.1 200 OK
Cache-Control: no-store
Pragma: no-cache
Content-Type: application/json;charset=UTF-8

{responseContent}
```

**JWT**

When the value of `action` is `JWT`, it means that the access token which the client application
presented is valid and an ID token was successfully generated in the format of JWT (JSON Web Token)
([RFC 7519](https://datatracker.ietf.org/doc/html/rfc7519)).

The userinfo endpoint implementation is expected to generate a response to the client application.
The content type of the response must be `application/jwt` and the response body must be an ID
token in JWT format.

The value of `responseContent` is the ID token in JSON format when `action` is `JWT`, so a response
to the client can be built like below.

```
HTTP/1.1 200 OK
Cache-Control: no-store
Pragma: no-cache
Content-Type: application/jwt

{responseContent}
```

</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_userinfo_issue_api" method="post" path="/api/{serviceId}/auth/userinfo/issue" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthUserinfoIssueApiRequestBody;
import org.openapis.openapi.models.operations.AuthUserinfoIssueApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthUserinfoIssueApiResponse res = sdk.userinfo().issue()
                .serviceId("<id>")
                .requestBody(AuthUserinfoIssueApiRequestBody.builder()
                    .token("Ntm9MDb8WXQAevqrBkd84KTTHbYHVQrTjgUZCOWqEUI")
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
| `requestBody`                                                                                 | [AuthUserinfoIssueApiRequestBody](../../models/operations/AuthUserinfoIssueApiRequestBody.md) | :heavy_check_mark:                                                                            | N/A                                                                                           |
| `serverURL`                                                                                   | *String*                                                                                      | :heavy_minus_sign:                                                                            | An optional server URL to use.                                                                |

### Response

**[AuthUserinfoIssueApiResponse](../../models/operations/AuthUserinfoIssueApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## issueForm

This API generates an ID token.

<br>
<details>
<summary>Description</summary>

This API is supposed to be called from within the implementation of the [userinfo endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo)
of the authorization server in order to generate an ID token. Before calling this API, a valid
response from `/auth/userinfo` API must be obtained. Then, call this API with the access token
contained in the response and the claims values of the user (subject) associated with the access
token. See **OK** written in the description of `/auth/userinfo` API for details.

The response from `/auth/userinfo/issue` API has various parameters. Among them, it is `action`
parameter that the authorization server implementation should check first because it denotes the
next action that the authorization server implementation should take. According to the value of
`action`, the service implementation must take the steps described below.

**INTERNAL_SERVER_ERROR**

When the value of `action` is `INTERNAL_SERVER_ERROR`, it means that the request from the authorization
server implementation was wrong or that an error occurred in Authlete. In either case, from the
viewpoint of the client application, it is an error on the server side. Therefore, the service
implementation should generate a response to the client application with HTTP status of "500 Internal
Server Error".

The parameter `responseContent` returns a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 500 Internal Server Error
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**BAD_REQUEST**

When the value of `action` is `BAD_REQUEST`, it means that the request from the client application
does not contain an access token (= the request from the authorization server implementation to
Authlete does not contain `token` parameter).

The parameter `responseContent` returns a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 400 Bad Request
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**UNAUTHORIZED**

When the value of `action` is `UNAUTHORIZED`, it means that the access token does not exist, has
expired, or is not associated with any subject (= any user account).

The parameter `responseContent` returns a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 401 Unauthorized
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**FORBIDDEN**

When the value of `action` is `FORBIDDEN`, it means that the access token does not include the
`openid` scope.

The parameter `responseContent` returns a string which describes the error in the format of [RFC
6750](https://datatracker.ietf.org/doc/html/rfc6750) (OAuth 2.0 Bearer Token Usage) so the userinfo
endpoint implementation can use the value of `responseContent` as the value of`WWW-Authenticate`
header.

The following is an example response which complies with RFC 6750. Note that OpenID Connect Core
1.0 requires that an error response from userinfo endpoint comply with RFC 6750. See [5.3.3. UserInfo
Response](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoError) for details.

```
HTTP/1.1 403 Forbidden
WWW-Authenticate: {responseContent}
Cache-Control: no-store
Pragma: no-cache
```

**JSON**

When the value of `action` is `JSON`, it means that the access token which the client application
presented is valid and an ID token was successfully generated in the format of JSON.

The userinfo endpoint implementation is expected to generate a response to the client application.
The content type of the response must be `application/json` and the response body must be an ID
token in JSON format.

The value of `responseContent` is the ID token in JSON format when `action` is `JSON`, so
a response to the client can be built like below.

```
HTTP/1.1 200 OK
Cache-Control: no-store
Pragma: no-cache
Content-Type: application/json;charset=UTF-8

{responseContent}
```

**JWT**

When the value of `action` is `JWT`, it means that the access token which the client application
presented is valid and an ID token was successfully generated in the format of JWT (JSON Web Token)
([RFC 7519](https://datatracker.ietf.org/doc/html/rfc7519)).

The userinfo endpoint implementation is expected to generate a response to the client application.
The content type of the response must be `application/jwt` and the response body must be an ID
token in JWT format.

The value of `responseContent` is the ID token in JSON format when `action` is `JWT`, so a response
to the client can be built like below.

```
HTTP/1.1 200 OK
Cache-Control: no-store
Pragma: no-cache
Content-Type: application/jwt

{responseContent}
```

</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="auth_userinfo_issue_api_form" method="post" path="/api/{serviceId}/auth/userinfo/issue" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AuthUserinfoIssueApiFormRequestBody;
import org.openapis.openapi.models.operations.AuthUserinfoIssueApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        AuthUserinfoIssueApiFormResponse res = sdk.userinfo().issueForm()
                .serviceId("<id>")
                .requestBody(AuthUserinfoIssueApiFormRequestBody.builder()
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

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                           | *String*                                                                                              | :heavy_check_mark:                                                                                    | A service ID.                                                                                         |
| `requestBody`                                                                                         | [AuthUserinfoIssueApiFormRequestBody](../../models/operations/AuthUserinfoIssueApiFormRequestBody.md) | :heavy_check_mark:                                                                                    | N/A                                                                                                   |
| `serverURL`                                                                                           | *String*                                                                                              | :heavy_minus_sign:                                                                                    | An optional server URL to use.                                                                        |

### Response

**[AuthUserinfoIssueApiFormResponse](../../models/operations/AuthUserinfoIssueApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |