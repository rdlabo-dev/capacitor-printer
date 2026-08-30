# @rdlabo/capacitor-printer

<!-- rdlabo-docs-omit -->
[![npm version](https://badge.fury.io/js/@rdlabo%2Fcapacitor-printer.svg)](https://badge.fury.io/js/@rdlabo%2Fcapacitor-printer)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
<!-- /rdlabo-docs-omit -->

Print files or the current web view from a Capacitor app.

This plugin wraps the native printing UI on iOS and Android. You can print a local file (for example, a PDF generated in your app) or the content of the current web view.

<!-- rdlabo-docs-omit -->
**Full documentation:** [https://docs.rdlabo.dev/projects/capacitor-printer](https://docs.rdlabo.dev/projects/capacitor-printer)
<!-- /rdlabo-docs-omit -->

**Documentation:** [Read the full documentation](https://docs.rdlabo.dev/projects/capacitor-printer)

## Install

```bash
npm install @rdlabo/capacitor-printer
npx cap sync
```

## Usage

See [PDF](https://docs.rdlabo.dev/projects/capacitor-printer/docs/pdf) to print a file and [Web](https://docs.rdlabo.dev/projects/capacitor-printer/docs/web) to print the current WebView.

<!-- rdlabo-docs-omit -->
### Print a file

```ts
import { Printer } from '@rdlabo/capacitor-printer';

const printPdf = async (filePath: string) => {
  try {
    await Printer.printFile({
      path: filePath,
      mimeType: 'application/pdf',
    });
  } finally {
    // The source file can be deleted once the promise settles.
  }
};
```

### Print the current web view

```ts
import { Printer } from '@rdlabo/capacitor-printer';

const printPage = async () => {
  await Printer.printWebView({ name: 'My Receipt' });
};
```

<!-- /rdlabo-docs-omit -->

## When to use

Use this plugin when your app needs to present the system print dialog, such as:

- Printing a receipt or invoice as PDF.
- Printing a report generated in the app.
- Printing the contents of the current page.

## Platform notes

- **iOS and Android**: `printFile` and `printWebView` are both supported.
- **Web**: Not supported because browsers already provide `window.print()`.

## API

<docgen-index>

* [`printFile(...)`](#printfile)
* [`printWebView(...)`](#printwebview)
* [Interfaces](#interfaces)
* [Type Aliases](#type-aliases)

</docgen-index>

<docgen-api>
<!--Update the source file JSDoc comments and rerun docgen to update the docs below-->

### printFile(...)

```typescript
printFile(options: PrintFileOptions) => Promise<void>
```

Present the printing user interface to print a file.

The promise settles after the operating system no longer needs the source
file, so the file can be safely deleted in a `finally` block.

Only available on Android and iOS.

| Param         | Type                                                          |
| ------------- | ------------------------------------------------------------- |
| **`options`** | <code><a href="#printfileoptions">PrintFileOptions</a></code> |

--------------------


### printWebView(...)

```typescript
printWebView(options?: PrintOptions | undefined) => Promise<void>
```

Present the printing user interface to print the web view content.

| Param         | Type                                                  |
| ------------- | ----------------------------------------------------- |
| **`options`** | <code><a href="#printoptions">PrintOptions</a></code> |

--------------------


### Interfaces


#### PrintFileOptions

| Prop           | Type                | Description                                                                                                                                 |
| -------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **`path`**     | <code>string</code> | The path to the file. Android supports file paths, `file://` URLs, and `content://` URLs. iOS supports file paths and local `file://` URLs. |
| **`mimeType`** | <code>string</code> | The MIME type of the file. Only used on Android.                                                                                            |


#### PrintOptions

| Prop       | Type                | Description                | Default                 |
| ---------- | ------------------- | -------------------------- | ----------------------- |
| **`name`** | <code>string</code> | The name of the print job. | <code>'Document'</code> |


### Type Aliases


#### PrintWebViewOptions

<code><a href="#printoptions">PrintOptions</a></code>

</docgen-api>

<!-- rdlabo-docs-omit -->
## Prerelease channels

An open, non-draft pull request can be published to the npm `beta` dist-tag after its `Validation` and `Package Candidate` workflows pass. A repository owner or maintainer must add a comment whose entire body is:

```text
/beta
```

The request authorizes only the pull request head SHA that existed when the comment was added. The workflow revalidates the owner or maintainer permission and head SHA immediately before publishing. Any new commit requires CI to pass again and a fresh owner or maintainer `/beta` comment. Fork pull requests are supported. Pull requests that change a release-gating workflow cannot be beta-published until those workflow changes land on `main`.

Beta versions use `<base>-beta.pr<PR number>.sha<12-character SHA>`. The candidate is built in a read-only workflow without npm publishing credentials. The privileged release workflow publishes only the validated immutable package artifact with lifecycle scripts disabled. A notification failure cannot invalidate a successful npm publish.

When a pull request is merged into `main`, it is automatically published to `beta` only after the required CI and `Package Candidate` succeed for that exact merge commit. Direct pushes to `main` do not publish a candidate.

Only `npm run release` creates a release tag. Stable `vX.Y.Z` tags publish to npm `latest`; revision/prerelease tags publish to `next`. Neither `beta` nor `next` publishing changes the npm `latest` dist-tag.

## Maintainers

- [rdlabo](https://rdlabo.dev/)
<!-- /rdlabo-docs-omit -->

<!-- rdlabo-docs-omit -->
## License

This project is licensed under the [MIT License](./LICENSE).
<!-- /rdlabo-docs-omit -->
