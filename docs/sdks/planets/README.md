# Planets
(*planets*)

## Overview

Everything about planets

### Available Operations

* [getAllData](#getalldata) - Get all planets
* [createPlanetJson](#createplanetjson) - Create a planet
* [createPlanetRaw](#createplanetraw) - Create a planet
* [getPlanet](#getplanet) - Get a planet
* [updatePlanetJson](#updateplanetjson) - Update a planet
* [updatePlanetRaw](#updateplanetraw) - Update a planet
* [deletePlanet](#deleteplanet) - Delete a planet
* [uploadImage](#uploadimage) - Upload an image to a planet

## getAllData

It’s easy to say you know them all, but do you really? Retrieve all the planets and check whether you missed one.

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.planets.getAllData({});

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { planetsGetAllData } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/planetsGetAllData.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await planetsGetAllData(scalarGalaxyTypescript, {});
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("planetsGetAllData failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetAllDataRequest](../../models/operations/getalldatarequest.md)                                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.GetAllDataResponse](../../models/operations/getalldataresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## createPlanetJson

Time to play god and create a new planet. What do you think? Ah, don’t think too much. What could go wrong anyway?

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.planets.createPlanetJson({
    name: "Mars",
    description: "The red planet",
    type: "terrestrial",
    habitabilityIndex: 0.68,
    physicalProperties: {
      mass: 0.107,
      radius: 0.532,
      gravity: 0.378,
      temperature: {
        min: 130,
        max: 308,
        average: 210,
      },
    },
    atmosphere: [
      {
        compound: "CO2",
        percentage: 95.3,
      },
    ],
    discoveredAt: new Date("1610-01-07T00:00:00Z"),
    image: "https://cdn.scalar.com/photos/mars.jpg",
    satellites: [
      {
        name: "Phobos",
        diameter: 22.2,
      },
    ],
    creator: {
      name: "Marc",
    },
    tags: [
      "solar-system",
      "rocky",
      "explored",
    ],
    callbackUrl: "https://example.com/webhook",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { planetsCreatePlanetJson } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/planetsCreatePlanetJson.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await planetsCreatePlanetJson(scalarGalaxyTypescript, {
    name: "Mars",
    description: "The red planet",
    type: "terrestrial",
    habitabilityIndex: 0.68,
    physicalProperties: {
      mass: 0.107,
      radius: 0.532,
      gravity: 0.378,
      temperature: {
        min: 130,
        max: 308,
        average: 210,
      },
    },
    atmosphere: [
      {
        compound: "CO2",
        percentage: 95.3,
      },
    ],
    discoveredAt: new Date("1610-01-07T00:00:00Z"),
    image: "https://cdn.scalar.com/photos/mars.jpg",
    satellites: [
      {
        name: "Phobos",
        diameter: 22.2,
      },
    ],
    creator: {
      name: "Marc",
    },
    tags: [
      "solar-system",
      "rocky",
      "explored",
    ],
    callbackUrl: "https://example.com/webhook",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("planetsCreatePlanetJson failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [components.PlanetInput](../../models/components/planetinput.md)                                                                                                               | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.CreatePlanetJsonResponse](../../models/operations/createplanetjsonresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## createPlanetRaw

Time to play god and create a new planet. What do you think? Ah, don’t think too much. What could go wrong anyway?

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.planets.createPlanetRaw(bytesToStream(new TextEncoder().encode("{\"name\":\"Mars\",\"description\":\"The red planet\",\"type\":\"terrestrial\",\"habitabilityIndex\":0.68,\"physicalProperties\":{\"mass\":0.107,\"radius\":0.532,\"gravity\":0.378,\"temperature\":{\"min\":130,\"max\":308,\"average\":210}},\"atmosphere\":[{\"compound\":\"CO2\",\"percentage\":95.3}],\"discoveredAt\":\"1610-01-07T00:00:00Z\",\"image\":\"https://cdn.scalar.com/photos/mars.jpg\",\"satellites\":[{\"name\":\"Phobos\",\"diameter\":22.2}],\"creator\":{\"name\":\"Marc\"},\"tags\":[\"solar-system\",\"rocky\",\"explored\"],\"callbackUrl\":\"https://example.com/webhook\"}")));

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { planetsCreatePlanetRaw } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/planetsCreatePlanetRaw.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await planetsCreatePlanetRaw(scalarGalaxyTypescript, bytesToStream(new TextEncoder().encode("{\"name\":\"Mars\",\"description\":\"The red planet\",\"type\":\"terrestrial\",\"habitabilityIndex\":0.68,\"physicalProperties\":{\"mass\":0.107,\"radius\":0.532,\"gravity\":0.378,\"temperature\":{\"min\":130,\"max\":308,\"average\":210}},\"atmosphere\":[{\"compound\":\"CO2\",\"percentage\":95.3}],\"discoveredAt\":\"1610-01-07T00:00:00Z\",\"image\":\"https://cdn.scalar.com/photos/mars.jpg\",\"satellites\":[{\"name\":\"Phobos\",\"diameter\":22.2}],\"creator\":{\"name\":\"Marc\"},\"tags\":[\"solar-system\",\"rocky\",\"explored\"],\"callbackUrl\":\"https://example.com/webhook\"}")));
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("planetsCreatePlanetRaw failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [ReadableStream<Uint8Array>](../../models/planet.md)                                                                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.CreatePlanetRawResponse](../../models/operations/createplanetrawresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## getPlanet

You’ll better learn a little bit more about the planets. It might come in handy once space travel is available for everyone.

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.planets.getPlanet({
    planetId: 1,
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { planetsGetPlanet } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/planetsGetPlanet.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await planetsGetPlanet(scalarGalaxyTypescript, {
    planetId: 1,
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("planetsGetPlanet failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetPlanetRequest](../../models/operations/getplanetrequest.md)                                                                                                     | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.GetPlanetResponse](../../models/operations/getplanetresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## updatePlanetJson

Sometimes you make mistakes, that's fine. No worries, you can update all planets.

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.planets.updatePlanetJson({
    planetId: 1,
    planet: {
      name: "Mars",
      description: "The red planet",
      type: "terrestrial",
      habitabilityIndex: 0.68,
      physicalProperties: {
        mass: 0.107,
        radius: 0.532,
        gravity: 0.378,
        temperature: {
          min: 130,
          max: 308,
          average: 210,
        },
      },
      atmosphere: [
        {
          compound: "CO2",
          percentage: 95.3,
        },
      ],
      discoveredAt: new Date("1610-01-07T00:00:00Z"),
      image: "https://cdn.scalar.com/photos/mars.jpg",
      satellites: [
        {
          name: "Phobos",
          diameter: 22.2,
        },
      ],
      creator: {
        name: "Marc",
      },
      tags: [
        "solar-system",
        "rocky",
        "explored",
      ],
      callbackUrl: "https://example.com/webhook",
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { planetsUpdatePlanetJson } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/planetsUpdatePlanetJson.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await planetsUpdatePlanetJson(scalarGalaxyTypescript, {
    planetId: 1,
    planet: {
      name: "Mars",
      description: "The red planet",
      type: "terrestrial",
      habitabilityIndex: 0.68,
      physicalProperties: {
        mass: 0.107,
        radius: 0.532,
        gravity: 0.378,
        temperature: {
          min: 130,
          max: 308,
          average: 210,
        },
      },
      atmosphere: [
        {
          compound: "CO2",
          percentage: 95.3,
        },
      ],
      discoveredAt: new Date("1610-01-07T00:00:00Z"),
      image: "https://cdn.scalar.com/photos/mars.jpg",
      satellites: [
        {
          name: "Phobos",
          diameter: 22.2,
        },
      ],
      creator: {
        name: "Marc",
      },
      tags: [
        "solar-system",
        "rocky",
        "explored",
      ],
      callbackUrl: "https://example.com/webhook",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("planetsUpdatePlanetJson failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.UpdatePlanetJsonRequest](../../models/operations/updateplanetjsonrequest.md)                                                                                       | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.UpdatePlanetJsonResponse](../../models/operations/updateplanetjsonresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## updatePlanetRaw

Sometimes you make mistakes, that's fine. No worries, you can update all planets.

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.planets.updatePlanetRaw({
    planetId: 1,
    planet: bytesToStream(new TextEncoder().encode("{\"name\":\"Mars\",\"description\":\"The red planet\",\"type\":\"terrestrial\",\"habitabilityIndex\":0.68,\"physicalProperties\":{\"mass\":0.107,\"radius\":0.532,\"gravity\":0.378,\"temperature\":{\"min\":130,\"max\":308,\"average\":210}},\"atmosphere\":[{\"compound\":\"CO2\",\"percentage\":95.3}],\"discoveredAt\":\"1610-01-07T00:00:00Z\",\"image\":\"https://cdn.scalar.com/photos/mars.jpg\",\"satellites\":[{\"name\":\"Phobos\",\"diameter\":22.2}],\"creator\":{\"name\":\"Marc\"},\"tags\":[\"solar-system\",\"rocky\",\"explored\"],\"callbackUrl\":\"https://example.com/webhook\"}")),
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { planetsUpdatePlanetRaw } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/planetsUpdatePlanetRaw.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await planetsUpdatePlanetRaw(scalarGalaxyTypescript, {
    planetId: 1,
    planet: bytesToStream(new TextEncoder().encode("{\"name\":\"Mars\",\"description\":\"The red planet\",\"type\":\"terrestrial\",\"habitabilityIndex\":0.68,\"physicalProperties\":{\"mass\":0.107,\"radius\":0.532,\"gravity\":0.378,\"temperature\":{\"min\":130,\"max\":308,\"average\":210}},\"atmosphere\":[{\"compound\":\"CO2\",\"percentage\":95.3}],\"discoveredAt\":\"1610-01-07T00:00:00Z\",\"image\":\"https://cdn.scalar.com/photos/mars.jpg\",\"satellites\":[{\"name\":\"Phobos\",\"diameter\":22.2}],\"creator\":{\"name\":\"Marc\"},\"tags\":[\"solar-system\",\"rocky\",\"explored\"],\"callbackUrl\":\"https://example.com/webhook\"}")),
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("planetsUpdatePlanetRaw failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.UpdatePlanetRawRequest](../../models/operations/updateplanetrawrequest.md)                                                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.UpdatePlanetRawResponse](../../models/operations/updateplanetrawresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## deletePlanet

This endpoint was used to delete planets. Unfortunately, that caused a lot of trouble for planets with life. So, this endpoint is now deprecated and should not be used anymore.

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  await scalarGalaxyTypescript.planets.deletePlanet({
    planetId: 1,
  });


}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { planetsDeletePlanet } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/planetsDeletePlanet.js";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await planetsDeletePlanet(scalarGalaxyTypescript, {
    planetId: 1,
  });
  if (res.ok) {
    const { value: result } = res;
    
  } else {
    console.log("planetsDeletePlanet failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.DeletePlanetRequest](../../models/operations/deleteplanetrequest.md)                                                                                               | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<void\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |

## uploadImage

Got a crazy good photo of a planet? Share it with the world!

### Example Usage

```typescript
import { ScalarGalaxyTypescript } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript";
import { openAsBlob } from "node:fs";

const scalarGalaxyTypescript = new ScalarGalaxyTypescript();

async function run() {
  const result = await scalarGalaxyTypescript.planets.uploadImage({
    planetId: 1,
    requestBody: {
      image: await openAsBlob("example.file"),
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ScalarGalaxyTypescriptCore } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/core.js";
import { planetsUploadImage } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/funcs/planetsUploadImage.js";
import { openAsBlob } from "node:fs";

// Use `ScalarGalaxyTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const scalarGalaxyTypescript = new ScalarGalaxyTypescriptCore();

async function run() {
  const res = await planetsUploadImage(scalarGalaxyTypescript, {
    planetId: 1,
    requestBody: {
      image: await openAsBlob("example.file"),
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("planetsUploadImage failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.UploadImageRequest](../../models/operations/uploadimagerequest.md)                                                                                                 | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.UploadImageResponse](../../models/operations/uploadimageresponse.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.APIError | 4XX, 5XX        | \*/\*           |