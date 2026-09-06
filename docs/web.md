---
title: Print WebView
---

# Print WebView

Present the system print UI for the current WebView content. Only Android and iOS. Call this after [Installation](/docs/readme#installation). From a button, this is the fastest way to confirm the system print UI without an external file. Print a PDF or other file with [Print PDF and files](/docs/pdf).

```ts
import { Printer } from '@rdlabo/capacitor-printer';

await Printer.printWebView({ name: 'Document' });
```

`name` is the print job name and defaults to `'Document'`.

<!-- !::printWebView:: -->

<!-- !::PrintWebViewOptions:: -->
