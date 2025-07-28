# Authentication
(*authentication*)

## Overview

Some endpoints are public, but some require authentication. We provide all the required endpoints to create an account and authorize yourself.

### Available Operations

* [createUserJson](#createuserjson) - Create a user
* [createUserRaw](#createuserraw) - Create a user
* [getTokenJson](#gettokenjson) - Get a token
* [getTokenRaw](#gettokenraw) - Get a token
* [getMe](#getme) - Get authenticated user

## createUserJson

Time to create a user account, eh?

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.authentication.createUserJson({
    name: "Marc",
    email: "marc@scalar.com",
    password: "i-love-scalar",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { authenticationCreateUserJson } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/authenticationCreateUserJson.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await authenticationCreateUserJson(scalarGalaxyTypescript, {
    name: "Marc",
    email: "marc@scalar.com",
    password: "i-love-scalar",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("authenticationCreateUserJson failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CreateUserJsonRequestBody](../../models/operations/createuserjsonrequestbody.md)                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.CreateUserJsonResponse](../../models/operations/createuserjsonresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## createUserRaw

Time to create a user account, eh?

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.authentication.createUserRaw(bytesToStream(new TextEncoder().encode("{\"name\":\"Marc\",\"email\":\"marc@scalar.com\",\"password\":\"i-love-scalar\"}")));

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { authenticationCreateUserRaw } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/authenticationCreateUserRaw.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await authenticationCreateUserRaw(scalarGalaxyTypescript, bytesToStream(new TextEncoder().encode("{\"name\":\"Marc\",\"email\":\"marc@scalar.com\",\"password\":\"i-love-scalar\"}")));
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("authenticationCreateUserRaw failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [ReadableStream<Uint8Array>](../../models/requestbody.md)                                                                                                                      | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.CreateUserRawResponse](../../models/operations/createuserrawresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## getTokenJson

Yeah, this is the boring security stuff. Just get your super secret token and move on.

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.authentication.getTokenJson({
    email: "marc@scalar.com",
    password: "i-love-scalar",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { authenticationGetTokenJson } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/authenticationGetTokenJson.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await authenticationGetTokenJson(scalarGalaxyTypescript, {
    email: "marc@scalar.com",
    password: "i-love-scalar",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("authenticationGetTokenJson failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [components.Credentials](../../models/components/credentials.md)                                                                                                               | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.GetTokenJsonResponse](../../models/operations/gettokenjsonresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## getTokenRaw

Yeah, this is the boring security stuff. Just get your super secret token and move on.

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.authentication.getTokenRaw(bytesToStream(new TextEncoder().encode("{\"email\":\"marc@scalar.com\",\"password\":\"i-love-scalar\"}")));

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { authenticationGetTokenRaw } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/authenticationGetTokenRaw.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await authenticationGetTokenRaw(scalarGalaxyTypescript, bytesToStream(new TextEncoder().encode("{\"email\":\"marc@scalar.com\",\"password\":\"i-love-scalar\"}")));
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("authenticationGetTokenRaw failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [ReadableStream<Uint8Array>](../../models/credentials.md)                                                                                                                      | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.GetTokenRawResponse](../../models/operations/gettokenrawresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## getMe

Find yourself they say. That’s what you can do here.

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.authentication.getMe();

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { authenticationGetMe } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/authenticationGetMe.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await authenticationGetMe(scalarGalaxyTypescript);
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("authenticationGetMe failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.GetMeResponse](../../models/operations/getmeresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |