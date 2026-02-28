# CustomerPortalSubscriptionsUpdateRequest

## Example Usage

```typescript
import { CustomerPortalSubscriptionsUpdateRequest } from "@spaire/sdk/models/operations/customerportalsubscriptionsupdate.js";

let value: CustomerPortalSubscriptionsUpdateRequest = {
  id: "<value>",
  customerSubscriptionUpdate: {
    seats: 845687,
  },
};
```

## Fields

| Field                                   | Type                                    | Required                                | Description                             |
| --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| `id`                                    | *string*                                | :heavy_check_mark:                      | The subscription ID.                    |
| `customerSubscriptionUpdate`            | *components.CustomerSubscriptionUpdate* | :heavy_check_mark:                      | N/A                                     |