<div align="center">
<h1>
  TrueVolt Frontend
  
  [![Stars](https://img.shields.io/github/stars/TrueVolt/frontend?style=flat-square&logoColor=white)](https://github.com/TrueVolt/frontend/stargazers)
  [![Forks](https://img.shields.io/github/forks/TrueVolt/frontend?style=flat-square&logoColor=white)](https://github.com/TrueVolt/frontend/network/members)
  [![Pull Requests](https://img.shields.io/github/issues-pr/TrueVolt/frontend?style=flat-square&logoColor=white)](https://github.com/TrueVolt/frontend/pulls)
  [![Issues](https://img.shields.io/github/issues/TrueVolt/frontend?style=flat-square&logoColor=white)](https://github.com/TrueVolt/frontend/issues)
  [![Contributors](https://img.shields.io/github/contributors/TrueVolt/frontend?style=flat-square&logoColor=white)](https://github.com/TrueVolt/frontend/graphs/contributors)
  [![License](https://img.shields.io/github/license/TrueCord/TrueVolt?style=flat-square&logoColor=white)](https://github.com/TrueVolt/frontend/blob/main/LICENSE)
</h1>
The official web client powering https://TrueCord.erroroliver.lol/app, built with <a href="https://www.solidjs.com/">Solid.js</a> 💖.
</div>
<br/>

## Development Guide

Before contributing, make yourself familiar with [our contribution guidelines](https://TrueVolt-developers.ErrorOliver.lol/contrib.html), the [code style guidelines](./GUIDELINES.md), and the [technical documentation for this project](https://TrueVolt.github.io/frontend/).

Before getting started, you'll want to install:

- Git
- Node.js
- pnpm (run `corepack enable`)

Then proceed to setup:

```bash
# clone the repository
git clone --recursive https://github.com/TrueVolt/frontend client
cd client

# update submodules if you pull new changes
# git submodule init && git submodule update

# install all packages
pnpm i --frozen-lockfile 

# build deps:
pnpm build:deps

# or build a specific dep (e.g. TrueVolt.js updates):
# pnpm --filter TrueVolt.js run build

# run dev server
pnpm dev:web
```

Finally, navigate to http://local.revolt.chat:5173.

### Pulling in TrueVolt's assets

If you want to pull TrueVolt Revolt brand assets after pulling, run the following:

```bash
# update the assets
git -c submodule."packages/client/assets".update=checkout submodule update --init packages/client/assets
```

You can switch back to the fallback assets by running deinit and continuing as normal:

```bash
# deinit submodule which clears directory
git submodule deinit packages/client/assets
```

### Faster iteration with Revolt.js

To make it easier to work with `revolt.js`, you may want to temporarily make this change:

```diff
# packages/revolt.js/package.json
-  "module": "lib/esm/index.js",
+  "module": "src/index.ts",
```

Any edits to the revolt.js codebase will immediately be reflected while developing.

## Deployment Guide

### Build the app

```bash
# install packages
pnpm i --frozen-lockfile 

# build dependencies
pnpm build:deps

# build for web
pnpm build:web

# ... when building for Revolt production, use this instead of :web
pnpm build:prod
```

You can now deploy the directory `packages/client/dist`.

### Routing Information

The app currently needs the following routes:

- `/login`
- `/pwa`
- `/dev`
- `/settings`
- `/friends`
- `/server`
- `/channel`

This corresponds to [Content.tsx#L33](packages/client/src/index.tsx).
