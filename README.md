# api documentation for  [node-oauth2-server (v2.4.0)](https://github.com/thomseddon/node-oauth2-server)  [![npm package](https://img.shields.io/npm/v/npmdoc-node-oauth2-server.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-node-oauth2-server) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-node-oauth2-server.svg)](https://travis-ci.org/npmdoc/node-npmdoc-node-oauth2-server)
#### Complete, compliant and well tested module for implementing an OAuth2 Server/Provider with express in node.js

[![NPM](https://nodei.co/npm/node-oauth2-server.png?downloads=true)](https://www.npmjs.com/package/node-oauth2-server)

[![apidoc](https://npmdoc.github.io/node-npmdoc-node-oauth2-server/build/screenCapture.buildNpmdoc.browser.%252Fhome%252Ftravis%252Fbuild%252Fnpmdoc%252Fnode-npmdoc-node-oauth2-server%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-node-oauth2-server/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-node-oauth2-server/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-node-oauth2-server/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Thom Seddon",
        "email": "thom@seddonmedia.co.uk"
    },
    "bugs": {
        "url": "https://github.com/thomseddon/node-oauth2-server/issues"
    },
    "contributors": [
        {
            "name": "Thom Seddon",
            "email": "thom@seddonmedia.co.uk"
        }
    ],
    "dependencies": {
        "basic-auth": "~0.0.1"
    },
    "description": "Complete, compliant and well tested module for implementing an OAuth2 Server/Provider with express in node.js",
    "devDependencies": {
        "body-parser": "~1.3.1",
        "express": "~4.4.3",
        "mocha": "~1.20.1",
        "should": "~4.0.4",
        "supertest": "~0.13.0"
    },
    "directories": {},
    "dist": {
        "shasum": "2893eb0c118c3f05fc7fbeace4a33e3bf4ec69de",
        "tarball": "https://registry.npmjs.org/node-oauth2-server/-/node-oauth2-server-2.4.0.tgz"
    },
    "engines": {
        "node": ">=0.8"
    },
    "gitHead": "4f7899b798c16cec0aee08285012ffb5f6fd3c4b",
    "homepage": "https://github.com/thomseddon/node-oauth2-server",
    "keywords": [
        "oauth",
        "oauth2"
    ],
    "licenses": [
        {
            "type": "Apache 2.0",
            "url": "http://www.apache.org/licenses/LICENSE-2.0.html"
        }
    ],
    "main": "lib/oauth2server.js",
    "maintainers": [
        {
            "name": "thomseddon",
            "email": "thom@nightworld.com"
        }
    ],
    "name": "node-oauth2-server",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/thomseddon/node-oauth2-server.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "2.4.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module node-oauth2-server](#apidoc.module.node-oauth2-server)
1.  [function <span class="apidocSignatureSpan">node-oauth2-server.</span>error (error, description, err)](#apidoc.element.node-oauth2-server.error)

#### [module node-oauth2-server.error](#apidoc.module.node-oauth2-server.error)
1.  [function <span class="apidocSignatureSpan">node-oauth2-server.</span>error (error, description, err)](#apidoc.element.node-oauth2-server.error.error)
1.  [function <span class="apidocSignatureSpan">node-oauth2-server.error.</span>super_ ()](#apidoc.element.node-oauth2-server.error.super_)



# <a name="apidoc.module.node-oauth2-server"></a>[module node-oauth2-server](#apidoc.module.node-oauth2-server)

#### <a name="apidoc.element.node-oauth2-server.error"></a>[function <span class="apidocSignatureSpan">node-oauth2-server.</span>error (error, description, err)](#apidoc.element.node-oauth2-server.error)
- description and source-code
```javascript
function OAuth2Error(error, description, err) {
  if (!(this instanceof OAuth2Error))
    return new OAuth2Error(error, description, err);

  Error.call(this);

  this.name = this.constructor.name;
  if (err instanceof Error) {
    this.message = err.message;
    this.stack = err.stack;
  } else {
    this.message = description;
    Error.captureStackTrace(this, this.constructor);
  }

  this.headers = {
    'Cache-Control': 'no-store',
    'Pragma': 'no-cache'
  };

  switch (error) {
    case 'invalid_client':
      this.headers['WWW-Authenticate'] = 'Basic realm="Service"';
<span class="apidocCodeCommentSpan">      /* falls through */
</span>    case 'invalid_grant':
    case 'invalid_request':
      this.code = 400;
      break;
    case 'invalid_token':
      this.code = 401;
      break;
    case 'server_error':
      this.code = 503;
      break;
    default:
      this.code = 500;
  }

  this.error = error;
  this.error_description = description || error;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.node-oauth2-server.error"></a>[module node-oauth2-server.error](#apidoc.module.node-oauth2-server.error)

#### <a name="apidoc.element.node-oauth2-server.error.error"></a>[function <span class="apidocSignatureSpan">node-oauth2-server.</span>error (error, description, err)](#apidoc.element.node-oauth2-server.error.error)
- description and source-code
```javascript
function OAuth2Error(error, description, err) {
  if (!(this instanceof OAuth2Error))
    return new OAuth2Error(error, description, err);

  Error.call(this);

  this.name = this.constructor.name;
  if (err instanceof Error) {
    this.message = err.message;
    this.stack = err.stack;
  } else {
    this.message = description;
    Error.captureStackTrace(this, this.constructor);
  }

  this.headers = {
    'Cache-Control': 'no-store',
    'Pragma': 'no-cache'
  };

  switch (error) {
    case 'invalid_client':
      this.headers['WWW-Authenticate'] = 'Basic realm="Service"';
<span class="apidocCodeCommentSpan">      /* falls through */
</span>    case 'invalid_grant':
    case 'invalid_request':
      this.code = 400;
      break;
    case 'invalid_token':
      this.code = 401;
      break;
    case 'server_error':
      this.code = 503;
      break;
    default:
      this.code = 500;
  }

  this.error = error;
  this.error_description = description || error;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.node-oauth2-server.error.super_"></a>[function <span class="apidocSignatureSpan">node-oauth2-server.error.</span>super_ ()](#apidoc.element.node-oauth2-server.error.super_)
- description and source-code
```javascript
function Error() { [native code] }
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
