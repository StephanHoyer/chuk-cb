 [![Build
 Status](https://travis-ci.org/StephanHoyer/chuk-cb.png?branch=master)](https://travis-ci.org/StephanHoyer/chuk-cb)

 # chuk-cb

[Chuk](https://github.com/StephanHoyer/chuk) plugin which simplifys writing callbacks in REPL session.

## Installation

```bash
$ npm install chuk-cb
```

## Usage

After installing cb add this code to your `Chukfile`

```js
scope.cb = require('chuk-cb')(scope);
```

Your `Chukfile` may now look like this:

```js
module.exports = function(scope) {
  // some other initialisation
  scope.cb = require('chuk-cb')(scope);
};
```

If you now run `chuk` and you have a call which requires a callback function
which arguments you want to use if called, simply pass `cb` to that call.
So instead of

```
chuk > var foo
chuk > User.findOne({name: 'foo'}, function(err, user) { foo = user; })
chuk > user
{ name: 'foo', haircolor: 'bar' }
```

simply write

```
chuk > User.findOne({name: 'foo'}, cb)
_0 = null
_1 = [object Object]
undefined
chuk > _1
{ name: 'foo', haircolor: 'bar' }
```

As you can see `cb` adds the parameters of it to the global scope.

## License

(The MIT License)

Copyright (c) 2012 Stephan Hoyer <ste.hoyer@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

