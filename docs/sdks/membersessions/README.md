# MemberSessions

## Overview

### Available Operations

* [create](#create) - Create Member Session

## create

Create a member session.

This endpoint is only available for organizations with `member_model_enabled`
and `seat_based_pricing_enabled` feature flags enabled.

**Scopes**: `member_sessions:write`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="member-sessions:create" method="post" path="/v1/member-sessions/" -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const result = await spaire.memberSessions.create({
    memberId: "<value>",
    returnUrl: "https://example.com/account",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { SpaireCore } from "@spaire/sdk/core.js";
import { memberSessionsCreate } from "@spaire/sdk/funcs/memberSessionsCreate.js";

// Use `SpaireCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const spaire = new SpaireCore({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const res = await memberSessionsCreate(spaire, {
    memberId: "<value>",
    returnUrl: "https://example.com/account",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("memberSessionsCreate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [components.MemberSessionCreate](../../models/components/membersessioncreate.md)                                                                                               | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.MemberSession](../../models/components/membersession.md)\>**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.HTTPValidationError | 422                        | application/json           |
| errors.SDKError            | 4XX, 5XX                   | \*/\*                      |