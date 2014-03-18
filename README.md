Task/1.0
========

> JavaScript Task Specification

Task is unit of execution. In the javascript world, there have existing hundreds of tasks that we can use, 
like `jshint`, `csslint`, `uglifyjs`, `jade`, `jasmine`, etc. But they are all unconnected, this specification addresses how tasks should be written in order to be connected that can be both client and server side.

## 1. Terminology

1. `task` is an object or function with a `run` method whose behavior conforms to this specification.
2. `thenable` is an object or function that defines a `then` method.
3. `records` is array of [Record](https://github.com/node-task/record) instances.
4. `logger` is a `Logging` object, default is `console`.

## 2. Requirements

### 2.1 The `run` Method
A task must provide a `run` method must returning a `thenable`. A task’s `run` method accepts three arguments, and all arguments are optional:

```js
run([records [, options [, logger]]])
```

Within Common.JS modules ecosystem, the entry point module like `index.js` should exports `run` method:

```js
// index.js
exports.run = function(records, options, logger){
  return new Promise(function(resolve, reject){
     logger.log("it's work")
     resolve(records);
  })
}
```

## 3. Implementations
 * [Node packages](https://github.com/taskjs/packages)
