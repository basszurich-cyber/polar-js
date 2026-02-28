# CustomerPortal.CustomerMeters

## Overview

### Available Operations

* [list](#list) - List Meters
* [get](#get) - Get Customer Meter

## list

List meters of the authenticated customer.

**Scopes**: `customer_portal:read` `customer_portal:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:customer_meters:list" method="get" path="/v1/customer-portal/meters/" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.customerMeters.list({
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
import { customerPortalCustomerMetersList } from "@spaire/sdk/funcs/customerPortalCustomerMetersList.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalCustomerMetersList(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {});
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("customerPortalCustomerMetersList failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CustomerPortalCustomerMetersListRequest](../../models/operations/customerportalcustomermeterslistrequest.md)                                                       | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CustomerPortalCustomerMetersListSecurity](../../models/operations/customerportalcustomermeterslistsecurity.md)                                                     | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.CustomerPortalCustomerMetersListResponse](../../models/operations/customerportalcustomermeterslistresponse.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |

## get

Get a meter by ID for the authenticated customer.

**Scopes**: `customer_portal:read` `customer_portal:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:customer_meters:get" method="get" path="/v1/customer-portal/meters/{id}" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.customerMeters.get({
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
import { customerPortalCustomerMetersGet } from "@spaire/sdk/funcs/customerPortalCustomerMetersGet.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalCustomerMetersGet(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {
    id: "<value>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customerPortalCustomerMetersGet failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CustomerPortalCustomerMetersGetRequest](../../models/operations/customerportalcustomermetersgetrequest.md)                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CustomerPortalCustomerMetersGetSecurity](../../models/operations/customerportalcustomermetersgetsecurity.md)                                                       | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CustomerCustomerMeter](../../models/components/customercustomermeter.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ResourceNotFound    | 404                        | application/json           |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |