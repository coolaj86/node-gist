## Node.js Gist client

Gist API v3 client for Node.JS

## Installation

For use in your modules (adds to package.json automatically)

    # Old 0.2 in npm
    npm install -S gist

    # Bleeding Edge
    npm install -S 'git://github.com/coolaj86/node-gist.git'

    # v1.0.2
    npm install -S 'git://github.com/coolaj86/node-gist.git#v1.0.2'

For the commandline gist

    npm install -g gist

    npm install -g 'git://github.com/coolaj86/node-gist.git'

    npm install -g 'git://github.com/coolaj86/node-gist.git#v1.0.2'

## Usage

### Commandline

    gist </path/to/file>

    echo "Hello World!" > ./hello.txt
    gist ./hello.txt

### API

  * `gist.gists([username], fn)`
  * `gist.gist(id, fn)`
  * `gist([validOauthToken]).create(newGist, fn)`

```javascript
var gist = require('gist')(validOAuthToken);

// get all your gists (or all public if you didnt specify a token)
gist.gists(function(err, resp, json) {
  console.log(err, json)
})

// get all public gists for some user
gist.gists('maxogden', function(err, resp, json) {
  console.log(err, json)
})

// get a gist by id
gist.gist('2698151', function(err, resp, json) {
  console.log(err, json)
})

// creating a new gist
var newGist = {
  "description": "the description for this gist",
  "public": false,
  "files": {
    "file1.txt": {
      "content": "String file contents"
    }
  }
}
gist(validOauthToken).create(newGist, function(err, resp, json) {
  console.log(err, json)
})
```

## Author

* Max Ogden (@maxogden)

this library was forked from Emerson Macedo (<http://codificando.com/>) and entirely rewritten

## License

(The MIT License)

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
