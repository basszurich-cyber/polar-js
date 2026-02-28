# DiscountType

## Example Usage

```typescript
import { DiscountType } from "@spaire/sdk/models/components/discounttype.js";

let value: DiscountType = "fixed";
```

## Values

This is an open enum. Unrecognized values will be captured as the `Unrecognized<string>` branded type.

```typescript
"fixed" | "percentage" | Unrecognized<string>
```