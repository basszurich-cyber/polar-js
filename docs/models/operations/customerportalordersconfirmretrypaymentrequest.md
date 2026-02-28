# CustomerPortalOrdersConfirmRetryPaymentRequest

## Example Usage

```typescript
import { CustomerPortalOrdersConfirmRetryPaymentRequest } from "@spaire/sdk/models/operations/customerportalordersconfirmretrypayment.js";

let value: CustomerPortalOrdersConfirmRetryPaymentRequest = {
  id: "<value>",
  customerOrderConfirmPayment: {},
};
```

## Fields

| Field                                                                                            | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `id`                                                                                             | *string*                                                                                         | :heavy_check_mark:                                                                               | The order ID.                                                                                    |
| `customerOrderConfirmPayment`                                                                    | [components.CustomerOrderConfirmPayment](../../models/components/customerorderconfirmpayment.md) | :heavy_check_mark:                                                                               | N/A                                                                                              |