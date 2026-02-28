# CustomerPortal.Downloadables

## Overview

### Available Operations

* [list](#list) - List Downloadables

## list

**Scopes**: `customer_portal:read` `customer_portal:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:downloadables:list" method="get" path="/v1/customer-portal/downloadables/" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.downloadables.list({
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
import { customerPortalDownloadablesList } from "@spaire/sdk/funcs/customerPortalDownloadablesList.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalDownloadablesList(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  }, {});
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("customerPortalDownloadablesList failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CustomerPortalDownloadablesListRequest](../../models/operations/customerportaldownloadableslistrequest.md)                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CustomerPortalDownloadablesListSecurity](../../models/operations/customerportaldownloadableslistsecurity.md)                                                       | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.CustomerPortalDownloadablesListResponse](../../models/operations/customerportaldownloadableslistresponse.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |