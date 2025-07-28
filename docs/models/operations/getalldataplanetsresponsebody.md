# GetAllDataPlanetsResponseBody

A paginated resource

## Example Usage

```typescript
import { GetAllDataPlanetsResponseBody } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/models/operations";

let value: GetAllDataPlanetsResponseBody = {
  data: [
    {
      id: 1,
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
        id: 1,
        name: "Marc",
      },
      tags: [
        "solar-system",
        "rocky",
        "explored",
      ],
      lastUpdated: new Date("2024-01-15T14:30:00Z"),
      callbackUrl: "https://example.com/webhook",
    },
  ],
  meta: {
    limit: 10,
    offset: 0,
    total: 100,
    next: "/planets?limit=10&offset=10",
  },
};
```

## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `data`                                                                 | [components.Planet](../../models/components/planet.md)[]               | :heavy_minus_sign:                                                     | N/A                                                                    |
| `meta`                                                                 | [operations.GetAllDataMeta](../../models/operations/getalldatameta.md) | :heavy_minus_sign:                                                     | N/A                                                                    |