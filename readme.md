# remark-reference-links [![Build Status][build-badge]][build-status] [![Coverage Status][coverage-badge]][coverage-status] [![Chat][chat-badge]][chat]

[**remark**][remark] plug-in to transform links and images into
references and definitions.

## Installation

[npm][]:

```bash
npm install remark-reference-links
```

## Usage

Say we have the following file, `example.md`:

```markdown
[foo](http://example.com "Example Domain"), [foo](http://example.com "Example Domain"), [bar](http://example.com "Example Domain").

![foo](http://example.com "Example Domain"), ![foo](http://example.com "Example Domain"), ![bar](http://example.com "Example Domain").
```

And our script, `example.js`, looks as follows:

```javascript
var fs = require('fs');
var remark = require('remark');
var links = require('remark-reference-links');

remark()
  .use(links)
  .process(fs.readFileSync('example.md'), function (err, file) {
    if (err) throw err;
    console.log(String(file));
  });
```

Now, running `node example` yields:

```markdown
[foo][1], [foo][1], [bar][1].

![foo][1], ![foo][1], ![bar][1].

[1]: http://example.com "Example Domain"
```

## API

### `remark.use(referenceLinks)`

Transform links and images into references and definitions.

## Related

*   [`remarkjs/remark-inline-links`](https://github.com/remarkjs/remark-inline-links)
    — Reverse, thus rewriting references and definitions into normal links
    and images
*   [`eush77/remark-defsplit`](https://github.com/eush77/remark-defsplit)
    — Reverse, thus rewriting references and definitions into normal links
    and images, but with URI-based identifiers instead of numerical ones

## License

[MIT][license] © [Titus Wormer][author]

<!-- Definitions -->

[build-badge]: https://img.shields.io/travis/remarkjs/remark-reference-links.svg

[build-status]: https://travis-ci.org/remarkjs/remark-reference-links

[coverage-badge]: https://img.shields.io/codecov/c/github/remarkjs/remark-reference-links.svg

[coverage-status]: https://codecov.io/github/remarkjs/remark-reference-links

[chat-badge]: https://img.shields.io/gitter/room/remarkjs/Lobby.svg

[chat]: https://gitter.im/remarkjs/Lobby

[license]: LICENSE

[author]: http://wooorm.com

[npm]: https://docs.npmjs.com/cli/install

[remark]: https://github.com/remarkjs/remark
