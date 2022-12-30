# storybook-yarn

> The original issue (ERR_UNSUPPORTED_ESM_URL_SCHEME) is fixed on storybook.
> Now there's another error with yarn v4 (v3 works fine)

Test yarn v4 (berry) with storybook v7

Running yarn storybook we get an error:

```
ERR! Error: Path contains invalid characters: D:\repositories\storybook-yarn\node_modules\.cache\sb-manager\.yarn\__virtual__\@storybook-addon-links-virtual-7a0d1ebbb1\4\C:\Users\camar\AppData\Local\Yarn\Berry\cache\@storybook-addon-links-npm-7.0.0-beta.17-cc8db3676f-9.zip\node_modules\@storybook\addon-links\dist
ERR!     at checkPath (C:\Users\camar\AppData\Local\Yarn\Berry\cache\fs-extra-npm-9.1.0-983c2ddb4c-9.zip\node_modules\fs-extra\lib\mkdirs\make-dir.js:20:21)
ERR!     at module.exports.makeDir (C:\Users\camar\AppData\Local\Yarn\Berry\cache\fs-extra-npm-9.1.0-983c2ddb4c-9.zip\node_modules\fs-extra\lib\mkdirs\make-dir.js:45:3)
ERR!     at Object.defineProperty.value (C:\Users\camar\AppData\Local\Yarn\Berry\cache\universalify-npm-2.0.0-03b8b418a8-9.zip\node_modules\universalify\index.js:22:13)
ERR!     at C:\Users\camar\AppData\Local\Yarn\Berry\cache\fs-extra-npm-9.1.0-983c2ddb4c-9.zip\node_modules\fs-extra\lib\ensure\file.js:23:24
ERR!     at callback (C:\Users\camar\AppData\Local\Yarn\Berry\cache\graceful-fs-npm-4.2.10-79c70989ca-9.zip\node_modules\graceful-fs\polyfills.js:306:20)
ERR!     at D:\repositories\storybook-yarn\.pnp.cjs:14076:13
ERR!  Error: Path contains invalid characters: D:\repositories\storybook-yarn\node_modules\.cache\sb-manager\.yarn\__virtual__\@storybook-addon-links-virtual-7a0d1ebbb1\4\C:\Users\camar\AppData\Local\Yarn\Berry\cache\@storybook-addon-links-npm-7.0.0-beta.17-cc8db3676f-9.zip\node_modules\@storybook\addon-links\dist
ERR!     at checkPath (C:\Users\camar\AppData\Local\Yarn\Berry\cache\fs-extra-npm-9.1.0-983c2ddb4c-9.zip\node_modules\fs-extra\lib\mkdirs\make-dir.js:20:21)
ERR!     at module.exports.makeDir (C:\Users\camar\AppData\Local\Yarn\Berry\cache\fs-extra-npm-9.1.0-983c2ddb4c-9.zip\node_modules\fs-extra\lib\mkdirs\make-dir.js:45:3)
ERR!     at Object.defineProperty.value (C:\Users\camar\AppData\Local\Yarn\Berry\cache\universalify-npm-2.0.0-03b8b418a8-9.zip\node_modules\universalify\index.js:22:13)
ERR!     at C:\Users\camar\AppData\Local\Yarn\Berry\cache\fs-extra-npm-9.1.0-983c2ddb4c-9.zip\node_modules\fs-extra\lib\ensure\file.js:23:24
ERR!     at callback (C:\Users\camar\AppData\Local\Yarn\Berry\cache\graceful-fs-npm-4.2.10-79c70989ca-9.zip\node_modules\graceful-fs\polyfills.js:306:20)
ERR!     at D:\repositories\storybook-yarn\.pnp.cjs:14076:13 {
ERR!   code: 'EINVAL'
ERR! }
```

## Original issue

Test yarn v3 (berry) with storybook v7

Steps:

- yarn set version stable
- yarn init
- yarn add --dev vite
- npx sb@next init --builder=vite

Choose web-components type. After installing an error will occur:

