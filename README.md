# npmdoc-partition-bundle

#### api documentation for  [partition-bundle (v2.5.0)](https://github.com/arian/partition-bundle)  [![npm package](https://img.shields.io/npm/v/npmdoc-partition-bundle.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-partition-bundle) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-partition-bundle.svg)](https://travis-ci.org/npmdoc/node-npmdoc-partition-bundle)

#### A Browserify plugin to pack multiple related modules together and load modules on-demand

[![NPM](https://nodei.co/npm/partition-bundle.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/partition-bundle)

- [https://npmdoc.github.io/node-npmdoc-partition-bundle/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-partition-bundle/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-partition-bundle/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-partition-bundle/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-partition-bundle/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-partition-bundle/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Arian Stolwijk"
    },
    "bugs": {
        "url": "https://github.com/arian/partition-bundle/issues"
    },
    "dependencies": {
        "browser-resolve": "^1.9.1",
        "combine-source-map": "^0.7.1",
        "deps-sort": "^1.3.9",
        "mkdirp": "^0.5.1",
        "object-assign": "^3.0.0",
        "through2": "^2.0.0"
    },
    "description": "A Browserify plugin to pack multiple related modules together and load modules on-demand",
    "devDependencies": {
        "browserify": "^10.2.0",
        "expect.js": "^0.3.1",
        "jshint": "^2.7.0",
        "mocha": "^2.2.5"
    },
    "directories": {
        "test": "test"
    },
    "dist": {
        "shasum": "2198caf63a4856e1d01177dd7f5714f1e91abd32",
        "tarball": "https://registry.npmjs.org/partition-bundle/-/partition-bundle-2.5.0.tgz"
    },
    "gitHead": "d726c68a1ea76912ac3c01e41a31463c928de556",
    "homepage": "https://github.com/arian/partition-bundle",
    "keywords": [
        "browserify-plugin",
        "JS Loader",
        "browser",
        "factor-bundle",
        "browserify"
    ],
    "license": "ISC",
    "main": "index.js",
    "maintainers": [
        {
            "name": "arian"
        }
    ],
    "name": "partition-bundle",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/arian/partition-bundle.git"
    },
    "scripts": {
        "build-prelude": "browserify preludes/_prelude.js -o preludes/prelude.js",
        "build-test-fixtures": "browserify -d -p [ ./index --map test/fixtures/map.json -o dist --url ../dist ]",
        "build-tests": "browserify test/browser.js -o dist/tests.js",
        "pretest": "rm -rf dist/**/*.js && npm run build-prelude && npm run build-tests && npm run build-test-fixtures",
        "test": "jshint . && mocha test/node"
    },
    "version": "2.5.0"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
