# PlanetInput

A planet in the Scalar Galaxy

## Example Usage

```typescript
import { PlanetInput } from "@shariqnzr-gmail-com-team/scalar-galaxy-typescript/models/components";

let value: PlanetInput = {
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
};
```

## Fields

| Field                                                                                         | Type                                                                                          | Required                                                                                      | Description                                                                                   | Example                                                                                       |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `name`                                                                                        | *string*                                                                                      | :heavy_check_mark:                                                                            | N/A                                                                                           | Mars                                                                                          |
| `description`                                                                                 | *string*                                                                                      | :heavy_minus_sign:                                                                            | N/A                                                                                           | The red planet                                                                                |
| `type`                                                                                        | [components.Type](../../models/components/type.md)                                            | :heavy_minus_sign:                                                                            | N/A                                                                                           | terrestrial                                                                                   |
| `habitabilityIndex`                                                                           | *number*                                                                                      | :heavy_minus_sign:                                                                            | A score from 0 to 1 indicating potential habitability                                         | 0.68                                                                                          |
| `physicalProperties`                                                                          | [components.PhysicalProperties](../../models/components/physicalproperties.md)                | :heavy_minus_sign:                                                                            | N/A                                                                                           |                                                                                               |
| `atmosphere`                                                                                  | [components.Atmosphere](../../models/components/atmosphere.md)[]                              | :heavy_minus_sign:                                                                            | Atmospheric composition                                                                       |                                                                                               |
| `discoveredAt`                                                                                | [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | :heavy_minus_sign:                                                                            | N/A                                                                                           | 1610-01-07T00:00:00Z                                                                          |
| `image`                                                                                       | *string*                                                                                      | :heavy_minus_sign:                                                                            | N/A                                                                                           | https://cdn.scalar.com/photos/mars.jpg                                                        |
| `satellites`                                                                                  | [components.Satellite](../../models/components/satellite.md)[]                                | :heavy_minus_sign:                                                                            | N/A                                                                                           |                                                                                               |
| `creator`                                                                                     | [components.UserInput](../../models/components/userinput.md)                                  | :heavy_minus_sign:                                                                            | A user                                                                                        |                                                                                               |
| `tags`                                                                                        | *string*[]                                                                                    | :heavy_minus_sign:                                                                            | N/A                                                                                           | [<br/>"solar-system",<br/>"rocky",<br/>"explored"<br/>]                                       |
| `callbackUrl`                                                                                 | *string*                                                                                      | :heavy_minus_sign:                                                                            | URL to receive notifications about this planet                                                | https://example.com/webhook                                                                   |