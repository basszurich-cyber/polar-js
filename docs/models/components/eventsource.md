# EventSource

## Example Usage

```typescript
import { EventSource } from "@spaire/sdk/models/components/eventsource.js";

let value: EventSource = "system";
```

## Values

This is an open enum. Unrecognized values will be captured as the `Unrecognized<string>` branded type.

```typescript
"system" | "user" | Unrecognized<string>
```