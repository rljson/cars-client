<!--
@license
Copyright (c) rljson

Use of this source code is governed by terms that can be
found in the LICENSE file in the root of this package.
-->

# Rename the package to cars-client

## Motivation

- The package is more than the user interface of one page: it is the
  Rljson client of the cars example app, which shows the data and syncs
  it into IndexedDB in the browser
- Its old names, the repo `cars-ui` and the package
  `@rljson/cars-ui-runtime`, named neither, and the split into core and
  runtime packages they stem from no longer exists

## Strategy

- Give repo, package, files, exports and container one name:
  `cars-client`
- Rename everything current; leave the history as it was written
- Change no behaviour, so the tests prove the rename alone

## Implementation

- The repo `rljson/cars-ui` is now `rljson/cars-client` on GitHub, which
  redirects the old URL
- `package.json` names `@rljson/cars-client`, with homepage, issues and
  repository URL of the new repo
- vite derives the bundle from the package name, so the build writes
  `dist/cars-client.js`; `public/index.html` and the Dockerfile load and
  copy that file
- `src/cars-ui-runtime.ts` is `src/cars-client.ts`, the version file
  `src/cars_client_version.ts` exports `carsClientVersion`; the tests
  and the golden follow
- The container is `cars-client`; README, README.de and `index.jsonc`
  say so

## Result

- All tests pass with 100 % coverage, and the build writes
  `dist/cars-client.js`

## Open Points

- The Rljson sync into IndexedDB is not built yet; the page still shows
  the hello lines
