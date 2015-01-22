# AnyPromise

AnyPromise is an implementation-agnostic JavaScript interface for
Promises, based on the
[ES6 Promise specification](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise).

Libraries requiring Promises can depend on the interface while letting
the caller provide the implementation.  That way, a library doesn't
have to explicitly depend on a given Promise library; it merely
depends on the abstract interface.

## Example

``` javascript
/* == library.js == */

export function timeoutPromise(Promise, delay) {
  return Promise((resolve, reject) => {
    setTimeout(resolve, delay);
  });
};


/* == consumer.js == */
import {timeoutPromise} from 'library';
import {Promise} from 'any-promise-es6';
// or: import {Promise} from 'any-promise-rsvp';

timeoutPromise(Promise, 1000).then(() => {
  console.log("done waiting 1 second!");
});
```

`timeoutPromise` provides an abstract functionality that depends on a
Promise interface, but not a specific implementation; the
implementation is provided by the caller.

## Interface

TODO: describe the interface

## Adapters

Adapters are thin wrapper libraries that implement the AnyPromise
interface on top of existing Promise libraries:

- [ES6](https://github.com/argo-rest/any-http-es6)
- [AngularJS](https://github.com/argo-rest/any-http-promise)

## Known uses

- [theseus](https://github.com/argo-rest/theseus)

## See also

- [AnyHTTP](https://github.com/argo-rest/any-http)
