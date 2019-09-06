# script-loader

Promise based dynamic scripts loader for **browsers**. (`@vaju/script-loader`)

## Why

- Load script files on demand _(for better page load performance)_.
- Duplication check _(skip loading if the same script is already loaded)_.
- Typescript ready.
- Promise ready.
- No dependencies, tiny (1.2 KB).

## Install

```bash
npm i @vaju/script-loader
```

## Usage

```ts
import { scriptLoader } from '@vaju/script-loader';

// ...

await scriptLoader([
  { scr: 'https://cdn.firebase.com/libs/firebaseui/3.6.0/firebaseui.js' },

  // or optionally pass options
  {
    scr: 'https://cdn.firebase.com/libs/firebaseui/3.6.0/firebaseui.js',
    opt: {
      async: true, // default
      type: 'text/javascript', // default
      attrs: {}, // default
    },
  },
]);
```

Results in appending the following script node to DOM (inside the `<head>` or `<body>` tag).

```html
<script async type=​"text/​javascript" src=​"https://.../​firebaseui.js">​</script>​
```

## APIs

```ts
import { scriptLoader } from '@vaju/script-loader';

// ...

await scriptLoader(
  dynamicScripts,
  hostElement, // optional
  document, // optional
);
```

Where, **`dynamicScripts`** has the following form:

```ts
const dynamicScripts = [
  {
    src: 'script src url',
    // optional opt
    opt: {
      async: true, // (default) script will have async attribute
      type: 'text/javascript', // (default)
      attrs: {}, // optional map of attributes. Default is empty.
    },
  },
];
```

Optional **hostElement** is an `HTMLElement` to which the `<script>` tag is attached. Default is `<head> || <body>`

```ts
const hostElement = document.getElementsByTagName('head')[0];
```

Optional `document` object. Default is `document`.

## Licence

MIT &copy; 2019 [Vajahath Ahmed](https://twitter.com/vajahath7)
