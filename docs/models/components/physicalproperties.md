# PhysicalProperties

## Example Usage

```typescript
import { PhysicalProperties } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/models/components";

let value: PhysicalProperties = {
  mass: 0.107,
  radius: 0.532,
  gravity: 0.378,
  temperature: {
    min: 130,
    max: 308,
    average: 210,
  },
};
```

## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      | Example                                                          |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `mass`                                                           | *number*                                                         | :heavy_minus_sign:                                               | Mass in Earth masses                                             | 0.107                                                            |
| `radius`                                                         | *number*                                                         | :heavy_minus_sign:                                               | Radius in Earth radii                                            | 0.532                                                            |
| `gravity`                                                        | *number*                                                         | :heavy_minus_sign:                                               | Surface gravity in Earth g                                       | 0.378                                                            |
| `temperature`                                                    | [components.Temperature](../../models/components/temperature.md) | :heavy_minus_sign:                                               | N/A                                                              |                                                                  |