# CustomerPortal.Subscriptions

## Overview

### Available Operations

* [list](#list) - List Subscriptions
* [get](#get) - Get Subscription
* [cancel](#cancel) - Cancel Subscription
* [update](#update) - Update Subscription

## list

List subscriptions of the authenticated customer.

**Scopes**: `customer_portal:read` `customer_portal:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:subscriptions:list" method="get" path="/v1/customer-portal/subscriptions/" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.subscriptions.list({
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {});

  for await (const page of result) {
    console.log(page);
  }
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { customerPortalSubscriptionsList } from "@spaire/sdk/funcs/customerPortalSubscriptionsList.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalSubscriptionsList(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {});
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("customerPortalSubscriptionsList failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CustomerPortalSubscriptionsListRequest](../../models/operations/customerportalsubscriptionslistrequest.md)                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CustomerPortalSubscriptionsListSecurity](../../models/operations/customerportalsubscriptionslistsecurity.md)                                                       | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.CustomerPortalSubscriptionsListResponse](../../models/operations/customerportalsubscriptionslistresponse.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |

## get

Get a subscription for the authenticated customer.

**Scopes**: `customer_portal:read` `customer_portal:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:subscriptions:get" method="get" path="/v1/customer-portal/subscriptions/{id}" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.subscriptions.get({
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {
    id: "<value>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { customerPortalSubscriptionsGet } from "@spaire/sdk/funcs/customerPortalSubscriptionsGet.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalSubscriptionsGet(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {
    id: "<value>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customerPortalSubscriptionsGet failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CustomerPortalSubscriptionsGetRequest](../../models/operations/customerportalsubscriptionsgetrequest.md)                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CustomerPortalSubscriptionsGetSecurity](../../models/operations/customerportalsubscriptionsgetsecurity.md)                                                         | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CustomerSubscription](../../models/components/customersubscription.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ResourceNotFound    | 404                        | application/json           |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |

## cancel

Cancel a subscription of the authenticated customer.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:subscriptions:cancel" method="delete" path="/v1/customer-portal/subscriptions/{id}" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.subscriptions.cancel({
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {
    id: "<value>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { customerPortalSubscriptionsCancel } from "@spaire/sdk/funcs/customerPortalSubscriptionsCancel.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalSubscriptionsCancel(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {
    id: "<value>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customerPortalSubscriptionsCancel failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CustomerPortalSubscriptionsCancelRequest](../../models/operations/customerportalsubscriptionscancelrequest.md)                                                     | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CustomerPortalSubscriptionsCancelSecurity](../../models/operations/customerportalsubscriptionscancelsecurity.md)                                                   | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CustomerSubscription](../../models/components/customersubscription.md)\>**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| errors.AlreadyCanceledSubscription | 403                                | application/json                   |
| errors.ResourceNotFound            | 404                                | application/json                   |
| errors.HTTPValidationError         | 422                                | application/json                   |
| errors.SDKError                    | 4XX, 5XX                           | \*/\*                              |

## update

Update a subscription of the authenticated customer.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:subscriptions:update" method="patch" path="/v1/customer-portal/subscriptions/{id}" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.subscriptions.update({
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {
    id: "<value>",
    customerSubscriptionUpdate: {},
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { customerPortalSubscriptionsUpdate } from "@spaire/sdk/funcs/customerPortalSubscriptionsUpdate.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalSubscriptionsUpdate(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {
    id: "<value>",
    customerSubscriptionUpdate: {},
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customerPortalSubscriptionsUpdate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CustomerPortalSubscriptionsUpdateRequest](../../models/operations/customerportalsubscriptionsupdaterequest.md)                                                     | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CustomerPortalSubscriptionsUpdateSecurity](../../models/operations/customerportalsubscriptionsupdatesecurity.md)                                                   | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CustomerSubscription](../../models/components/customersubscription.md)\>**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| errors.AlreadyCanceledSubscription | 403                                | application/json                   |
| errors.ResourceNotFound            | 404                                | application/json                   |
| errors.HTTPValidationError         | 422                                | application/json                   |
| errors.SDKError                    | 4XX, 5XX                           | \*/\*                              |