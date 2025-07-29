# VerifiableCredentialIssuer
(*verifiableCredentialIssuer()*)

## Overview

### Available Operations

* [getMetadata](#getmetadata) - /api/{serviceId}/vci/metadata API
* [getMetadataForm](#getmetadataform) - /api/{serviceId}/vci/metadata API
* [postJwks](#postjwks) - /api/{serviceId}/vci/jwks API
* [postJwksForm](#postjwksform) - /api/{serviceId}/vci/jwks API
* [createOffer](#createoffer) - /api/{serviceId}/vci/offer/create API
* [createOfferForm](#createofferform) - /api/{serviceId}/vci/offer/create API
* [getOfferInfo](#getofferinfo) - /api/{serviceId}/vci/offer/info API
* [getOfferInfoForm](#getofferinfoform) - /api/{serviceId}/vci/offer/info API
* [issueSingle](#issuesingle) - /api/{serviceId}/vci/single/issue API
* [batchParse](#batchparse) - /api/{serviceId}/vci/batch/parse API
* [batchParseForm](#batchparseform) - /api/{serviceId}/vci/batch/parse API
* [parseDeferred](#parsedeferred) - /api/{serviceId}/vci/deferred/parse API
* [parseDeferredForm](#parsedeferredform) - /api/{serviceId}/vci/deferred/parse API
* [issueDeferred](#issuedeferred) - /api/{serviceId}/vci/deferred/issue API

## getMetadata

/api/{serviceId}/vci/metadata API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_metadata_api" method="post" path="/api/{serviceId}/vci/metadata" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciMetadataApiRequestBody;
import org.openapis.openapi.models.operations.VciMetadataApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciMetadataApiResponse res = sdk.verifiableCredentialIssuer().getMetadata()
                .serviceId("<id>")
                .requestBody(VciMetadataApiRequestBody.builder()
                    .pretty(true)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `serviceId`                                                                       | *String*                                                                          | :heavy_check_mark:                                                                | A service ID.                                                                     |
| `requestBody`                                                                     | [VciMetadataApiRequestBody](../../models/operations/VciMetadataApiRequestBody.md) | :heavy_check_mark:                                                                | N/A                                                                               |
| `serverURL`                                                                       | *String*                                                                          | :heavy_minus_sign:                                                                | An optional server URL to use.                                                    |

### Response

**[VciMetadataApiResponse](../../models/operations/VciMetadataApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## getMetadataForm

/api/{serviceId}/vci/metadata API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_metadata_api_form" method="post" path="/api/{serviceId}/vci/metadata" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciMetadataApiFormRequestBody;
import org.openapis.openapi.models.operations.VciMetadataApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciMetadataApiFormResponse res = sdk.verifiableCredentialIssuer().getMetadataForm()
                .serviceId("<id>")
                .requestBody(VciMetadataApiFormRequestBody.builder()
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

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `serviceId`                                                                               | *String*                                                                                  | :heavy_check_mark:                                                                        | A service ID.                                                                             |
| `requestBody`                                                                             | [VciMetadataApiFormRequestBody](../../models/operations/VciMetadataApiFormRequestBody.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |
| `serverURL`                                                                               | *String*                                                                                  | :heavy_minus_sign:                                                                        | An optional server URL to use.                                                            |

### Response

**[VciMetadataApiFormResponse](../../models/operations/VciMetadataApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## postJwks

/api/{serviceId}/vci/jwks API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_jwks_api" method="post" path="/api/{serviceId}/vci/jwks" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciJwksApiRequestBody;
import org.openapis.openapi.models.operations.VciJwksApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciJwksApiResponse res = sdk.verifiableCredentialIssuer().postJwks()
                .serviceId("<id>")
                .requestBody(VciJwksApiRequestBody.builder()
                    .pretty(false)
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `serviceId`                                                               | *String*                                                                  | :heavy_check_mark:                                                        | A service ID.                                                             |
| `requestBody`                                                             | [VciJwksApiRequestBody](../../models/operations/VciJwksApiRequestBody.md) | :heavy_check_mark:                                                        | N/A                                                                       |
| `serverURL`                                                               | *String*                                                                  | :heavy_minus_sign:                                                        | An optional server URL to use.                                            |

### Response

**[VciJwksApiResponse](../../models/operations/VciJwksApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## postJwksForm

/api/{serviceId}/vci/jwks API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_jwks_api_form" method="post" path="/api/{serviceId}/vci/jwks" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciJwksApiFormRequestBody;
import org.openapis.openapi.models.operations.VciJwksApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciJwksApiFormResponse res = sdk.verifiableCredentialIssuer().postJwksForm()
                .serviceId("<id>")
                .requestBody(VciJwksApiFormRequestBody.builder()
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

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `serviceId`                                                                       | *String*                                                                          | :heavy_check_mark:                                                                | A service ID.                                                                     |
| `requestBody`                                                                     | [VciJwksApiFormRequestBody](../../models/operations/VciJwksApiFormRequestBody.md) | :heavy_check_mark:                                                                | N/A                                                                               |
| `serverURL`                                                                       | *String*                                                                          | :heavy_minus_sign:                                                                | An optional server URL to use.                                                    |

### Response

**[VciJwksApiFormResponse](../../models/operations/VciJwksApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## createOffer

/api/{serviceId}/vci/offer/create API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_offer_create_api" method="post" path="/api/{serviceId}/vci/offer/create" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciOfferCreateApiRequestBody;
import org.openapis.openapi.models.operations.VciOfferCreateApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciOfferCreateApiResponse res = sdk.verifiableCredentialIssuer().createOffer()
                .serviceId("<id>")
                .requestBody(VciOfferCreateApiRequestBody.builder()
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
| `requestBody`                                                                           | [VciOfferCreateApiRequestBody](../../models/operations/VciOfferCreateApiRequestBody.md) | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `serverURL`                                                                             | *String*                                                                                | :heavy_minus_sign:                                                                      | An optional server URL to use.                                                          |

### Response

**[VciOfferCreateApiResponse](../../models/operations/VciOfferCreateApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## createOfferForm

/api/{serviceId}/vci/offer/create API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_offer_create_api_form" method="post" path="/api/{serviceId}/vci/offer/create" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciOfferCreateApiFormRequestBody;
import org.openapis.openapi.models.operations.VciOfferCreateApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciOfferCreateApiFormResponse res = sdk.verifiableCredentialIssuer().createOfferForm()
                .serviceId("<id>")
                .requestBody(VciOfferCreateApiFormRequestBody.builder()
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

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                     | *String*                                                                                        | :heavy_check_mark:                                                                              | A service ID.                                                                                   |
| `requestBody`                                                                                   | [VciOfferCreateApiFormRequestBody](../../models/operations/VciOfferCreateApiFormRequestBody.md) | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `serverURL`                                                                                     | *String*                                                                                        | :heavy_minus_sign:                                                                              | An optional server URL to use.                                                                  |

### Response

**[VciOfferCreateApiFormResponse](../../models/operations/VciOfferCreateApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## getOfferInfo

/api/{serviceId}/vci/offer/info API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_offer_info_api" method="post" path="/api/{serviceId}/vci/offer/info" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciOfferInfoApiRequestBody;
import org.openapis.openapi.models.operations.VciOfferInfoApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciOfferInfoApiResponse res = sdk.verifiableCredentialIssuer().getOfferInfo()
                .serviceId("<id>")
                .requestBody(VciOfferInfoApiRequestBody.builder()
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
| `requestBody`                                                                       | [VciOfferInfoApiRequestBody](../../models/operations/VciOfferInfoApiRequestBody.md) | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `serverURL`                                                                         | *String*                                                                            | :heavy_minus_sign:                                                                  | An optional server URL to use.                                                      |

### Response

**[VciOfferInfoApiResponse](../../models/operations/VciOfferInfoApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## getOfferInfoForm

/api/{serviceId}/vci/offer/info API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_offer_info_api_form" method="post" path="/api/{serviceId}/vci/offer/info" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciOfferInfoApiFormRequestBody;
import org.openapis.openapi.models.operations.VciOfferInfoApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciOfferInfoApiFormResponse res = sdk.verifiableCredentialIssuer().getOfferInfoForm()
                .serviceId("<id>")
                .requestBody(VciOfferInfoApiFormRequestBody.builder()
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
| `requestBody`                                                                               | [VciOfferInfoApiFormRequestBody](../../models/operations/VciOfferInfoApiFormRequestBody.md) | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `serverURL`                                                                                 | *String*                                                                                    | :heavy_minus_sign:                                                                          | An optional server URL to use.                                                              |

### Response

**[VciOfferInfoApiFormResponse](../../models/operations/VciOfferInfoApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## issueSingle

/api/{serviceId}/vci/single/issue API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_single_issue_api" method="post" path="/api/{serviceId}/vci/single/issue" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciSingleIssueApiRequestBody;
import org.openapis.openapi.models.operations.VciSingleIssueApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciSingleIssueApiResponse res = sdk.verifiableCredentialIssuer().issueSingle()
                .serviceId("<id>")
                .requestBody(VciSingleIssueApiRequestBody.builder()
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
| `requestBody`                                                                           | [VciSingleIssueApiRequestBody](../../models/operations/VciSingleIssueApiRequestBody.md) | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `serverURL`                                                                             | *String*                                                                                | :heavy_minus_sign:                                                                      | An optional server URL to use.                                                          |

### Response

**[VciSingleIssueApiResponse](../../models/operations/VciSingleIssueApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## batchParse

/api/{serviceId}/vci/batch/parse API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_batch_parse_api" method="post" path="/api/{serviceId}/vci/batch/parse" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciBatchParseApiRequestBody;
import org.openapis.openapi.models.operations.VciBatchParseApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciBatchParseApiResponse res = sdk.verifiableCredentialIssuer().batchParse()
                .serviceId("<id>")
                .requestBody(VciBatchParseApiRequestBody.builder()
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
| `requestBody`                                                                         | [VciBatchParseApiRequestBody](../../models/operations/VciBatchParseApiRequestBody.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `serverURL`                                                                           | *String*                                                                              | :heavy_minus_sign:                                                                    | An optional server URL to use.                                                        |

### Response

**[VciBatchParseApiResponse](../../models/operations/VciBatchParseApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## batchParseForm

/api/{serviceId}/vci/batch/parse API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_batch_parse_api_form" method="post" path="/api/{serviceId}/vci/batch/parse" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciBatchParseApiFormRequestBody;
import org.openapis.openapi.models.operations.VciBatchParseApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciBatchParseApiFormResponse res = sdk.verifiableCredentialIssuer().batchParseForm()
                .serviceId("<id>")
                .requestBody(VciBatchParseApiFormRequestBody.builder()
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
| `requestBody`                                                                                 | [VciBatchParseApiFormRequestBody](../../models/operations/VciBatchParseApiFormRequestBody.md) | :heavy_check_mark:                                                                            | N/A                                                                                           |
| `serverURL`                                                                                   | *String*                                                                                      | :heavy_minus_sign:                                                                            | An optional server URL to use.                                                                |

### Response

**[VciBatchParseApiFormResponse](../../models/operations/VciBatchParseApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## parseDeferred

/api/{serviceId}/vci/deferred/parse API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_deferred_parse_api" method="post" path="/api/{serviceId}/vci/deferred/parse" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciDeferredParseApiRequestBody;
import org.openapis.openapi.models.operations.VciDeferredParseApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciDeferredParseApiResponse res = sdk.verifiableCredentialIssuer().parseDeferred()
                .serviceId("<id>")
                .requestBody(VciDeferredParseApiRequestBody.builder()
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
| `requestBody`                                                                               | [VciDeferredParseApiRequestBody](../../models/operations/VciDeferredParseApiRequestBody.md) | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `serverURL`                                                                                 | *String*                                                                                    | :heavy_minus_sign:                                                                          | An optional server URL to use.                                                              |

### Response

**[VciDeferredParseApiResponse](../../models/operations/VciDeferredParseApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## parseDeferredForm

/api/{serviceId}/vci/deferred/parse API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_deferred_parse_api_form" method="post" path="/api/{serviceId}/vci/deferred/parse" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciDeferredParseApiFormRequestBody;
import org.openapis.openapi.models.operations.VciDeferredParseApiFormResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciDeferredParseApiFormResponse res = sdk.verifiableCredentialIssuer().parseDeferredForm()
                .serviceId("<id>")
                .requestBody(VciDeferredParseApiFormRequestBody.builder()
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

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                         | *String*                                                                                            | :heavy_check_mark:                                                                                  | A service ID.                                                                                       |
| `requestBody`                                                                                       | [VciDeferredParseApiFormRequestBody](../../models/operations/VciDeferredParseApiFormRequestBody.md) | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `serverURL`                                                                                         | *String*                                                                                            | :heavy_minus_sign:                                                                                  | An optional server URL to use.                                                                      |

### Response

**[VciDeferredParseApiFormResponse](../../models/operations/VciDeferredParseApiFormResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |

## issueDeferred

/api/{serviceId}/vci/deferred/issue API

### Example Usage

<!-- UsageSnippet language="java" operationID="vci_deferred_issue_api" method="post" path="/api/{serviceId}/vci/deferred/issue" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.VciDeferredIssueApiRequestBody;
import org.openapis.openapi.models.operations.VciDeferredIssueApiResponse;

public class Application {

    public static void main(String[] args) throws BadRequestException, UnauthorizedException, ForbiddenException, InternalServerError, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciDeferredIssueApiResponse res = sdk.verifiableCredentialIssuer().issueDeferred()
                .serviceId("<id>")
                .requestBody(VciDeferredIssueApiRequestBody.builder()
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
| `requestBody`                                                                               | [VciDeferredIssueApiRequestBody](../../models/operations/VciDeferredIssueApiRequestBody.md) | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `serverURL`                                                                                 | *String*                                                                                    | :heavy_minus_sign:                                                                          | An optional server URL to use.                                                              |

### Response

**[VciDeferredIssueApiResponse](../../models/operations/VciDeferredIssueApiResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| models/errors/BadRequestException   | 400                                 | application/json                    |
| models/errors/UnauthorizedException | 401                                 | application/json                    |
| models/errors/ForbiddenException    | 403                                 | application/json                    |
| models/errors/InternalServerError   | 500                                 | application/json                    |
| models/errors/APIException          | 4XX, 5XX                            | \*/\*                               |