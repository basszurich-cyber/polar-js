<!-- Start SDK Example Usage [usage] -->
```typescript
import { Spaire } from "@spaire/sdk";

const spaire = new Spaire({
  accessToken: process.env["SPAIRE_ACCESS_TOKEN"] ?? "",
});

async function run() {
  const result = await spaire.organizations.list({});

  for await (const page of result) {
    console.log(page);
  }
}

run();

```
<!-- End SDK Example Usage [usage] -->