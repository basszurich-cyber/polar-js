# MemberRole

## Example Usage

```typescript
import { MemberRole } from "@spaire/sdk/models/components/memberrole.js";

let value: MemberRole = "owner";
```

## Values

This is an open enum. Unrecognized values will be captured as the `Unrecognized<string>` branded type.

```typescript
"owner" | "billing_manager" | "member" | Unrecognized<string>
```