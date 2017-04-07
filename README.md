# api documentation for  [partition-bundle (v2.5.0)](https://github.com/arian/partition-bundle)  [![npm package](https://img.shields.io/npm/v/npmdoc-partition-bundle.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-partition-bundle) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-partition-bundle.svg)](https://travis-ci.org/npmdoc/node-npmdoc-partition-bundle)
#### A Browserify plugin to pack multiple related modules together and load modules on-demand

[![NPM](https://nodei.co/npm/partition-bundle.png?downloads=true)](https://www.npmjs.com/package/partition-bundle)

[![apidoc](https://npmdoc.github.io/node-npmdoc-partition-bundle/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-partition-bundle_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-partition-bundle/build/apidoc.html)

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
            "name": "arian",
            "email": "stolwijk.arian@gmail.com"
        }
    ],
    "name": "partition-bundle",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module partition-bundle](#apidoc.module.partition-bundle)
1.  [function <span class="apidocSignatureSpan">partition-bundle.</span>parallel (array, fn)](#apidoc.element.partition-bundle.parallel)

#### [module partition-bundle.parallel](#apidoc.module.partition-bundle.parallel)
1.  [function <span class="apidocSignatureSpan">partition-bundle.</span>parallel (array, fn)](#apidoc.element.partition-bundle.parallel.parallel)
1.  [function <span class="apidocSignatureSpan">partition-bundle.parallel.</span>errors (args)](#apidoc.element.partition-bundle.parallel.errors)



# <a name="apidoc.module.partition-bundle"></a>[module partition-bundle](#apidoc.module.partition-bundle)

#### <a name="apidoc.element.partition-bundle.parallel"></a>[function <span class="apidocSignatureSpan">partition-bundle.</span>parallel (array, fn)](#apidoc.element.partition-bundle.parallel)
- description and source-code
```javascript
function parallel(array, fn) {

  var length = array.length;
  var results = new Array(length);
  var loaded = 0;

  function wrap(fn, index) {
    fn(function callback(err) {
      results[index] = arguments;
      loaded++;
      ready();
    });
  }

  function ready() {
    if (loaded >= length) {
      fn.apply(null, results);
    }
  }

  ready();

  fold(array, 0, wrap);

}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.partition-bundle.parallel"></a>[module partition-bundle.parallel](#apidoc.module.partition-bundle.parallel)

#### <a name="apidoc.element.partition-bundle.parallel.parallel"></a>[function <span class="apidocSignatureSpan">partition-bundle.</span>parallel (array, fn)](#apidoc.element.partition-bundle.parallel.parallel)
- description and source-code
```javascript
function parallel(array, fn) {

  var length = array.length;
  var results = new Array(length);
  var loaded = 0;

  function wrap(fn, index) {
    fn(function callback(err) {
      results[index] = arguments;
      loaded++;
      ready();
    });
  }

  function ready() {
    if (loaded >= length) {
      fn.apply(null, results);
    }
  }

  ready();

  fold(array, 0, wrap);

}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.partition-bundle.parallel.errors"></a>[function <span class="apidocSignatureSpan">partition-bundle.parallel.</span>errors (args)](#apidoc.element.partition-bundle.parallel.errors)
- description and source-code
```javascript
function errors(args) {
  return fold(args, [], function(val, key, errors) {
    if (val[0]) errors.push(val[0]);
    return errors;
  });
}
```
- example usage
```shell
...
    else loading[file] = [cb];
  });
  return tasks;
});

// when all files are loaded, the modules can be required
parallel(loadTasks, function() {
  var errors = parallel.errors(arguments);
  if (errors.length) {
    errFn(errors[0]);
  } else {
    __requireAll(deps, function(errors, exports) {
      if (errors.length) errFn(errors[0]);
      else fn.apply(null, exports);
    });
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
