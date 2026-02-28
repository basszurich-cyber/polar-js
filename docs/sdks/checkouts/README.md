# Checkouts

## Overview

### Available Operations

* [list](#list) - List Checkout Sessions
* [create](#create) - Create Checkout Session
* [get](#get) - Get Checkout Session
* [update](#update) - Update Checkout Session
* [clientGet](#clientget) - Get Checkout Session from Client
* [clientUpdate](#clientupdate) - Update Checkout Session from Client
* [clientConfirm](#clientconfirm) - Confirm Checkout Session from Client

## list

List checkout sessions.

**Scopes**: `checkouts:read` `checkouts:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="checkouts:list" method="get" path="/v1/checkouts/" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const result = await spaire.checkouts.list({
    organizationId: "1dbfc517-0bbf-4301-9ba8-555ca42b9737",
  });

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
import { checkoutsList } from "@spaire/sdk/funcs/checkoutsList.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const res = await checkoutsList(spaire, {
    organizationId: "1dbfc517-0bbf-4301-9ba8-555ca42b9737",
  });
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("checkoutsList failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CheckoutsListRequest](../../models/operations/checkoutslistrequest.md)                                                                                             | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.CheckoutsListResponse](../../models/operations/checkoutslistresponse.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |

## create

Create a checkout session.

**Scopes**: `checkouts:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="checkouts:create" method="post" path="/v1/checkouts/" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const result = await spaire.checkouts.create({
    customerName: "John Doe",
    customerBillingAddress: {
      country: "US",
    },
    locale: "en",
    products: [
      "<value 1>",
      "<value 2>",
      "<value 3>",
    ],
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { checkoutsCreate } from "@spaire/sdk/funcs/checkoutsCreate.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const res = await checkoutsCreate(spaire, {
    customerName: "John Doe",
    customerBillingAddress: {
      country: "US",
    },
    locale: "en",
    products: [
      "<value 1>",
      "<value 2>",
      "<value 3>",
    ],
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("checkoutsCreate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [components.CheckoutCreate](../../models/components/checkoutcreate.md)                                                                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Checkout](../../models/components/checkout.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |

## get

Get a checkout session by ID.

**Scopes**: `checkouts:read` `checkouts:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="checkouts:get" method="get" path="/v1/checkouts/{id}" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const result = await spaire.checkouts.get({
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
import { checkoutsGet } from "@spaire/sdk/funcs/checkoutsGet.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const res = await checkoutsGet(spaire, {
    id: "<value>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("checkoutsGet failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CheckoutsGetRequest](../../models/operations/checkoutsgetrequest.md)                                                                                               | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Checkout](../../models/components/checkout.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ResourceNotFound    | 404                        | application/json           |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |

## update

Update a checkout session.

**Scopes**: `checkouts:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="checkouts:update" method="patch" path="/v1/checkouts/{id}" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const result = await spaire.checkouts.update({
    id: "<value>",
    checkoutUpdate: {
      customerName: "John Doe",
      customerBillingAddress: {
        country: "US",
      },
      locale: "en",
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { checkoutsUpdate } from "@spaire/sdk/funcs/checkoutsUpdate.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const res = await checkoutsUpdate(spaire, {
    id: "<value>",
    checkoutUpdate: {
      customerName: "John Doe",
      customerBillingAddress: {
        country: "US",
      },
      locale: "en",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("checkoutsUpdate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CheckoutsUpdateRequest](../../models/operations/checkoutsupdaterequest.md)                                                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Checkout](../../models/components/checkout.md)\>**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.AlreadyActiveSubscriptionError | 403                                   | application/json                      |
| errors.NotOpenCheckout                | 403                                   | application/json                      |
| errors.PaymentNotReady                | 403                                   | application/json                      |
| errors.TrialAlreadyRedeemed           | 403                                   | application/json                      |
| errors.ResourceNotFound               | 404                                   | application/json                      |
| errors.HTTPValidationError            | 422                                   | application/json                      |
| errors.SDKError                       | 4XX, 5XX                              | \*/\*                                 |

## clientGet

Get a checkout session by client secret.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="checkouts:client_get" method="get" path="/v1/checkouts/client/{client_secret}" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.checkouts.clientGet({
    clientSecret: "<value>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { checkoutsClientGet } from "@spaire/sdk/funcs/checkoutsClientGet.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await checkoutsClientGet(spaire, {
    clientSecret: "<value>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("checkoutsClientGet failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CheckoutsClientGetRequest](../../models/operations/checkoutsclientgetrequest.md)                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CheckoutPublic](../../models/components/checkoutpublic.md)\>**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.ResourceNotFound     | 404                         | application/json            |
| errors.ExpiredCheckoutError | 410                         | application/json            |
| errors.HTTPValidationError  | 422                         | application/json            |
| errors.SDKError             | 4XX, 5XX                    | \*/\*                       |

## clientUpdate

Update a checkout session by client secret.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="checkouts:client_update" method="patch" path="/v1/checkouts/client/{client_secret}" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.checkouts.clientUpdate({
    clientSecret: "<value>",
    checkoutUpdatePublic: {
      customerName: "John Doe",
      customerBillingAddress: {
        country: "US",
      },
      locale: "en",
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { checkoutsClientUpdate } from "@spaire/sdk/funcs/checkoutsClientUpdate.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await checkoutsClientUpdate(spaire, {
    clientSecret: "<value>",
    checkoutUpdatePublic: {
      customerName: "John Doe",
      customerBillingAddress: {
        country: "US",
      },
      locale: "en",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("checkoutsClientUpdate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CheckoutsClientUpdateRequest](../../models/operations/checkoutsclientupdaterequest.md)                                                                             | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CheckoutPublic](../../models/components/checkoutpublic.md)\>**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.AlreadyActiveSubscriptionError | 403                                   | application/json                      |
| errors.NotOpenCheckout                | 403                                   | application/json                      |
| errors.PaymentNotReady                | 403                                   | application/json                      |
| errors.TrialAlreadyRedeemed           | 403                                   | application/json                      |
| errors.ResourceNotFound               | 404                                   | application/json                      |
| errors.ExpiredCheckoutError           | 410                                   | application/json                      |
| errors.HTTPValidationError            | 422                                   | application/json                      |
| errors.SDKError                       | 4XX, 5XX                              | \*/\*                                 |

## clientConfirm

Confirm a checkout session by client secret.

Orders and subscriptions will be processed.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="checkouts:client_confirm" method="post" path="/v1/checkouts/client/{client_secret}/confirm" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const result = await spaire.checkouts.clientConfirm({
    clientSecret: "<value>",
    checkoutConfirmStripe: {
      customerName: "John Doe",
      customerBillingAddress: {
        country: "US",
      },
      locale: "en",
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { checkoutsClientConfirm } from "@spaire/sdk/funcs/checkoutsClientConfirm.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const res = await checkoutsClientConfirm(spaire, {
    clientSecret: "<value>",
    checkoutConfirmStripe: {
      customerName: "John Doe",
      customerBillingAddress: {
        country: "US",
      },
      locale: "en",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("checkoutsClientConfirm failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CheckoutsClientConfirmRequest](../../models/operations/checkoutsclientconfirmrequest.md)                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CheckoutPublicConfirmed](../../models/components/checkoutpublicconfirmed.md)\>**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.PaymentError                   | 400                                   | application/json                      |
| errors.AlreadyActiveSubscriptionError | 403                                   | application/json                      |
| errors.NotOpenCheckout                | 403                                   | application/json                      |
| errors.PaymentNotReady                | 403                                   | application/json                      |
| errors.TrialAlreadyRedeemed           | 403                                   | application/json                      |
| errors.ResourceNotFound               | 404                                   | application/json                      |
| errors.ExpiredCheckoutError           | 410                                   | application/json                      |
| errors.HTTPValidationError            | 422                                   | application/json                      |
| errors.SDKError                       | 4XX, 5XX                              | \*/\*                                 |