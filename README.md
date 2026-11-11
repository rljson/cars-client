<!--
@license
Copyright (c) rljson

Use of this source code is governed by terms that can be
found in the LICENSE file in the root of this package.
-->

# @rljson/cars-client

English | [Deutsch](README.de.md)

[![CI](https://github.com/rljson/cars-client/actions/workflows/quick_check.yaml/badge.svg)](https://github.com/rljson/cars-client/actions/workflows/quick_check.yaml)

Browser app of the cars example app.

## Motivation

- The cars app needs a page in the browser, served from its own small container
- The page asks only `/api` on its own host; nginx forwards it to the backend for frontend
- For now it shows the hello world

## Installation

The package is private and not published to npm. Depend on a tagged
version of its git repository:

```bash
pnpm add git+ssh://git@github.com/rljson/cars-client.git#semver:^0.0.1
```

## Usage

```ts
import { helloLines } from '@rljson/cars-client';

const lines = await helloLines((url) => fetch(url));
console.log(lines.join('\n'));
```

It prints:

```text
Hello from cars-client
Hello from cars-bff-runtime
```

## Container

Build the container `cars-client` in the registry:

```bash
az acr build --registry crcarsdemo --image cars-client:<version>-<sha> .
```

## Limitations

- Shows only the hello world
- nginx forwards `/api` to `BFF_URL`, by default `cars-bff` in the namespace `demo`

## Documentation

- The guides in [doc/guides](doc/guides)

## Status

Before 1.0 — the API may change between minor versions.

## Contributing

See [doc/guides/develop-guide.md](doc/guides/develop-guide.md).

## License

MIT — see [LICENSE](LICENSE).