```
Error: Cannot find module '@storybook/web-components/package.json'
Require stack:
- C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\cli\dist\generate.js
- C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\cli\bin\index.js
    at Function.Module._resolveFilename (node:internal/modules/cjs/loader:985:15)
    at Function.resolve (node:internal/modules/cjs/helpers:109:19)
    at getRendererDir (C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\cli\dist\generate.js:1:6584)
    at componentsPath (C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\cli\dist\generate.js:11:1438)
    at copyComponents (C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\cli\dist\generate.js:11:2612)
    at async baseGenerator (C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\cli\dist\generate.js:44:668)
    at async doInitiate (C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\cli\dist\generate.js:344:208)
    at async withTelemetry (C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\core-server\dist\index.js:33:5533)
    at async initiate (C:\Users\camar\AppData\Local\npm-cache\_npx\eebb2d3a7d26a7f1\node_modules\@storybook\cli\dist\generate.js:350:133)
```

- yarn storybook

A second error occurs:

```
 Error: Your application tried to access @storybook/builder-vite, but it isn't declared in your dependencies; this makes the require call ambiguous and unsound.
ERR!
ERR! Required package: @storybook/builder-vite (via "@storybook\builder-vite")
ERR! Required by: D:\repositories\storybook-yarn\.storybook\
ERR!
ERR! Require stack:
ERR! - D:\repositories\storybook-yarn\.yarn\cache\@storybook-core-server-npm-7.0.0-beta.15-b304f2875e-321ca5d8ec.zip\node_modules\@storybook\core-server\dist\index.js
ERR! - D:\repositories\storybook-yarn\.yarn\cache\@storybook-cli-npm-7.0.0-beta.15-41cccd4a33-5e39dffce8.zip\node_modules\@storybook\cli\dist\generate.js
ERR! - D:\repositories\storybook-yarn\.yarn\cache\@storybook-cli-npm-7.0.0-beta.15-41cccd4a33-5e39dffce8.zip\node_modules\@storybook\cli\bin\index.js
```

- yarn add --dev @storybook/builder-vite
- yarn storybook

A diferent error (using node 16.18.1):

