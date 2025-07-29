# DeviceFlow
(*deviceFlow()*)

## Overview

### Available Operations

* [verify](#verify) - Process Device Verification Request
* [verifyForm](#verifyform) - Process Device Verification Request
* [complete](#complete) - Complete Device Authorization
* [completeForm](#completeform) - Complete Device Authorization

## verify

The API returns information associated with a user code.

<br>
<details>
<summary>Description</summary>

After receiving a response from the device authorization endpoint of the authorization server,
the client application shows the end-user the user code and the verification URI which are included
in the device authorization response. Then, the end-user will access the verification URI using
a web browser on another device (typically, a smart phone). In normal implementations, the verification
endpoint will return an HTML page with an input form where the end-user inputs a user code. The
authorization server will receive a user code from the form.

After receiving a user code, the authorization server should call Authlete's `/device/verification`
API with the user code. And then, the authorization server implementation should retrieve the value
of `action` parameter from the API response and take the following steps according to the value.

**SERVER_ERROR**

When the value of `action` is `SERVER_ERROR`, it means that an error occurred on Authlete side. The
authorization server implementation should tell the end-user that something wrong happened and
urge her to re-initiate a device flow.

**NOT_EXIST**

When the value of `action` is `NOT_EXIST`, it means that the user code does not exist. The authorization
server implementation should tell the end-user that the user code is invalid and urge her to retry
to input a valid user code.

**EXPIRED**

When the value of `action` is `EXPIRED`, it means that the user code has expired. The authorization
server implementation should tell the end-user that the user code has expired and urge her to
re-initiate a device flow.

**VALID**

When the value of `action` is `VALID`, it means that the user code exists, has not expired, and
belongs to the service. The authorization server implementation should interact with the end-user
to ask whether she approves or rejects the authorization request from the device.
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="device_verification_api" method="post" path="/api/{serviceId}/device/verification" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeviceVerificationApiRequestBody;
import org.openapis.openapi.models.operations.DeviceVerificationApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        DeviceVerificationApiResponse res = sdk.deviceFlow().verify()
                .serviceId("<id>")
                .requestBody(DeviceVerificationApiRequestBody.builder()
                    .userCode("XWWKPBWVXQ")
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                     | *String*                                                                                        | :heavy_check_mark:                                                                              | A service ID.                                                                                   |
| `requestBody`                                                                                   | [DeviceVerificationApiRequestBody](../../models/operations/DeviceVerificationApiRequestBody.md) | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `serverURL`                                                                                     | *String*                                                                                        | :heavy_minus_sign:                                                                              | An optional server URL to use.                                                                  |

### Response

**[DeviceVerificationApiResponse](../../models/operations/DeviceVerificationApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## verifyForm

The API returns information associated with a user code.

<br>
<details>
<summary>Description</summary>

After receiving a response from the device authorization endpoint of the authorization server,
the client application shows the end-user the user code and the verification URI which are included
in the device authorization response. Then, the end-user will access the verification URI using
a web browser on another device (typically, a smart phone). In normal implementations, the verification
endpoint will return an HTML page with an input form where the end-user inputs a user code. The
authorization server will receive a user code from the form.

After receiving a user code, the authorization server should call Authlete's `/device/verification`
API with the user code. And then, the authorization server implementation should retrieve the value
of `action` parameter from the API response and take the following steps according to the value.

**SERVER_ERROR**

When the value of `action` is `SERVER_ERROR`, it means that an error occurred on Authlete side. The
authorization server implementation should tell the end-user that something wrong happened and
urge her to re-initiate a device flow.

**NOT_EXIST**

When the value of `action` is `NOT_EXIST`, it means that the user code does not exist. The authorization
server implementation should tell the end-user that the user code is invalid and urge her to retry
to input a valid user code.

**EXPIRED**

When the value of `action` is `EXPIRED`, it means that the user code has expired. The authorization
server implementation should tell the end-user that the user code has expired and urge her to
re-initiate a device flow.

**VALID**

When the value of `action` is `VALID`, it means that the user code exists, has not expired, and
belongs to the service. The authorization server implementation should interact with the end-user
to ask whether she approves or rejects the authorization request from the device.
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="device_verification_api_form" method="post" path="/api/{serviceId}/device/verification" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeviceVerificationApiFormRequestBody;
import org.openapis.openapi.models.operations.DeviceVerificationApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        DeviceVerificationApiFormResponse res = sdk.deviceFlow().verifyForm()
                .serviceId("<id>")
                .requestBody(DeviceVerificationApiFormRequestBody.builder()
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

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                             | *String*                                                                                                | :heavy_check_mark:                                                                                      | A service ID.                                                                                           |
| `requestBody`                                                                                           | [DeviceVerificationApiFormRequestBody](../../models/operations/DeviceVerificationApiFormRequestBody.md) | :heavy_check_mark:                                                                                      | N/A                                                                                                     |
| `serverURL`                                                                                             | *String*                                                                                                | :heavy_minus_sign:                                                                                      | An optional server URL to use.                                                                          |

### Response

**[DeviceVerificationApiFormResponse](../../models/operations/DeviceVerificationApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## complete

This API returns information about what action the authorization server should take after it receives
the result of end-user's decision about whether the end-user has approved or rejected a client
application's request.

<br>
<details>
<summary>Description</summary>

In the device flow, an end-user accesses the verification endpoint of the authorization server where
she interacts with the verification endpoint and inputs a user code. The verification endpoint checks
if the user code is valid and then asks the end-user whether she approves or rejects the authorization
request which the user code represents.

After the authorization server receives the decision of the end-user, it should call Authlete's
`/device/complete` API to tell Authlete the decision.

When the end-user was authenticated and authorization was granted to the client by the end-user,
the authorization server should call the API with `result=AUTHORIZED`. In this successful case,
the subject request parameter is mandatory. The API will update the database record so that `/auth/token`
API can generate an access token later.

If the `scope` parameter of the device authorization request included the openid scope, an ID token
is generated. In this case, `sub`, `authTime`, `acr` and `claims` request parameters in the API
call to `/device/complete` affect the ID token.

When the authorization server receives the decision of the end-user and it indicates that she has
rejected to give authorization to the client, the authorization server should call the API with
`result=ACCESS_DENIED`. In this case, the API will update the database record so that the `/auth/token`
API can generate an error response later. If `errorDescription` and `errorUri` request parameters
are given to the `/device/complete` API, they will be used as the values of `error_description`
and `error_uri` response parameters in the error response from the token endpoint.

When the authorization server could not get decision from the end-user for some reasons, the authorization
server should call the API with `result=TRANSACTION_FAILED`. In this error case, the API will behave
in the same way as in the case of `ACCESS_DENIED`. The only difference is that `expired_token` is
used as the value of the `error` response parameter instead of `access_denied`.

After receiving a response from the `/device/complete` API, the implementation of the authorization
server should retrieve the value of `action` from the response and take the following steps according
to the value.

**SERVER_ERROR**

When the value of `action` is `SERVER_ERROR`, it means that an error occurred on Authlete side. The
authorization server implementation should tell the end-user that something wrong happened and
urge her to re-initiate a device flow.

**USER_CODE_NOT_EXIST**

When the value of `action` is `USER_CODE_NOT_EXIST`, it means that the user code included in the API
call does not exist. The authorization server implementation should tell the end-user that the user
code has been invalidated and urge her to re-initiate a device flow.

**USER_CODE_EXPIRED**

When the value of `action` is `USER_CODE_EXPIRED`,  it means that the user code included in the API
call has expired. The authorization server implementation should tell the end-user that the user
code has expired and urge her to re-initiate a device flow.

**INVALID_REQUEST**

When the value of `action` is `INVALID_REQUEST`, it means that the API call is invalid. Probably,
the authorization server implementation has some bugs.

**SUCCESS**

When the value of `action` is `SUCCESS`, it means that the API call has been processed successfully.
The authorization server should return a successful response to the web browser the end-user is
using.
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="device_complete_api" method="post" path="/api/{serviceId}/device/complete" -->
```java
package hello.world;

import java.lang.Exception;
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

        DeviceCompleteApiResponse res = sdk.deviceFlow().complete()
                .serviceId("<id>")
                .requestBody(DeviceCompleteApiRequestBody.builder()
                    .userCode("XWWKPBWVXQ")
                    .result(DeviceCompleteApiResult.AUTHORIZED)
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

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `serviceId`                                                                             | *String*                                                                                | :heavy_check_mark:                                                                      | A service ID.                                                                           |
| `requestBody`                                                                           | [DeviceCompleteApiRequestBody](../../models/operations/DeviceCompleteApiRequestBody.md) | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `serverURL`                                                                             | *String*                                                                                | :heavy_minus_sign:                                                                      | An optional server URL to use.                                                          |

### Response

**[DeviceCompleteApiResponse](../../models/operations/DeviceCompleteApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## completeForm

This API returns information about what action the authorization server should take after it receives
the result of end-user's decision about whether the end-user has approved or rejected a client
application's request.

<br>
<details>
<summary>Description</summary>

In the device flow, an end-user accesses the verification endpoint of the authorization server where
she interacts with the verification endpoint and inputs a user code. The verification endpoint checks
if the user code is valid and then asks the end-user whether she approves or rejects the authorization
request which the user code represents.

After the authorization server receives the decision of the end-user, it should call Authlete's
`/device/complete` API to tell Authlete the decision.

When the end-user was authenticated and authorization was granted to the client by the end-user,
the authorization server should call the API with `result=AUTHORIZED`. In this successful case,
the subject request parameter is mandatory. The API will update the database record so that `/auth/token`
API can generate an access token later.

If the `scope` parameter of the device authorization request included the openid scope, an ID token
is generated. In this case, `sub`, `authTime`, `acr` and `claims` request parameters in the API
call to `/device/complete` affect the ID token.

When the authorization server receives the decision of the end-user and it indicates that she has
rejected to give authorization to the client, the authorization server should call the API with
`result=ACCESS_DENIED`. In this case, the API will update the database record so that the `/auth/token`
API can generate an error response later. If `errorDescription` and `errorUri` request parameters
are given to the `/device/complete` API, they will be used as the values of `error_description`
and `error_uri` response parameters in the error response from the token endpoint.

When the authorization server could not get decision from the end-user for some reasons, the authorization
server should call the API with `result=TRANSACTION_FAILED`. In this error case, the API will behave
in the same way as in the case of `ACCESS_DENIED`. The only difference is that `expired_token` is
used as the value of the `error` response parameter instead of `access_denied`.

After receiving a response from the `/device/complete` API, the implementation of the authorization
server should retrieve the value of `action` from the response and take the following steps according
to the value.

**SERVER_ERROR**

When the value of `action` is `SERVER_ERROR`, it means that an error occurred on Authlete side. The
authorization server implementation should tell the end-user that something wrong happened and
urge her to re-initiate a device flow.

**USER_CODE_NOT_EXIST**

When the value of `action` is `USER_CODE_NOT_EXIST`, it means that the user code included in the API
call does not exist. The authorization server implementation should tell the end-user that the user
code has been invalidated and urge her to re-initiate a device flow.

**USER_CODE_EXPIRED**

When the value of `action` is `USER_CODE_EXPIRED`,  it means that the user code included in the API
call has expired. The authorization server implementation should tell the end-user that the user
code has expired and urge her to re-initiate a device flow.

**INVALID_REQUEST**

When the value of `action` is `INVALID_REQUEST`, it means that the API call is invalid. Probably,
the authorization server implementation has some bugs.

**SUCCESS**

When the value of `action` is `SUCCESS`, it means that the API call has been processed successfully.
The authorization server should return a successful response to the web browser the end-user is
using.
</details>


### Example Usage

<!-- UsageSnippet language="java" operationID="device_complete_api_form" method="post" path="/api/{serviceId}/device/complete" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeviceCompleteApiFormRequestBody;
import org.openapis.openapi.models.operations.DeviceCompleteApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        DeviceCompleteApiFormResponse res = sdk.deviceFlow().completeForm()
                .serviceId("<id>")
                .requestBody(DeviceCompleteApiFormRequestBody.builder()
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

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                     | *String*                                                                                        | :heavy_check_mark:                                                                              | A service ID.                                                                                   |
| `requestBody`                                                                                   | [DeviceCompleteApiFormRequestBody](../../models/operations/DeviceCompleteApiFormRequestBody.md) | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `serverURL`                                                                                     | *String*                                                                                        | :heavy_minus_sign:                                                                              | An optional server URL to use.                                                                  |

### Response

**[DeviceCompleteApiFormResponse](../../models/operations/DeviceCompleteApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |