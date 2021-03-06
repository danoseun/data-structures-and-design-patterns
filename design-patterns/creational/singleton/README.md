# Singleton Pattern

This restricts instantiaton of objects to only one instance. It is implemented by creating a class with a method that instantiates a new object

Singletons differ from normal classes because their instantiation can be delayed, probably because they require some information before initialization.

```js
const MySingleton = (function() {
  let instance
  function privateMethod() {
    return 1
  }
  function init() {
    const myNumber = Math.random();
    let publicValue = 0
    function publicFunction() {
      return myNumber;
    }
    function privateFunction() {
      myNumber++;
    }
    return {
      value: publicValue,
      func: publicFunction,
      getOne: privateMethod,
      increment: function() {
        privateFunction();
      }
    }
  }
  return function getInstance() {
    if (!instance) {
      instance = init()
    }
    return instance;
  }
})()
```