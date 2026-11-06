<!--
@license
Copyright (c) rljson

Use of this source code is governed by terms that can be
found in the LICENSE file in the root of this package.
-->

# @rljson/cars-ui-runtime

[English](README.md) | Deutsch

[![CI](https://github.com/rljson/cars-ui-runtime/actions/workflows/quick_check.yaml/badge.svg)](https://github.com/rljson/cars-ui-runtime/actions/workflows/quick_check.yaml)

Browser-App der cars-Beispiel-App.

## Motivation

- Die cars-App braucht eine Seite im Browser, ausgeliefert von einem eigenen kleinen Container
- Die Seite fragt nur `/api` auf ihrem eigenen Host; nginx leitet das an das Backend for Frontend weiter
- Vorerst zeigt sie das Hello World

## Installation

Das Paket ist privat und wird nicht auf npm veröffentlicht. Abhängig
macht man sich von einer getaggten Version seines Git-Repos:

```bash
pnpm add git+ssh://git@github.com/rljson/cars-ui-runtime.git#semver:^0.0.1
```

## Verwendung

```ts
import { helloLines } from '@rljson/cars-ui-runtime';

const lines = await helloLines((url) => fetch(url));
console.log(lines.join('\n'));
```

Gibt aus:

```text
Hello from cars-ui-runtime
Hello from cars-bff-runtime
```

## Container

Den Container `cars-ui` in der Registry bauen:

```bash
az acr build --registry crcarsdemo --image cars-ui:<version>-<sha> .
```

## Grenzen

- Zeigt nur das Hello World
- nginx leitet `/api` an `BFF_URL` weiter, standardmäßig `cars-server` im Namespace `demo`

## Dokumentation

- Die Leitfäden in [doc/guides](doc/guides)

## Stand

Vor 1.0 — die API kann sich zwischen Minor-Versionen ändern.

## Mitwirken

Siehe [doc/guides/develop-guide.md](doc/guides/develop-guide.md).

## Lizenz

MIT — siehe [LICENSE](LICENSE).
