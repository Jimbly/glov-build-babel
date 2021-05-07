Babel task processor for [glov-build](https://github.com/Jimbly/glov-build)
=============================

Installation requires also installing @babel/core and related modules.
```sh
npm install --save-dev glov-build-babel @babel/core @babel/preset-env
```

API usage:
```javascript
const babel = require('glov-build-babel');

gb.task({
  name: ...,
  input: ...,
  ...babel(options),
});
```
Options
* **`babel`** - optional options object to pass to `babel`
* **`sourcemap`** - optional options object to pass to `glov-build-sourcemap`

Example usage:
```javascript
const babel = require('glov-build-babel');

gb.task({
  name: 'client_js_babel_files',
  input: ['client/**/*.js','common/**/*.js'],
  target: 'dev',
  ...babel({
    sourcemap: {
      inline: true,
    },
    babel: {
      babelrc: false,
      presets: [['@babel/env', {
        targets: {
          ie: '10'
        },
        loose: true,
      }]],
      plugins: [
        ['some-babel-plugin', {}],
      ]
    }
  })
});

```
