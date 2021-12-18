---
id: sites
sidebar_label: sites
title: "npx remotion lambda sites"
slug: /lambda/cli/sites
---

The `npx remotion lambda sites` command allows to create, view and delete Remotion projects in your S3 bucket.

- [`create`](#create)
- [`ls`](#ls)
- [`rm`](#rm)

## create

```
npx remotion lambda sites create src/index.tsx
```

Bundle and upload a Remotion video to an S3 bucket.

<details>
<summary>
Example output
</summary>
<pre>
(1/3) [====================] Bundled video 3975ms<br/>
(2/3) [====================] Created bucket 457ms<br/>
(3/3) [====================] Uploaded to S3 25118ms<br/>
<br/>
Deployed to S3!<br/>
https://remotionlambda-12345.s3.eu-central-1.amazonaws.com/sites/abcdef/index.html<br/>

</pre>
</details>

### `--site-name`

Uploads the project to a specific directory and returns a deterministic URL. If a site already existed under this name, it will be overwritten.

```
npx remotion lambda sites create src/index.tsx --site-name=my-project
```

<details>
<summary>
Example output
</summary>
<pre>
(1/3) [====================] Bundled video 3975ms<br/>
(2/3) [====================] Created bucket 457ms<br/>
(3/3) [====================] Uploaded to S3 25118ms<br/>
<br/>
Deployed to S3!<br/>
https://remotionlambda-12345.s3.eu-central-1.amazonaws.com/sites/my-project/index.html<br/>

</pre>
</details>

## ls

```
npx remotion lambda sites ls
```

Get a list of sites. The URL that is printed can be passed to the `render` command to render a video.

<details>
<summary>
Example output
</summary>
<pre>
Site ID             Bucket                        Size      Last updated<br/>
pr6fwglz05          remotionlambda-abcdefg        14.7 MB   2021-12-02<br/>     
https://remotionlambda-abcdefg.s3.eu-central-1.amazonaws.com/sites/pr6fwglz05/index.html<br/><br/>   
testbed             remotionlambda-abcdefg        14.7 MB   2021-12-02  <br/>
https://remotionlambda-abcdefg.s3.eu-central-1.amazonaws.com/sites/testbed/index.html<br/>
</pre>
</details>

### `-q`

Returns only a list of space-separated sites.

```
npx remotion lambda sites ls -q
```

<details>
<summary>
Example output
</summary>
<pre>
pr6fwglz05 testbed<br/>
</pre>
</details>

## rm

Removes a site (or multiple) from S3 by it's ID.

```bash
npx remotion lambda sites rm abcdef
npx remotion lambda sites rm abcdef my-project # multiple at once
```

<details>
<summary>
Example output
</summary>
<pre>Site abcdef in bucket remotionlambda-gc1w0xbfzl (14.7 MB): Delete? (Y/n): Y
<br/>Deleted sites/abcdef/052787b08233d85edebfc4ce4610944e.mp4
<br/>Deleted sites/abcdef/258.bundle.js
<br/>Deleted sites/abcdef/15.bundle.js
<br/>Deleted sites/abcdef/249.bundle.js.map
<br/>Deleted sites/abcdef/263.bundle.js
<br/>Deleted sites/abcdef/143.bundle.js
<br/>Deleted sites/abcdef/258.bundle.js.map
<br/>Deleted sites/abcdef/15.bundle.js.map
<br/>Deleted sites/abcdef/185.bundle.js.map
<br/>Deleted sites/abcdef/249.bundle.js
<br/>Deleted sites/abcdef/143.bundle.js.map
<br/>Deleted sites/abcdef/185.bundle.js
<br/>Deleted sites/abcdef/1f2d09019ff34eed846a5151b8561d5b.mp4
<br/>Deleted sites/abcdef/263.bundle.js.map
<br/>Deleted sites/abcdef/268.bundle.js
<br/>Deleted sites/abcdef/378.bundle.js.map
<br/>Deleted sites/abcdef/268.bundle.js.map
<br/>Deleted sites/abcdef/378.bundle.js
<br/>Deleted sites/abcdef/2b91c5234e41d3c36d4bf6df37876958.webm
<br/>Deleted sites/abcdef/450.bundle.js
<br/>Deleted sites/abcdef/46.bundle.js.map
<br/>Deleted sites/abcdef/46.bundle.js
<br/>Deleted sites/abcdef/450.bundle.js.map
<br/>Deleted sites/abcdef/534.bundle.js.map
<br/>Deleted sites/abcdef/569.bundle.js
<br/>Deleted sites/abcdef/3577958454aa99ad707b596f65151746.webm
<br/>Deleted sites/abcdef/534.bundle.js
<br/>Deleted sites/abcdef/575.bundle.js.map
<br/>Deleted sites/abcdef/575.bundle.js
<br/>Deleted sites/abcdef/569.bundle.js.map
<br/>Deleted sites/abcdef/801.bundle.js
<br/>Deleted sites/abcdef/7badbf53d3130d91b90c46181a2ecdc4.webm
<br/>Deleted sites/abcdef/801.bundle.js.map
<br/>Deleted sites/abcdef/873.bundle.js
<br/>Deleted sites/abcdef/98.bundle.js.map
<br/>Deleted sites/abcdef/bff822b868a2b87b31877f3606c9cc13.mp3
<br/>Deleted sites/abcdef/873.bundle.js.map
<br/>Deleted sites/abcdef/98.bundle.js
<br/>Deleted sites/abcdef/a2f36e3a48b4989e0da1fea9959fb35f.mp3
<br/>Deleted sites/abcdef/bundle.js
<br/>Deleted sites/abcdef/bundle.js.map
<br/>Deleted sites/abcdef/a7d87d9934059032eebb9c1536378a2a.webm
<br/>Deleted sites/abcdef/index.html
<br/>Deleted site abcdef and freed up 14.7 MB.
<br/>
</pre>
</details>

### `-y`

Removes a site without asking for confirmation.

```
npx remotion lambda sites rm abcdef -y
```

<details>
<summary>
Example output
</summary>
<pre>Site abcdef in bucket remotionlambda-gc1w0xbfzl (14.7 MB): Delete? (Y/n): Y
<br/>Deleted sites/abcdef/052787b08233d85edebfc4ce4610944e.mp4
<br/>Deleted sites/abcdef/258.bundle.js
<br/>Deleted sites/abcdef/15.bundle.js
<br/>Deleted sites/abcdef/249.bundle.js.map
<br/>Deleted sites/abcdef/263.bundle.js
<br/>Deleted sites/abcdef/143.bundle.js
<br/>Deleted sites/abcdef/258.bundle.js.map
<br/>Deleted sites/abcdef/15.bundle.js.map
<br/>Deleted sites/abcdef/185.bundle.js.map
<br/>Deleted sites/abcdef/249.bundle.js
<br/>Deleted sites/abcdef/143.bundle.js.map
<br/>Deleted sites/abcdef/185.bundle.js
<br/>Deleted sites/abcdef/1f2d09019ff34eed846a5151b8561d5b.mp4
<br/>Deleted sites/abcdef/263.bundle.js.map
<br/>Deleted sites/abcdef/268.bundle.js
<br/>Deleted sites/abcdef/378.bundle.js.map
<br/>Deleted sites/abcdef/268.bundle.js.map
<br/>Deleted sites/abcdef/378.bundle.js
<br/>Deleted sites/abcdef/2b91c5234e41d3c36d4bf6df37876958.webm
<br/>Deleted sites/abcdef/450.bundle.js
<br/>Deleted sites/abcdef/46.bundle.js.map
<br/>Deleted sites/abcdef/46.bundle.js
<br/>Deleted sites/abcdef/450.bundle.js.map
<br/>Deleted sites/abcdef/534.bundle.js.map
<br/>Deleted sites/abcdef/569.bundle.js
<br/>Deleted sites/abcdef/3577958454aa99ad707b596f65151746.webm
<br/>Deleted sites/abcdef/534.bundle.js
<br/>Deleted sites/abcdef/575.bundle.js.map
<br/>Deleted sites/abcdef/575.bundle.js
<br/>Deleted sites/abcdef/569.bundle.js.map
<br/>Deleted sites/abcdef/801.bundle.js
<br/>Deleted sites/abcdef/7badbf53d3130d91b90c46181a2ecdc4.webm
<br/>Deleted sites/abcdef/801.bundle.js.map
<br/>Deleted sites/abcdef/873.bundle.js
<br/>Deleted sites/abcdef/98.bundle.js.map
<br/>Deleted sites/abcdef/bff822b868a2b87b31877f3606c9cc13.mp3
<br/>Deleted sites/abcdef/873.bundle.js.map
<br/>Deleted sites/abcdef/98.bundle.js
<br/>Deleted sites/abcdef/a2f36e3a48b4989e0da1fea9959fb35f.mp3
<br/>Deleted sites/abcdef/bundle.js
<br/>Deleted sites/abcdef/bundle.js.map
<br/>Deleted sites/abcdef/a7d87d9934059032eebb9c1536378a2a.webm
<br/>Deleted sites/abcdef/index.html
<br/>Deleted site abcdef and freed up 14.7 MB.
<br/>
</pre>
</details>

:::tip
With the `npx remotion lambda sites rm -f $(npx remotion lambda sites ls -q)` command, you can delete all your sites at once (on most UNIX shells like `zsh`).
:::