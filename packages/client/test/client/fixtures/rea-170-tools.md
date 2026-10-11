# REA public tool catalog

`rea-170-tools.json` contains the complete `tools` array from a public REA
`Client.listTools()` response at commit
[`21650455a9c90a26e725c3505a3c17054cc4516c`](https://github.com/morluto/rea/tree/21650455a9c90a26e725c3505a3c17054cc4516c).
The snapshot contains tool definitions only: 170 tools with 170 output schemas,
including shared schema IDs and nested `$defs`/`$ref` structures.

It is compact UTF-8 JSON without a trailing newline, 1,954,693 bytes, SHA-256
`badac148871025e4ac3f4b71c8914c25b4d32d973d07a28f60ed799764906f2b`.

The `rea` scenario in `cold-output-server.mjs` replays this catalog over stdio.
It returns `{ result: null }` for `close_binary`, with an intentionally invalid
`{ result: 0 }` on the second call. The test uses the normal Ajv provider and
checks validator preparation and compilation counts. It does not run REA or
require a target binary or analysis provider.

From the SDK repository root:

```sh
pnpm --filter @modelcontextprotocol/client exec vitest run test/client/lazyOutputValidator.transports.test.ts -t 'public REA catalog'
```

The catalog is copied from REA under its MIT license:

MIT License

Copyright (c) 2026 morluto

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
