# OrderStatus

## Example Usage

```typescript
import { OrderStatus } from "@spaire/sdk/models/components/orderstatus.js";

let value: OrderStatus = "void";
```

## Values

This is an open enum. Unrecognized values will be captured as the `Unrecognized<string>` branded type.

```typescript
"pending" | "paid" | "refunded" | "partially_refunded" | "void" | Unrecognized<string>
```