# GetPlanetResponse


## Supported Types

### `components.Planet`

```typescript
const value: components.Planet = {
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
};
```

### `Uint8Array`

```typescript
const value: Uint8Array = new TextEncoder().encode("0xdC7D3f4be0");
```

