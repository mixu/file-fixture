# file-fixture

Generate temporary file/directory names and temporary file/directory structures for writing tests.

## Examples

Preamble:

    var FileFixture = require('file-fixture'),
        fixture = new FileFixture();

`.dirname()`: create a temporary directory

    var outPath = fixture.dirname();

Returns the full path to the file.

`.filename(opts)`: generate a temporary file name.

    var outFile = fixture.filename({ ext: '.js' });

Returns the full path to the directory.

Use the optional `{ ext: '...' }` argument if you want a specific extension.

`.dir(spec)`: generate a temporary directories with specific file names and contents:

    var outDir = fixture.dir({
      'index.js': 'module.exports = require("./second.js");',
      'second.js': 'module.exports = true;'
    });

Returns the path to root of the directory. The directory will contain two files with the given file names and content.

You can also pass an array of strings as the content - it will be joined with newlines before being written:

    var outDir = fixture.dir({
      'index.html': [
        '<html>',
        '  <p>Hello World</p>',
        '</html>'
      ]
    });


`.file(data, opts)`: write a temporary file with a specific content:

    var outPath = fixture.file('<html>Hello world</html>', { ext: '.html'});

Returns the path to the file.
