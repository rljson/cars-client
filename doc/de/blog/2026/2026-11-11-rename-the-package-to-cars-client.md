<!--
@license
Copyright (c) rljson

Use of this source code is governed by terms that can be
found in the LICENSE file in the root of this package.
-->

# Das Package heißt jetzt cars-client

## Motivation

- Das Package ist mehr als die Oberfläche einer Seite: es ist der
  Rljson-Client der Cars-Beispiel-App, der die Daten zeigt und im Browser
  in IndexedDB synchronisiert
- Seine alten Namen, das Repo `cars-ui` und das Package
  `@rljson/cars-ui-runtime`, sagten weder das eine noch das andere, und
  die Trennung in Core- und Runtime-Packages, aus der sie stammen, gibt es
  nicht mehr

## Strategie

- Repo, Package, Dateien, Exporte und Container bekommen einen Namen:
  `cars-client`
- Alles Aktuelle wird umbenannt; die Historie bleibt, wie sie geschrieben
  wurde
- Kein Verhalten ändert sich, so beweisen die Tests allein die Umbenennung

## Umsetzung

- Das Repo `rljson/cars-ui` heißt auf GitHub jetzt `rljson/cars-client`;
  GitHub leitet die alte URL weiter
- `package.json` nennt `@rljson/cars-client`, mit Homepage, Issues und
  Repository-URL des neuen Repos
- vite leitet das Bundle aus dem Package-Namen ab, also schreibt der Build
  `dist/cars-client.js`; `public/index.html` und das Dockerfile laden und
  kopieren diese Datei
- `src/cars-ui-runtime.ts` ist jetzt `src/cars-client.ts`, die
  Versionsdatei `src/cars_client_version.ts` exportiert
  `carsClientVersion`; Tests und Golden folgen
- Der Container heißt `cars-client`; README, README.de und `index.jsonc`
  sagen es

## Ergebnis

- Alle Tests laufen mit 100 % Abdeckung, und der Build schreibt
  `dist/cars-client.js`

## Offene Punkte

- Der Rljson-Sync in IndexedDB ist noch nicht gebaut; die Seite zeigt
  weiter die Hello-Zeilen
