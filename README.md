<!--
@license
Copyright (c) rljson

Use of this source code is governed by terms that can be
found in the LICENSE file in the root of this package.
-->

# @rljson/cars-ui-runtime

English | [Deutsch](README.de.md)

[![CI](https://github.com/rljson/cars-ui-runtime/actions/workflows/quick_check.yaml/badge.svg)](https://github.com/rljson/cars-ui-runtime/actions/workflows/quick_check.yaml)
[![npm](https://img.shields.io/npm/v/@rljson/cars-ui-runtime.svg)](https://www.npmjs.com/package/@rljson/cars-ui-runtime)

Browser app of the cars example app.

## Motivation

- The cars app needs a page in the browser, served from its own small container
- The page asks only `/api` on its own host; nginx forwards it to the backend for frontend
- For now it shows the hello world

## Installation

```bash
pnpm add @rljson/cars-ui-runtime
```

## Usage

```ts
import { helloLines } from '@rljson/cars-ui-runtime';

const lines = await helloLines((url) => fetch(url));
console.log(lines.join('\n'));
```

It prints:

```text
Hello from cars-ui-runtime
Hello from cars-bff-runtime
```

## Container

Build the container `cars-ui` in the registry:

```bash
az acr build --registry crcarsdemo --image cars-ui:<version>-<sha> .
```

## Limitations

- Shows only the hello world
- nginx forwards `/api` to `BFF_URL`, by default `cars-server` in the namespace `demo`

## Documentation

- The guides in [doc/guides](doc/guides)

## Status

Before 1.0 — the API may change between minor versions.

## Contributing

See [doc/guides/develop-guide.md](doc/guides/develop-guide.md).

## License

MIT — see [LICENSE](LICENSE).
