---
{"dg-publish":true,"permalink":"/conventional-scripts/","tags":["javascript","web-development"]}
---

There are many conventions used for package JSON scripts which makes it harder to get started in unfamiliar repos. This page suggests a canonical set of scripts to be used for the benefit of humans and coding agents alike.
# Example

```json
"dev": "next dev",
"typecheck": "tsc --noEmit",
"lint": "eslint",
"unit": "bun test",
"component": "cypress run --component",
"integration": "start-server-and-test cypress run",
"test": "typecheck && lint && unit && integration",
"build": "next build",
"start": "next start"
```

# Scripts
## dev
Starts dev server.
## typecheck
Static type checking
## lint
Static code quality checking 
## unit
These tests should run very quickly to provide the tightest feedback loop possible every time you save. They should therefore stub all I/O.

Suggested tools: Bun test ideally. Avoid Jest if you can, cold start time is far too long.
## component
Component tests are just unit tests for UI components. However in contrast to unit tests of vanilla JS/TS modules they are usually developed with the aid of over tools to provide visual information whether this be a fake DOM or an actual browser. Either way the methodology and performance characteristics are different and so these unit tests should be run separately.

Suggested tools: Cypress, Storybook.
## integration
These tests aim to be more live-like and do not need to stub I/O. They should intentionally trade-off speed to provide confidence the right thing is being shipped.

Suggested tools: Cypress, Playwright.
## test
Runs whatever other scripts it needs to check the package is production ready. If this exits 0 then you can push.
## build
Produces a *deployable* optimised for production. Often involves minification, transpilation, and bundling.
## start
Runs the production build.
# FAQ
# # What no `e2e` script?
The meaning of end-to-end is ambiguous and `e2e` looks ugly. Unit vs integration is the only helpful distinction IMO.
## Why not have scripts like `test:unit` and `start:dev`?
They take too long to type and look ugly.
## What about other scripts?
There will undoubtedly be other scripts specific to your package, these should go in a top-level `scripts` folder.

You could add everything to the package JSON scripts but that's maintenance burden. It also creates an unclear division of responsibilities.

So reserve package JSON just for these canonical scripts.