# Color.js 🎨

Extract colors from an image using JavaScript. Images that are already present in the DOM are supported, as well as (external) URL's.

## Install

Manually:

```html
<script src="dist/color.js"></script>
```

## Usage:

```js
const color = new Color('js-logo.jpg', {
  amount: 1
});

color.mostUsed((result) => {
  console.log(result); // rgb(241, 221, 63)
});
```

## Options

You can pass two arguments, an image and a configuration `object`.

### Image (required)

Can be a DOM element or a URL.

```js
const img = document.getElementById('image');
const color = new Color(img);
```

```js
const color = new Color('image.jpg');
```

```js
const color = new Color('https://example.com/image.jpg');
```

When using an external image, CORS should of course be enabled on the source.

### Configuration (optional)

The default configuration options. Explanations of each option can be found below.

```js
{
  amount: 3,
  format: 'rgb',
  sample: 10,
  blocks: 20,
}
```

#### Amount

The amount of colors that should be returned. When set to `1` a singular value is returned, otherwise an `array` of values.

#### Format

The format in which colors should be returned. Options are `'rgb'` (default), `'hex'` and `'array'`.

```js
'rgb(241, 221, 63)' // 'rgb'
'#f1dd3f' // 'hex'
[241, 221, 63] // 'array'
```

#### Sample

Configures how many pixels of an image should be processed. For example, a value of `20` means every 20th pixel is interpreted. A higher value means less accurate results, but better performance. An example of default sampling (`10`) on a 593x393 image:

![Sample](img/sample.jpg)

#### Blocks

Configures how many 'neighboring' colors should be combined into one color. A value of `1` would mean _every_ individual color would be considered, but this is often not ideal. Especially in photographs there's usually a lot of color data, and grouping colors would give more usable results in most cases. In the first example below, `blocks` is set to `5` and a lot of individual colors in the sea show are returned. When some more is applied (`30` in the second example), the results become more distinct.

![Blocks](img/blocks.jpg)

## API

### Average

### Most used

### Least used
