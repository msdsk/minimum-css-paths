# Reproduction

1. Install dependencies, run `npm run dev`. Notice the hypnotic pattern of the background, like the roof of an Opel Record 1992.

2. Now run `npm run build && npm run start` and notice that you can't be hypnotized anymore :<

## What is wrong

Nuxt revrites the css declaration from `background: url("/polka.svg")` to `background: url(/_nuxt/polka.svg)`, which is right for the dev process, but nuxt keeps it for the production build too, where static assets are served directly from the root.

## What is wrong #2

Trying to reproduce the issue I've found out that without using pages, css was loaded normally on dev but with production build it seemed to not be loaded whatsoever, regardless if I kept it as a separate file referenced from `nuxt.config.ts` or as a `<style>` tag inside `app.vue`.
