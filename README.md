# JavaScript style guide

The following document is a set of rules or conventions that I take from many others style guides.

This guide does not pretend to substitute the excellent other guides that are out there, is just my personal cheat sheet that I use to work and I decided to share it.

I use [ECMAScript 6](https://en.wikipedia.org/wiki/ECMAScript) specification and [Babel](https://babeljs.io/) as a compiler.

Also, I have another project [js-test-bench](https://github.com/calcaide/js-test-bench) that could be used as a playground to test the conventions or rules that are here.

## References

I have different JavaScript style guides as a reference. In fact, this style guide is a result of gather many tips from various places.

Here, some of this style guides that I found interesting or useful.

- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript).
- [ESLint rules](http://eslint.org/docs/rules/).
- [Idiomatic JS](https://github.com/rwaldron/idiomatic.js).
- [Douglas Crockford](http://javascript.crockford.com/code.html).
- [Google](https://google.github.io/styleguide/javascriptguide.xml).
- [MDN](https://developer.mozilla.org/en/).
- [②ality](http://www.2ality.com/).


## Table of contents

1. [Naming conventions](#naming-conventions).
2. [Whitespace](#whitespace).
3. [Modules](#modules).
4. [Classes](#classes).
5. [Blocks](#blocks).
6. [Variables](#variables).

***

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
- [1.2](#naming--lowerCamelCase) Use lowerCamelCase when naming **objects**, **functions**, and **instances**. ESLint: [`camelCase`](http://eslint.org/docs/rules/camelcase).

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
- [1.3](#naming-UpperCamelCase) Use UpperCamelCase only when naming **constructors** or **classes**. ESLint: [`new-cap`](http://eslint.org/docs/rules/new-cap).

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
- [1.4](#naming-UPPERCASE) Use UPPER_CASE for **constants**. ESLint: [`camelCase`](http://eslint.org/docs/rules/camelcase).

```javascript
// avoid
const userPermissions = 0777;

// recommended
const USER_PERMISSIONS = 0777;
```

<a name="naming--underscores"></a><a name="1.5"></a>
- [1.5](#naming--underscores) Do not use trailing or leading underscores. ESLint: [`no-underscore-dangle`](http://eslint.org/docs/rules/no-underscore-dangle).

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


## Whitespace

*There is no Why explanation in these statements because all are very personal preferences, in most of them are open discussions in the community, so you don't have a clear answer about it.*

<a name="whitespace--indent"></a><a name="2.1"></a>
- [2.1](#whitespaces--indent) Use 4 spaces for indent. ESLint: [`indent`](http://eslint.org/docs/rules/indent).

```javascript
// avoid
function foo(){
∙∙const bar;
}

// recommended
function foo(){
∙∙∙∙const bar;
}
```

<a name="whitespace--before-blocks"></a><a name="2.2"></a>
- [2.2](#whitespace--before-blocks) Place 1 space before blocks. ESLint: [`space-before-blocks`](http://eslint.org/docs/rules/space-before-blocks).

```javascript
// avoid
if (foo){
    bar();
}

function bar(){
    console.log('bar() function');
}

// recommended
if (foo) {
    bar();
}

function bar() {
    console.log('bar() function');
}
```

<a name="whitespace--before-opening"></a><a name="2.3"></a>
- [2.3](#whitespace--before-opening) Place 1 space before the opening parenthesis in control statements (`import`, `export`, `class`, `if`, `while`, etc). Place no space in function name in function calls and declarations. ESLint: [`keyword-spacing`](http://eslint.org/docs/rules/keyword-spacing).

```javascript
// avoid
if(foo) {
    bar();
}

function bar () {
    console.log('bar() function');
}

// recommended
if (foo) {
    bar();
}

function bar() {
    console.log('bar() function');
}
```

<a name="whitespace--around-operators"></a><a name="2.4"></a>
- [2.4](#whitespace--around-operators) Place spaces around operators. ESLint: [`space-infix-ops`](http://eslint.org/docs/rules/space-infix-ops).

```javascript
// avoid
const sum=a+b;

// recommended
const sum = a + b;
```

<a name="whitespace--indented-line"></a><a name="2.5"></a>
- [2.5](#whitespace--indented-line) Require and indented new line when making long method chains (more than two method chains) or when are too large. Use a leading dot to emphasizes that the line is not a new statement. ESLint: [`newline-per-chained-call`](http://eslint.org/docs/rules/newline-per-chained-call).

```javascript
// avoid
angular.module('fooModule', []).component('someComponent', SomeComponent).name;

doSomething().then(doSomethingElse).then(result => { console.log(result) });

// recommended
angular
    .module('fooModule', [])
    .component('someComponent', SomeComponent)
    .name;

doSomething()
    .then(doSomethingElse)
    .then( result => {
        console.log(result);
    });
```

<a name="whitespace--after-block"></a><a name="2.6"></a>
- [2.6](#whitespace--after-block) Leave a blank line after blocks and before the next statement.

```javascript
// avoid
if (foo) {
    bar();
}
return baz;

const arr = [
    function foo() {
    },
    function bar() {
    }
];
return arr;

// recommended
if (foo) {
    bar();
}

return baz;

const arr = [
    function foo() {
    },

    function bar() {
    }
]
```

<a name="whitespace--inside-parenthesis"></a><a name="2.7"></a>
- [2.7](#whitespace--inside-parenthesis) Do not add spaces inside a parenthesis. ESLint: [`space-in-parens`](http://eslint.org/docs/rules/space-in-parens).

```javascript
// avoid
const math = ( 2 + 2 ) * 3;
foo(math, [2,4] );

// recommended
const math = (2 + 2) * 3;
foo(math, [2,4]);
```

<a name="whitespace--inside-brackets"></a><a name="2.8"></a>
- [2.8](#whitespace--inside-brackets) Do not add space inside brackets. ESLint: [`array-bracket-spacing`](http://eslint.org/docs/rules/array-bracket-spacing).

```javascript
// avoid
const arr = [ 'foo', 'bar' ];
const numArr = [ 1, 2, 3, 4 ];

// recommended
const arr = ['foo', 'bar'];
const numArr = [1, 2, 3, 4];
```

<a name="whitespace--inside-curly"></a><a name="2.9"></a>
- [2.9](#whitespace--inside-curly) Do not add spaces inside curly braces. ESLint: [`object-curly-spacing`](http://eslint.org/docs/rules/object-curly-spacing).

```javascript
// avoid
const obj = { foo: [1,2], bar: 'baz', baz: 'bar', num: 17 };

// recommended
const obj = {foo: [1,2], bar: 'baz', baz: 'bar', num: 17};
```

<a name="whitespace--lines-longer"></a><a name="2.10"></a>
- [2.10](#whitespace--lines-longer) Avoid having lines of code that are longer than 80 characters (including whitespaces). Except for strings. ESLint: [`max-len`](http://eslint.org/docs/rules/max-len). ESLint: [`object-curly-spacing`](http://eslint.org/docs/rules/object-curly-spacing)

```javascript
// avoid
const obj = {bar: 'this pretends to be a long object', foo: {arr: [1,2,3,4], baz: 'this also pretends to be a long object'}};

// recommended
const obj = {
    bar: 'this pretends to be a long object',
    foo: {
        arr: [1,2,3,4],
        baz: 'this also pretends to be a long object'
    }
};
```

**[⬆ back to top](#table-of-contents)**

## Modules

<a name="modules--strict-mode"></a><a name="3.1"></a>
- [3.1](#modules--strict-mode) Do not write more `"use strict"`. ESLint: [`strict`](http://eslint.org/docs/rules/strict).

*Why?* because ES6 modules are always in strict mode. Here [the spec](http://www.ecma-international.org/ecma-262/6.0/#sec-strict-mode-code).

<a name="modules--use-modules"></a><a name="3.2"></a>
- [3.2](#modules--use-modules) Use always ES6 modules (`import` / `export`) instead of a non-standard module system.

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

<a name="modules--imports-above"></a><a name="3.3"></a>
- [3.3](#modules--imports-above) Put all the imports above. ESLint [plugin](https://github.com/benmosher/eslint-plugin-import/): [`import/first`](https://github.com/benmosher/eslint-plugin-import/blob/master/docs/rules/first.md)

*Why?* Imports are hoisted, keeping them all at the top, give up consistency and better developer experience.

```javascript
// avoid
import library1 from 'library1';
library1.init();

import library2 from 'library2';

// recommended
import library1 from 'library1';
import library2 from 'library2';

library1.init();
```

<a name="modules--not-wildcards"></a><a name="3.4"></a>
- [3.4](#modules--not-wildcards) Do not use wildcard imports.

*Why?* This makes sure you have a single default export.

```javascript
// avoid
import * as foo from 'foo';

// recommended
import foo from 'foo';
```

<a name="modules--import-one-place"></a><a name="3.5"></a>
- [3.5](#modules--import-one-place) Only import from a path in one place. ESLint: [`no-duplicate-imports`](http://eslint.org/docs/rules/no-duplicate-imports)

*Why?* Import from the same path in different lines can make code harder to maintain.

```javascript
// avoid
import library1 from 'library1';
import { function1, function2 } from 'library1';

// recommended
import library1 , { function1, function2 } from 'library1';
```

<a name="modules--exports-below"></a><a name="3.6"></a>
- [3.6](#modules--exports-below) Put all the exports at the end of the module file.

*Why?* Becomes evident what you are exporting instead of having to crawl around the module.

```javascript
// avoid
const numA = 17;
const numB = 21;

export default numA;

const numC = 44;

// recommended
const numA = 17;
const numB = 21;
const numC = 44;

export default numA; 

```

<a name="modules--default-export"></a><a name="3.7"></a>
- [3.7](#modules--default-export) Always use a default export, and export an API object. ESLint [plugin](https://github.com/benmosher/eslint-plugin-import/): [`import/prefer-default-export`](https://github.com/benmosher/eslint-plugin-import/blob/master/docs/rules/prefer-default-export.md)

*Why?* [Pony Foo](https://ponyfoo.com/articles/es6-modules-in-depth#best-practices-and-export).

*Why?* Consistency, having one clear way to export make things consistent.

```javascript
// avoid
let sum = (a,b) => a+b:
const foo = 17;

export {sum, foo};

// recommended
let sum = (a,b) => a+b;
const foo = 17;

const api = {
    sum,
    foo
}

export default api;
```

<a name="modules--export-mutable"></a><a name="3.8"></a>
- [3.8](#modules--export-mutable) Do not export mutable bindings. ESLint [plugin](https://github.com/benmosher/eslint-plugin-import/): [`import/no-mutable-exports`](https://github.com/benmosher/eslint-plugin-import/blob/master/docs/rules/no-mutable-exports.md)

*Why?* Mutation should be avoided in general, but in particular when exporting mutable bindings.

*Note:* If you use the technique described above, ["Always use a default export, an export and API"](#modules--default-export) You just have to think about that when working with code from a third party.

```javascript
// avoid
let numA = 17;
let numB = 22;
export { numA, numB };

// recommended
const numA = 17;
const numB = 22;

const api = {
    numA,
    numB
}

export default api;
```

<a name="modules--export-from-import"></a><a name="3.9"></a>
- [3.9](#modules--export-from-import) Never export directly from an import.

*Why?* One line is shorter and concise, but having one clear way to import and export makes things consistent and better for the developer experience.

```javascript
// avoid
export { FooAction, BarAction } from './actionCreators.js';

// recommended
import { FooAction, BarAction} from './actionCreators.js';

const api = {
    FooAction,
    BarAction
}

export default api;
```

**[⬆ back to top](#table-of-contents)**

## Classes

<a name="classes--use-class"></a><a name="5.1"></a>
- [5.1](#classes--use-class) Always use `class`. Avoid manipulating `prototype` directly.

*Why?* Javascript classes introduced in ECMAScript 6, are syntactical sugar over prototype-based inheritance and provide a much simpler and clear syntax to create objects and deal with class inheritance.

```javascript
// avoid
function Vehicle(type, wheels){
    this.type = type;
    this.wheels = wheels;
}

Vehicle.prototype.toString = function(){
   return "Vehicle type: "+this.type+", Wheels: "+this.wheels;
}

// recommended
class Vehicle {
    constructor(type, wheels){
        this.type = type;
        this.wheels = wheels;
    }

    toString(){
        return "Vehicle type: "+this.type+", Wheels: "+this.wheels;
    }
}
```

<a name="classess--use-extends"></a><a name="4.2"></a>
- [4.2](#classes--use-extends) Use `extends` for inheritance.

*Why?* It is and abstraction to inherit prototype, again, much simpler and clear than classical prototype inheritance.

*Note*: in inheritance, `Vehicle` class is a **base class**, and `Car` is a **derived class**.

```javascript
// avoid
function Vehicle(type, wheels){
    this.type = type;
    this.wheels = wheels;
}

Vehicle.prototype.toString = function(){
   return "Vehicle type: "+this.type+", Wheels: "+this.wheels;
}

Car.prototype = new Vehicle('Car',4);
Car.prototype.constructor = Car;

function Car(brand){
   this.brand = brand;
}

Car.prototype.toString = function(){
   return "Vehicle type: "+this.type+", Wheels: "+this.wheels+", Brand: "+this.brand;
}

// recommended
class Vehicle {

    constructor(type, wheels){
        this.type = type;
        this.wheels = wheels;
    }

    toString(){
        return "Vehicle type: "+this.type+", Wheels "+this.wheels;
    }
}

class Car extends Vehicle {

    constructor(type, wheels, brand){
        super(type, wheels);
        this.brand = brand;
    }

    toString(){
        super.toString()+", Brand "+this.brand;
    }
}

```

<a namre="classes--super-calls"></a><a name="4.3"></a>
- [4.3](#) Uses super calls: superconstructor and superproperties.

```javascript
class A {
    constructor(prop1, prop2){
        this.prop1 = prop1;
        this.prop2 = prop2;
    }

    toString(){
        return 'Prop1: '+this.prop1+', Prop2: '+this.prop2;
    }
}

class B extends A {
    constructor(prop1, prop2, prop3){
        super(prop1, prop2);
        this.prop3 = prop3;
    }

    toString(){
        return super.toString()+', Prop3: '+this.prop3;
    }
}
```

<a name="classes--default-constructor"></a><a name="4.4"></a>
- [4.4](#classes--default-constructor) Classes have a default constructor if one is not specified. An empty constructor function or one that just delegates to a parent class is unnecessary. ESLint: [`no-useless-constructor`](http://eslint.org/docs/rules/no-useless-constructor).

```javascript
// avoid
class A { // Base class 
    constructor(){

    }   
}

class A extends B { // Derived class
    constructor(..args){
        super(...args);
    }
}

// recommended

class A { // Base class
    
}

class A extends B { // Derived class
    constructor(...args){
        super(...args);
        this.foo = 'bar';
    }
}
```

<a name="classes--duplicate-members"></a><a name="4.5"></a>
- [4.5](#classes--duplicate-members) Avoid duplicate class members. ESLint: [`no-dupe-class-members`](http://eslint.org/docs/rules/no-dupe-class-members).

*Why?* The last declaration overwrites other declarations silently.

```javascript
class Foo {
    bar() {
        return true;
    }

    bar() {
        return false;
    }
}

const foo = new Foo();
foo.bar(); // false
```

**[⬆ back to top](#table-of-contents)**

## Blocks
<a name="blocks--brace-style"></a><a name="5.1"></a>
- [5.1](#blocks--brace-style) Use always braces with all multi-line blocks and put the next condition in the same place that the first close the brace (the clearest example of that is with an `if` `else` statement). ESLint: [`brace-style`](http://eslint.org/docs/rules/brace-style.html)

*Why?* to follow [the one true brace style](https://en.wikipedia.org/wiki/Indent_style#Variant:_1TBS_.28OTBS.29)

```javascript
// avoid
function foo(){ return false; }

if(something)
    return true;

if(true){
    return false;
}
else{
    return true;
}

// recommended
function foo(){
    return false;   
}

if(something){
    return true;
}

if(true){
    return false;
}else{
    return true;
}
```

**[⬆ back to top](#table-of-contents)**

## Variables
<a name="variables--never-use-var"></a><a name="6.1"></a>
- [6.1](#variables--never-use-var) Never use `var`, always use `const` or `let`. ESLint: [`no-var`](http://eslint.org/docs/rules/no-var).

*Why?* `let` and `const` are block scoped instead of `var`, that is a function scoped.

```javascript
// avoid
var foo = "bar";
var VERSION = 1;

// recommended
let foo = "bar";
const VERSION = 1;
```

<a name="variables--always-use-const"></a><a name="6.2"></a>
- [6.2](#variables--always-use-const) Always use `const` to declare variables that don't need to reassign. ESLint: [`prefer-const`](http://eslint.org/docs/rules/prefer-const).

*Why?* `const` declaration means the variable is never reassigned, reducing cognitive load and improving maintainability.

```javascript
// avoid
for(let foo in [1,2,3]){ // foo is redefined (not reassigned) on each loop step.
    console.log(foo);
}

for(const foo = 0; foo < 3; foo+=1){ // ERROR. foo is reassigned with a new value each loop step.
    console.log(foo);
}

// recommended
for(const foo in [1,2,3]){ 
    console.log(foo);
}

for(let foo = 0; foo < 3; foo+=1){
    console.log(foo);
}
```

<a name="variables--one-declaration"></a><a name="6.3"></a>
- [6.3](#variables--one-declaration) Use one `const` or `let` declaration per variable. ESLint: [`one-var`](http://eslint.org/docs/rules/one-var).

*Why?* Mainly for the style but also for developer experience (always use a `;` at the end of a declaration).

```javascript
// avoid
const   foo,
        bar;
let     fox,
        box;

// recommended
const foo;
const bar;
let fox;
let box;
```

<a name="variables--group"></a><a name="6.4"></a>
- [6.4](#variables--group) Group all your `const`s and then group all your `let`s.

*Why?* Improve developer experience.

```javascript
// avoid
const favNum = 17;
let foo = 'bar';
const i;
let counter;

// recommended
const favNum = 17;
const i;
let foo = 'bar';
let counter;
```

<a name="variables--unary"></a><a name="6.5"></a>
- [6.5](#variables--unary) Not use unary `++` increments and `--` decrements. ESLint: [`no-plusplus`](http://eslint.org/docs/rules/no-plusplus).

*Why?* From ESLint documentation: the unary `++` and `--` operators are subject to automatic semicolon insertion, differences in whitespace can change semantics of source code.

*Why?* Is more clear to mutate values with `num += 1` than `num++`.

```javascript
// avoid
let counter = 0;
counter++;

// recommended
let counter = 0;
counter +=1;
```

**[⬆ back to top](#table-of-contents)**