# JavaScript style guide

## Table of contents
- [Introduction](#introduction).
- [References](#references).
- [Naming conventions](#naming-conventions).
- [Modules](#modules).

***

## Introduction

The following document is a set of rules or conventions that I take from many others style guides.

This guide does not pretend to substitute the excellent other guides that are out there, is just my personal cheat sheet that I use to work and I decided to share it.

I use [ECMAScript 6](https://es.wikipedia.org/wiki/ECMAScript) specification and [Babel](https://babeljs.io/) as a compiler.

Also, I have another project [js-test-bench](https://github.com/calcaide/js-test-bench) that could be used as a playground to test the conventions or rules that are here.

**[⬆ back to top](#table-of-contents)**

## References

I have different JavaScript style guides as a reference. In fact, this style guide is a result of gather many tips from various places.

Here, some of this style guides that I found interesting or useful.

- [Airbnb](https://github.com/airbnb/javascript).
- [ESLint rules](http://eslint.org/docs/rules/).
- [Idiomatic JS](https://github.com/rwaldron/idiomatic.js).
- [Douglas Crockford](http://javascript.crockford.com/code.html).
- [Google](https://google.github.io/styleguide/javascriptguide.xml).

**[⬆ back to top](#table-of-contents)**

## Naming conventions

<a name="naming--descriptive"></a><a name="1.1"></a>
- [1.1](#naming--descriptive) Be descriptive with your naming, avoid single letter names and too many long ones. ESLint: [`id-length`](http://eslint.org/docs/rules/id-length)

```javascript
// avoid
function q() {
    // code..
}

// recommended
function getQueryObject() {
    // code..
}
```

<a name="naming--lowerCamelCase"></a><a name="1.2"></a>
- [1.2](#naming--lowerCamelCase) Use lowerCamelCase when naming **objects**, **functions**, and **instances**. ESLint: [camelCase](http://eslint.org/docs/rules/camelcase).

```javascript
// avoid
let SOMEobj = {};

function get-query-object() {
    // code...
};

// recommended
let someObj = {};

function getQueryObject() {
    // code...
}
```

<a name="naming--UpperCamelCase"></a><a name="1.3"></a>
- [1.3](#naming-UpperCamelCase) Use UpperCamelCase only when naming **constructors** or **classes**. ESLint: [new-cap](http://eslint.org/docs/rules/new-cap).

```javascript
// avoid
class bankAccount {
    constructor(param1){
        // code...
    }
}

const myAccount = new bankAccount('Something');


// recommended
class BankAccount {
    constructor(param1){
        // code...
    }
}

const myAccount = new BankAccount('Something');
```

<a name="naming--UPPERCASE"></a><a name="1.4"></a>
- [1.4](#naming-UPPERCASE) Use UPPER_CASE for **constants**. ESLint: [camelCase](http://eslint.org/docs/rules/camelcase).

```javascript
// avoid
const userPermissions = 0777;

// recommended
const USER_PERMISSIONS = 0777;
```

<a name="naming--underscores"></a><a name="1.5"></a>
- [1.5](#naming--underscores) Do not use trailing or leading underscores. ESLint: [no-underscore-dangle](http://eslint.org/docs/rules/no-underscore-dangle).

*This rule is for the long history of using dangling underscores to indicate "private" members of objects, take more information about that in the ESLint rule [no-underscore-dangle](http://eslint.org/docs/rules/no-underscore-dangle).*

```javascript
// avoid
this._someValue = 'Something';
this._someNumber_ = 17;

// recommended
this.someValue = 'Something';
this.someNumber = 17;

// recommended
```

**[⬆ back to top](#table-of-contents)**


## Modules

<a name="modules--strict-mode"></a><a name="2.1"></a>
- [2.1](#modules--strict-mode) Do not write more `"use strict"`. ESLint: [strict](http://eslint.org/docs/rules/strict).

*Why?* because ES6 modules are always in strict mode. Here [the spec](http://www.ecma-international.org/ecma-262/6.0/#sec-strict-mode-code).

<a name="modules--use-modules"></a><a name="2.2"></a>
- [2.2](#modules--use-modules) Use always ES6 modules (`import` / `export`) instead of a non-standard module system.

```javascript
// avoid (AMD)
define(function(){
    return something;
});

// avoid (CommonJS)
module.exports = 'something';

// recommended
import assets from './assets';

    // code...

const api = {
    getTask
}

export default api;
```

<a name="modules--imports-above"></a><a name="2.3"></a>
- [2.3](#modules--imports-above) Put all the imports above.

*Why?* Imports are hoisted, keeping them all at the top, give up consistency and better developer experience.

```javascript
// avoid
import foo from 'foo';

foo.init();

import bar from 'bar';

// recommended
import foo from 'foo';
import bar from 'bar';

foo.init();
```

