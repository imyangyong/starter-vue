---
title: Eslint
---

## Install

```bash
pnpm i -D eslint @antfu/eslint-config
```

## Usage

1. create `eslint.config.mjs` in project root

```js
import antfu from '@antfu/eslint-config'

export default antfu()
```

2. add lint script to `package.json`

```json
{
  "scripts": {
    "lint": "eslint ."
  }
}
```

Check out the [Antfu eslint config](https://github.com/antfu/eslint-config) for more details.
