---
title: Print PDF and files
---

# Print PDF and files

Present the system print UI for a PDF or other file. Only Android and iOS. Call this after [Installation](/docs/readme#installation). Print the current WebView with [Print WebView](/docs/web).

Pass a path to a real local file your app already wrote (not a placeholder string). Android supports file paths, `file://` URLs, and `content://` URLs. iOS supports file paths and local `file://` URLs. `mimeType` is Android-only.

```ts
import { Printer } from '@rdlabo/capacitor-printer';

// filePath must point to a file that exists on the device.
await Printer.printFile({ path: filePath });
// After await settles, the OS no longer needs the source; delete it then if you no longer need it.
```

Signatures are on the [API](/docs/api#printfile) page.