```
ERR! Error [ERR_UNSUPPORTED_ESM_URL_SCHEME]: Only URLs with a scheme in: file, data are supported by the default ESM loader. On Windows, absolute paths must be valid file:// URLs. Received protocol 'd:'
ERR!     at __node_internal_captureLargerStackTrace (node:internal/errors:478:5)
ERR!     at new NodeError (node:internal/errors:387:5)
ERR!     at throwIfUnsupportedURLScheme (node:internal/modules/esm/resolve:1017:11)
ERR!     at defaultResolve (node:internal/modules/esm/resolve:1097:3)
ERR!     at nextResolve (node:internal/modules/esm/loader:163:28)
ERR!     at resolve$1 (file:///D:/repositories/storybook-yarn/.pnp.loader.mjs:1966:14)
ERR!     at nextResolve (node:internal/modules/esm/loader:163:28)
ERR!     at ESMLoader.resolve (node:internal/modules/esm/loader:837:30)
ERR!     at ESMLoader.getModuleJob (node:internal/modules/esm/loader:424:18)
ERR!     at ESMLoader.import (node:internal/modules/esm/loader:521:22)
ERR!     at importModuleDynamically (node:internal/modules/cjs/loader:1094:29)
ERR!     at importModuleDynamicallyWrapper (node:internal/vm/module:438:21)
ERR!     at importModuleDynamically (node:vm:389:46)
ERR!     at importModuleDynamicallyCallback (node:internal/process/esm_loader:35:14)
ERR!     at getPreviewBuilder (D:\repositories\storybook-yarn\.yarn\cache\@storybook-core-server-npm-7.0.0-beta.15-b304f2875e-321ca5d8ec.zip\node_modules\@storybook\core-server\dist\index.js:10:1913)
ERR!     at buildDevStandalone (D:\repositories\storybook-yarn\.yarn\cache\@storybook-core-server-npm-7.0.0-beta.15-b304f2875e-321ca5d8ec.zip\node_modules\@storybook\core-server\dist\index.js:33:2139)
ERR!     at processTicksAndRejections (node:internal/process/task_queues:96:5)
ERR!     at async withTelemetry (D:\repositories\storybook-yarn\.yarn\cache\@storybook-core-server-npm-7.0.0-beta.15-b304f2875e-321ca5d8ec.zip\node_modules\@storybook\core-server\dist\index.js:33:5533)
ERR!     at async dev (D:\repositories\storybook-yarn\.yarn\cache\@storybook-cli-npm-7.0.0-beta.15-41cccd4a33-5e39dffce8.zip\node_modules\@storybook\cli\dist\generate.js:441:440)
ERR!  Error [ERR_UNSUPPORTED_ESM_URL_SCHEME]: Only URLs with a scheme in: file, data are supported by the default ESM loader. On Windows, absolute paths must be valid file:// URLs. Received protocol 'd:'
ERR!     at __node_internal_captureLargerStackTrace (node:internal/errors:478:5)
ERR!     at new NodeError (node:internal/errors:387:5)
ERR!     at throwIfUnsupportedURLScheme (node:internal/modules/esm/resolve:1017:11)
ERR!     at nextResolve (node:internal/modules/esm/loader:163:28)
ERR!     at resolve$1 (file:///D:/repositories/storybook-yarn/.pnp.loader.mjs:1966:14)
ERR!     at nextResolve (node:internal/modules/esm/loader:163:28)
ERR!     at ESMLoader.resolve (node:internal/modules/esm/loader:837:30)
ERR!     at ESMLoader.getModuleJob (node:internal/modules/esm/loader:424:18)
ERR!     at ESMLoader.import (node:internal/modules/esm/loader:521:22)
ERR!     at importModuleDynamically (node:internal/modules/cjs/loader:1094:29)
ERR!     at importModuleDynamicallyWrapper (node:internal/vm/module:438:21)
ERR!     at importModuleDynamically (node:vm:389:46)
ERR!     at importModuleDynamicallyCallback (node:internal/process/esm_loader:35:14)
ERR!     at getPreviewBuilder (D:\repositories\storybook-yarn\.yarn\cache\@storybook-core-server-npm-7.0.0-beta.15-b304f2875e-321ca5d8ec.zip\node_modules\@storybook\core-server\dist\index.js:10:1913)
ERR!     at buildDevStandalone (D:\repositories\storybook-yarn\.yarn\cache\@storybook-core-server-npm-7.0.0-beta.15-b304f2875e-321ca5d8ec.zip\node_modules\@storybook\core-server\dist\index.js:33:2139)
ERR!     at async withTelemetry (D:\repositories\storybook-yarn\.yarn\cache\@storybook-core-server-npm-7.0.0-beta.15-b304f2875e-321ca5d8ec.zip\node_modules\@storybook\core-server\dist\index.js:33:5533)
ERR!     at async dev (D:\repositories\storybook-yarn\.yarn\cache\@storybook-cli-npm-7.0.0-beta.15-41cccd4a33-5e39dffce8.zip\node_modules\@storybook\cli\dist\generate.js:441:440) {
ERR!   code: 'ERR_UNSUPPORTED_ESM_URL_SCHEME'
ERR! }
```

- changed project type to "module". Error is the same
- upgraded node to v18.12.1: same error
- added some logs to .pnp.loader.mjs and found is trying to load builder-vite module: "D:\repositories\storybook-yarn\.yarn\_\_virtual\_\_\@storybook-builder-vite-virtual-5ce56f8e2a\0\cache\@storybook-builder-vite-npm-0.2.6-65efe11c86-9241575a9d.zip\node_modules\@storybook\builder-vite\dist\index.js"

See missing file:/// prefix.

For example see a path that works: "file:///D:/repositories/storybook-yarn/.yarn/unplugged/esbuild-npm-0.16.10-1db55565e0/node_modules/esbuild/lib/main.js"
