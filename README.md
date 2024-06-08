# @hishprorg/dolores-exercitationem

![Last version](https://img.shields.io/github/tag/Kikobeats/@hishprorg/dolores-exercitationem.svg?style=flat-square)
[![Build Status](https://img.shields.io/travis/Kikobeats/@hishprorg/dolores-exercitationem/master.svg?style=flat-square)](https://travis-ci.org/Kikobeats/@hishprorg/dolores-exercitationem)
[![Coverage Status](https://img.shields.io/coveralls/Kikobeats/@hishprorg/dolores-exercitationem.svg?style=flat-square)](https://coveralls.io/github/Kikobeats/@hishprorg/dolores-exercitationem)
[![Dependency status](https://img.shields.io/david/Kikobeats/@hishprorg/dolores-exercitationem.svg?style=flat-square)](https://david-dm.org/Kikobeats/@hishprorg/dolores-exercitationem)
[![Dev Dependencies Status](https://img.shields.io/david/dev/Kikobeats/@hishprorg/dolores-exercitationem.svg?style=flat-square)](https://david-dm.org/Kikobeats/@hishprorg/dolores-exercitationem#info=devDependencies)
[![NPM Status](https://img.shields.io/npm/dm/@hishprorg/dolores-exercitationem.svg?style=flat-square)](https://www.npmjs.org/package/@hishprorg/dolores-exercitationem)

> Organizes and maintains your JSON files readable.

![](http://i.imgur.com/2qNLC48.png)

**Finepack** is a tool to keep your JSON files organized, especially if you are creating an open source project and want to be sure that your files have all the information that is required or recommended by the main package management systems (like bower or npm). This is what it can do:

-   Lints the JSON to be sure that it is in a valid format.
-   Validates the keys to make sure of the existence of required keys such as `name` or `version`, and other important keys such as `homepage`, `main`, `license`...
-   Organizes the JSON by moving the most important properties to the top.
-   Sorts the rest of the keys alphabetically and recursively using the JavaScript [sort](https://mzl.la/1jBtmgE) function (elements are sorted by converting them to strings and comparing strings in Unicode code point order).
-   Can be configured not to sort the arrays or objects at one or more user specified keys.
-   Can use a user-provided compare function to define the sort order.

You can use **Finepack** as a CLI tool or from NodeJS as a library. Based on [fixpack](https://github.com/henrikjoreteg/fixpack) but with a little more ♥.

## Install

```bash
npm install @hishprorg/dolores-exercitationem -g
```

## Usage

### CLI

```
$ @hishprorg/dolores-exercitationem

  Organizes and maintains your JSON files readable.

  Usage
    $ @hishprorg/dolores-exercitationem <fileJSON> [options]

    options:
     --no-validate             disable validation mode.
     --no-color                disable colors in the output.
     --sort-ignore-object-at   don't sort object(s) at these comma separated key(s).
     --sort-ignore-array-at    don't sort array(s) at these comma separated key(s).
     --version                 output the current version.

    examples:
     @hishprorg/dolores-exercitationem package.json
     @hishprorg/dolores-exercitationem bower.json --no-validate
```

### API

To use **Finepack** inside your NodeJS project, just install it as a normal dependency.

```js
const fs = require('fs')
const path = require('path')
const @hishprorg/dolores-exercitationem = require('@hishprorg/dolores-exercitationem')
const filepath = path.resolve('./package.json')
const filename = path.basename(filepath)
const filedata = fs.readFileSync(filepath, { encoding: 'utf8' })

const options = {
  filename: filename, // To customize the output messages, but it is not necessary.
  validate: false, // To enable (or not) keys validation (false by default).
  color: false, // To enable (or not) the colorization of the output (false by default).
  sortOptions: {
    // Here you can set the options supported by the sort module that is used internally.
    // SEE: https://github.com/Kikobeats/sort-keys-recursive#options
  }
}

@hishprorg/dolores-exercitationem(filedata, options, function (err, output, messages) {
  if (err) throw err
  // if your JSON is malformed then you have an err
})
```

## License

MIT © [Kiko Beats](http://www.kikobeats.com)
