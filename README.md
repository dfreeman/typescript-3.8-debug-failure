This repo demonstrates an issue that appeared in `tsc`, specifically in watched builds,
and specifically with `allowJs: true`.

As of `typescript@3.8.0-dev.20191224`, running `yarn start` (or `npm start`) with
this project works as expected. In the next published release, `3.8.0-dev.20191228`,
it fails with an error like:

```
[3:50:17 PM] Starting compilation in watch mode...

/Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:80189
                throw e;
                ^

Error: Debug Failure.
    at Object.assertDefined (/Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:1709:24)
    at /Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:31795:34
    at Object.filter (/Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:297:31)
    at serializeAsClass (/Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:31793:48)
    at serializeSymbolWorker (/Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:31589:29)
    at serializeSymbol (/Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:31546:38)
    at /Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:31527:25
    at Map.forEach (<anonymous>)
    at visitSymbolTable (/Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:31526:33)
    at symbolTableToDeclarationStatements (/Users/dfreeman/Desktop/tsc-boom/node_modules/typescript/lib/tsc.js:31418:17)
```

The issue seems to have something to do with the type definitions for `@ember/component`
when used in a `.js` file with `allowJs: true`, but that's as far as I got.
