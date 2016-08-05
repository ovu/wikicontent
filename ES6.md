ECMASCRIPT 6 features
=====================

###Object initializer

Bracket notation

Sample:

  const variable = 'Test';

  const myObject { [variable]: 'Value' }

myObject will be {'Test': 'Value'}

More information in the official reference: http://www.ecma-international.org/ecma-262/6.0/#sec-object-initializer

###Arrow functions

In single line arrow functions perform an implicit return.

For example:

  getUsers()
  .then((users) => 'OK')

A complete explained sample can be found here: https://strongloop.com/strongblog/an-introduction-to-javascript-es6-arrow-functions/
