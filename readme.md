# chuk-cb

Chuk plugin which simplifys writing callbacks in REPL session.

## Installation

```bash
$ npm install chuk-cb
```

## Usage

After installing cb add this code to your Chukfile

```js
scope.cb = require('chuk-cb')(scope);
```

Your Chukfile may now look like this:

```js
module.exports = function(scope) {
  // some other initialisation
  scope.cb = require('chuk-cb')(scope);
};
```

If you now run Chuk and you have a call which requires a callback function
which arguments you want to use if called, simply pass `cb`to that call.
Instead of

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
