# Timeframe

## Example Usage

```typescript
import { Timeframe } from "@spaire/sdk/models/components/benefitlicensekeyexpirationproperties.js";

let value: Timeframe = "year";
```

## Values

This is an open enum. Unrecognized values will be captured as the `Unrecognized<string>` branded type.

```typescript
"year" | "month" | "day" | Unrecognized<string>
```