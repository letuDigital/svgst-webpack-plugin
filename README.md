# WEBPACK PLUGIN

```
███████╗██╗   ██╗ ██████╗     ███████╗████████╗ ██████╗ ██████╗ ███████╗
██╔════╝██║   ██║██╔════╝     ██╔════╝╚══██╔══╝██╔═══██╗██╔══██╗██╔════╝
███████╗██║   ██║██║  ███╗    ███████╗   ██║   ██║   ██║██████╔╝█████╗  
╚════██║╚██╗ ██╔╝██║   ██║    ╚════██║   ██║   ██║   ██║██╔══██╗██╔══╝  
███████║ ╚████╔╝ ╚██████╔╝    ███████║   ██║   ╚██████╔╝██║  ██║███████╗
╚══════╝  ╚═══╝   ╚═════╝     ╚══════╝   ╚═╝    ╚═════╝ ╚═╝  ╚═╝╚══════╝                                                                     
```

[![NPM](https://nodei.co/npm/svgst-webpack-plugin.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/svgst-webpack-plugin/)

## Package info
[![Build Status](https://travis-ci.org/pafnuty/svgst-webpack-plugin.svg?branch=master)](https://travis-ci.org/pafnuty/svgst-webpack-plugin)
[![NPM version](https://badge.fury.io/js/svgst-webpack-plugin.svg)](https://badge.fury.io/js/svgst-webpack-plugin)
[![Code Climate](https://codeclimate.com/github/pafnuty/svgst-webpack-plugin/badges/gpa.svg)](https://codeclimate.com/github/pafnuty/svgst-webpack-plugin)
[![Test Coverage](https://codeclimate.com/github/pafnuty/svgst-webpack-plugin/badges/coverage.svg)](https://codeclimate.com/github/pafnuty/svgst-webpack-plugin/coverage)

## Installation
```bash
npm i svgst-webpack-plugin --save-dev
```

## Webpack configuration

[EXAMPLE here](https://github.com/pafnuty/svgst-webpack-plugin/tree/master/platform)

## Usage
#### 1) require plugin
```javascript
//webpack.config.js
var SvgStore = require('svgst-webpack-plugin');
module.exports = {
  plugins: [
    // create svgStore instance object
    new SvgStore({
      // svgo options
      svgoOptions: {
        plugins: [
          { removeTitle: true }
        ]
      },
      prefix: 'icon'
    })
  ]
}
```

#### 2) Put function mark at your chunk
```javascript
// plugin will find marks and build sprite

var __svg__           = { path: './assets/svg/**/*.svg', name: 'assets/svg/[hash].logos.svg' };
// will overwrite to var __svg__ = { filename: "assets/svg/1466687804854.logos.svg" };

// also you can use next variables for sprite compile
// var __sprite__     = { path: './assets/svg/minify/*.svg', name: 'assets/svg/[hash].icons.svg' };
// var __svgstore__   = { path: './assets/svg/minify/*.svg', name: 'assets/svg/[hash].stuff.svg' };
// var __svgsprite__  = { path: './assets/svg/minify/*.svg', name: 'assets/svg/[hash].1logos.svg' };

// require basic or custom sprite loader
require('svgst-webpack-plugin/src/helpers/svgxhr')(__svg__);
```

##### Dear friends...
As you know, last version has integrated ajax sprite loader.
Right now, you can override that.
Or create your own sprite ajax loader function.

#### 3) HTML code for happy using
HTML:
```html
  <svg class="svg-icon">
    <use xlink:href="#icon-name"></use>
  </svg>
```
React JSX:
```html
  <svg className='svg-icon'>
    <use xlinkHref='#icon-name' />
  </svg>
```
## Plugin settings

#### options
- `template` - add custom jade template layout (optional)
- `svgoOptions` - options for [svgo](https://github.com/svg/svgo) (optional, default: `{}`)


## License

NPM package available here: [svgst-webpack-plugin](https://www.npmjs.com/package/svgst-webpack-plugin)

MIT © [Chernobrov Mike](http://mrsum.ru), [Gordey Levchenko](https://github.com/lgordey) , [Nadav Sinai](https://github.com/nadavsinai)
