# CustomerPortal.CustomerSession

## Overview

### Available Operations

* [introspect](#introspect) - Introspect Customer Session
* [getAuthenticatedUser](#getauthenticateduser) - Get Authenticated Portal User

## introspect

Introspect the current session and return its information.

**Scopes**: `customer_portal:read` `customer_portal:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:customer-session:introspect" method="get" path="/v1/customer-portal/customer-session/introspect" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.customerSession.introspect({
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { customerPortalCustomerSessionIntrospect } from "@spaire/sdk/funcs/customerPortalCustomerSessionIntrospect.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalCustomerSessionIntrospect(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customerPortalCustomerSessionIntrospect failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                                                                                     | [operations.CustomerPortalCustomerSessionIntrospectSecurity](../../models/operations/customerportalcustomersessionintrospectsecurity.md)                                       | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CustomerCustomerSession](../../models/components/customercustomersession.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.SDKError | 4XX, 5XX        | \*/\*           |

## getAuthenticatedUser

Get information about the currently authenticated portal user.

**Scopes**: `customer_portal:read` `customer_portal:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="customer_portal:customer-session:get_authenticated_user" method="get" path="/v1/customer-portal/customer-session/user" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire();

async function run() {
  const result = await spaire.customerPortal.customerSession.getAuthenticatedUser({
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { customerPortalCustomerSessionGetAuthenticatedUser } from "@spaire/sdk/funcs/customerPortalCustomerSessionGetAuthenticatedUser.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore();

async function run() {
  const res = await customerPortalCustomerSessionGetAuthenticatedUser(spaire, {
    customerSession: process.env["SPAIRE_CUSTOMER_SESSION"] ?? "",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customerPortalCustomerSessionGetAuthenticatedUser failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                                                                                     | [operations.CustomerPortalCustomerSessionGetAuthenticatedUserSecurity](../../models/operations/customerportalcustomersessiongetauthenticatedusersecurity.md)                   | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.PortalAuthenticatedUser](../../models/components/portalauthenticateduser.md)\>**

### Errors

| Error Type      | Status Code     | Content Type    |
| --------------- | --------------- | --------------- |
| errors.SDKError | 4XX, 5XX        | \*/\*           |