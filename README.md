## storybook-addon-designs

A [Storybook](https://github.com/storybooks/storybook) addon that embed Figma or websites in the addon panel for better design-development workflow.

- Demo (WIP)

## Requirements

- Storybook@>=5.0.0

This addon should work well with any framework: If you find the case the addon not works, please open an issue.

## Getting started

1. Install

```sh
npm install --save-dev storybook-addon-designs
# yarn add -D storybook-addon-designs
```

2. Register the addon in `addons.js`

```js
// .storybook/addons.js

import 'storybook-addon-designs/register'
```

3. Add it to story!

```js
import { withDesigns } from 'storybook-addon-designs'

storiesOf('My stories', module)
  .addDecorator(withDesigns)
  .add('My awesome story', () => <Button>Hello, World!</Button>, {
    design: {
      type: 'figma',
      url: 'https://www.figma.com/file/LKQ4FJ4bTnCSjedbRpk931/Sample-File'
    }
  })
```

## Usage

Add `withDesigns` decorator then put `design` parameter to your story.

> NOTE: If you omit `design` parameter, the addon does nothing.

The type of `design` parameter is differ by embed type.
If you have basic knowledge of TypeScript, [type definition file](./packages/storybook-addon-designs/src/config.ts) will help you a lot.

### `iframe` type

Just show the specified website in `<iframe>` element.

```js
{
  type: 'iframe',

  // An URL to show in iframe
  url: 'https://foo.bar',

  // Optional. Whether to allow embed sites to enter fullscreen mode.
  // default: false
  allowFullscreen: true
}
```

### `figma` type

Embedding [Figma Live Embed Kit](https://www.figma.com/developers/embed).
Copy the URL from the browser search bar then paste it to `url` field.

```js
{
  type: 'figma',

  // An URL for the file/node/prototype
  // Just copy&paste browsers URL bar!
  url: 'https://www.figma.com/file/LKQ4FJ4bTnCSjedbRpk931'

  // (From Figma's doc)
  // ... something that identifies your site.
  embedHost: 'storybook'

  // In addition to these options, this type inherit options from `iframe` type
}
```

## Related projects

- [storybook-addon-figma](https://github.com/hharnisc/storybook-addon-figma)
