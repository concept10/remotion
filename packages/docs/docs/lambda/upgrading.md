---
id: upgrading
title: Upgrading
slug: /lambda/upgrading
---

import {Prerelease} from "../../components/PrereleaseVersion"

- Get the newest version from the [changelog](/docs/lambda/changelog) page.
- Upgrade all packages to the newest version (`@remotion/lambda`, but also `remotion`, `@remotion/cli` etc.)

<Prerelease onlySnippet/>

- (Optional): Remove the old versions of the function:

:::info
You only should do this if the function is not being used anymore. If you are still using it in production, you can just skip this step.
:::

```
npx remotion lambda functions rm $(npx remotion lambda functions ls -q) -y
```

- Deploy the newest version of the Remotion Lambda function:

```
npx remotion lambda functions deploy
```

- Update your API calls according to the [changelog](/docs/lambda/changelog). While Remotion Lambda is in Alpha, breaking changes may occur in every version. Once it hits stable, breaking changes will only occur in major version bumps.

## Separating production and testing environments

If you already shipped Remotion Lambda to production, you can upgrade without incurring any downtime. Each version of Remotion Lambda has a schema identifier (in the format of `2021-08-12`) that will increment whenever Remotion Lambda gets upgraded.

If you have Remotion in production and cloned locally, upgrading Remotion Lambda in your code locally and then rendering a video will yield an error message that the versions are mismatching. Simply deploy a new function `npx remotion lambda functions deploy` and your local environment will talk to the new function, while production will talk to the older function.

If everything works and you commit and deploy the change to production, it will start talking to the new version and you can safely remove the old function.