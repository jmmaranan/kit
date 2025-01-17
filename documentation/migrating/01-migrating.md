---
title: Migrating
---

# Migrating from Sapper

SvelteKit is largely backwards-compatible with Sapper. However, there are a number of differences. You may find it helpful to view the [examples](https://github.com/sveltejs/kit/tree/master/examples) while migrating.

- Remove `rollup.config.js` or `webpack.config.js` and replace with [`vite.config.js`](https://github.com/sveltejs/kit/blob/master/packages/create-svelte/template/vite.config.js)
- Add a [`svelte.config.cjs` ](https://github.com/sveltejs/kit/blob/master/packages/create-svelte/template/svelte.config.cjs) with the adapter of your choice
- Update your `template.html` to [`app.html`](https://github.com/sveltejs/kit/blob/master/packages/create-svelte/template/src/app.html)
  - It should have a `<div id="svelte">` (or `id` matching `target` in `svelte.config.cjs`)
- The error and layout pages should prefixed by `$` instead of `_`
- Replace imports from `@sapper/app` with imports from `$app/navigation` and `$app/stores` and update APIs accordingly
- If you have source code in `src/node_modules`, move it to `src/lib` and update the import path to `$lib`
- Move any custom `client.js` code to `$layout.svelte` and put it in an `if (browser)` check (`import { browser } from "$app/env";`).
- `preload` has been renamed to `load`. It has a new method signature and return values
- `sapper:prefetch` and `sapper:noscroll` have been renamed to `sveltekit:prefetch` and `sveltekit:noscroll`

## Migrating integrations

- Please see [sveltejs/integrations](https://github.com/sveltejs/integrations#sveltekit) for examples of setting up popular tools like PostCSS, Tailwind CSS, mdsvex, Firebase, GraphQL, and Bulma.
