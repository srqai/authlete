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

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciMetadataApiRequestBody;
import org.openapis.openapi.models.operations.VciMetadataApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciMetadataApiResponse](../../models/operations/VciMetadataApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## getMetadataForm

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1vci1metadataPostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciMetadataApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciMetadataApiFormResponse res = sdk.verifiableCredentialIssuer().getMetadataForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1vci1metadataPostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1vci1metadataPostRequestBodyContentApplication1jsonSchema.builder()
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

| Parameter                                                                                                                                                                                                           | Type                                                                                                                                                                                                                | Required                                                                                                                                                                                                            | Description                                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                         | *String*                                                                                                                                                                                                            | :heavy_check_mark:                                                                                                                                                                                                  | A service ID.                                                                                                                                                                                                       |
| `1api1Percent7BserviceIdPercent7D1vci1metadataPostRequestBodyContentApplication1jsonSchema`                                                                                                                         | [1api1Percent7BserviceIdPercent7D1vci1metadataPostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1vci1metadataPostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                  | N/A                                                                                                                                                                                                                 |

### Response

**[VciMetadataApiFormResponse](../../models/operations/VciMetadataApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## postJwks

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciJwksApiRequestBody;
import org.openapis.openapi.models.operations.VciJwksApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciJwksApiResponse](../../models/operations/VciJwksApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## postJwksForm

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1vci1jwksPostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciJwksApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciJwksApiFormResponse res = sdk.verifiableCredentialIssuer().postJwksForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1vci1jwksPostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1vci1jwksPostRequestBodyContentApplication1jsonSchema.builder()
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

| Parameter                                                                                                                                                                                                   | Type                                                                                                                                                                                                        | Required                                                                                                                                                                                                    | Description                                                                                                                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                 | *String*                                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                          | A service ID.                                                                                                                                                                                               |
| `1api1Percent7BserviceIdPercent7D1vci1jwksPostRequestBodyContentApplication1jsonSchema`                                                                                                                     | [1api1Percent7BserviceIdPercent7D1vci1jwksPostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1vci1jwksPostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                          | N/A                                                                                                                                                                                                         |

### Response

**[VciJwksApiFormResponse](../../models/operations/VciJwksApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## createOffer

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciOfferCreateApiRequestBody;
import org.openapis.openapi.models.operations.VciOfferCreateApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciOfferCreateApiResponse](../../models/operations/VciOfferCreateApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## createOfferForm

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1vci1offer1createPostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciOfferCreateApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciOfferCreateApiFormResponse res = sdk.verifiableCredentialIssuer().createOfferForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1vci1offer1createPostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1vci1offer1createPostRequestBodyContentApplication1jsonSchema.builder()
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                   | Type                                                                                                                                                                                                                        | Required                                                                                                                                                                                                                    | Description                                                                                                                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                                 | *String*                                                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                                          | A service ID.                                                                                                                                                                                                               |
| `1api1Percent7BserviceIdPercent7D1vci1offer1createPostRequestBodyContentApplication1jsonSchema`                                                                                                                             | [1api1Percent7BserviceIdPercent7D1vci1offer1createPostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1vci1offer1createPostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                          | N/A                                                                                                                                                                                                                         |

### Response

**[VciOfferCreateApiFormResponse](../../models/operations/VciOfferCreateApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## getOfferInfo

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciOfferInfoApiRequestBody;
import org.openapis.openapi.models.operations.VciOfferInfoApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciOfferInfoApiResponse](../../models/operations/VciOfferInfoApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## getOfferInfoForm

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1vci1offer1infoPostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciOfferInfoApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciOfferInfoApiFormResponse res = sdk.verifiableCredentialIssuer().getOfferInfoForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1vci1offer1infoPostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1vci1offer1infoPostRequestBodyContentApplication1jsonSchema.builder()
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                               | Type                                                                                                                                                                                                                    | Required                                                                                                                                                                                                                | Description                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                             | *String*                                                                                                                                                                                                                | :heavy_check_mark:                                                                                                                                                                                                      | A service ID.                                                                                                                                                                                                           |
| `1api1Percent7BserviceIdPercent7D1vci1offer1infoPostRequestBodyContentApplication1jsonSchema`                                                                                                                           | [1api1Percent7BserviceIdPercent7D1vci1offer1infoPostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1vci1offer1infoPostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                      | N/A                                                                                                                                                                                                                     |

### Response

**[VciOfferInfoApiFormResponse](../../models/operations/VciOfferInfoApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## issueSingle

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciSingleIssueApiRequestBody;
import org.openapis.openapi.models.operations.VciSingleIssueApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciSingleIssueApiResponse](../../models/operations/VciSingleIssueApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## batchParse

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciBatchParseApiRequestBody;
import org.openapis.openapi.models.operations.VciBatchParseApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciBatchParseApiResponse](../../models/operations/VciBatchParseApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## batchParseForm

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1vci1batch1parsePostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciBatchParseApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciBatchParseApiFormResponse res = sdk.verifiableCredentialIssuer().batchParseForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1vci1batch1parsePostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1vci1batch1parsePostRequestBodyContentApplication1jsonSchema.builder()
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                 | Type                                                                                                                                                                                                                      | Required                                                                                                                                                                                                                  | Description                                                                                                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                               | *String*                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                        | A service ID.                                                                                                                                                                                                             |
| `1api1Percent7BserviceIdPercent7D1vci1batch1parsePostRequestBodyContentApplication1jsonSchema`                                                                                                                            | [1api1Percent7BserviceIdPercent7D1vci1batch1parsePostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1vci1batch1parsePostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                        | N/A                                                                                                                                                                                                                       |

### Response

**[VciBatchParseApiFormResponse](../../models/operations/VciBatchParseApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## parseDeferred

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciDeferredParseApiRequestBody;
import org.openapis.openapi.models.operations.VciDeferredParseApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciDeferredParseApiResponse](../../models/operations/VciDeferredParseApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## parseDeferredForm

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.1api1Percent7BserviceIdPercent7D1vci1deferred1parsePostRequestBodyContentApplication1jsonSchema;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciDeferredParseApiFormResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        VciDeferredParseApiFormResponse res = sdk.verifiableCredentialIssuer().parseDeferredForm()
                .serviceId("<id>")
                .1api1Percent7BserviceIdPercent7D1vci1deferred1parsePostRequestBodyContentApplication1jsonSchema(1api1Percent7BserviceIdPercent7D1vci1deferred1parsePostRequestBodyContentApplication1jsonSchema.builder()
                    .build())
                .call();

        if (res.object().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                                       | Type                                                                                                                                                                                                                            | Required                                                                                                                                                                                                                        | Description                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `serviceId`                                                                                                                                                                                                                     | *String*                                                                                                                                                                                                                        | :heavy_check_mark:                                                                                                                                                                                                              | A service ID.                                                                                                                                                                                                                   |
| `1api1Percent7BserviceIdPercent7D1vci1deferred1parsePostRequestBodyContentApplication1jsonSchema`                                                                                                                               | [1api1Percent7BserviceIdPercent7D1vci1deferred1parsePostRequestBodyContentApplication1jsonSchema](../../models/components/Oneapi1Percent7BserviceIdPercent7D1vci1deferred1parsePostRequestBodyContentApplication1jsonSchema.md) | :heavy_check_mark:                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                             |

### Response

**[VciDeferredParseApiFormResponse](../../models/operations/VciDeferredParseApiFormResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |

## issueDeferred

null

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.VciDeferredIssueApiRequestBody;
import org.openapis.openapi.models.operations.VciDeferredIssueApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

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

### Response

**[VciDeferredIssueApiResponse](../../models/operations/VciDeferredIssueApiResponse.md)**

### Errors

| Error Type                                                                   | Status Code                                                                  | Content Type                                                                 |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400                                                                          | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403                                                                     | application/json                                                             |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500                                                                          | application/json                                                             |
| models/errors/APIException                                                   | 4XX, 5XX                                                                     | \*/\*                                                                        |