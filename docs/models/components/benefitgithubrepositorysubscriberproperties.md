# BenefitGitHubRepositorySubscriberProperties

Properties available to subscribers for a benefit of type `github_repository`.

## Example Usage

```typescript
import { BenefitGitHubRepositorySubscriberProperties } from "@spaire/sdk/models/components/benefitgithubrepositorysubscriberproperties.js";

let value: BenefitGitHubRepositorySubscriberProperties = {
  repositoryOwner: "spairesource",
  repositoryName: "private_repo",
};
```

## Fields

| Field                        | Type                         | Required                     | Description                  | Example                      |
| ---------------------------- | ---------------------------- | ---------------------------- | ---------------------------- | ---------------------------- |
| `repositoryOwner`            | *string*                     | :heavy_check_mark:           | The owner of the repository. | spairesource                  |
| `repositoryName`             | *string*                     | :heavy_check_mark:           | The name of the repository.  | private_repo                 |