---
"@shopify/shopify-api": patch
---

Fix adapter initialization issues with modern bundlers (Vite, Webpack) in SSR frameworks

Adds `sideEffects` configuration to package.json to prevent bundlers from incorrectly tree-shaking adapter initialization code. This resolves the "Missing adapter implementation for 'abstractRuntimeString'" error that occurred when using the library with Nuxt 3, TanStack Start, Next.js, and other SSR frameworks.

The adapters (node, web-api, cf-worker) use side effects to initialize runtime functions, and modern bundlers were optimizing these away, causing runtime errors. The fix ensures these critical initialization side effects are preserved during the bundling process.