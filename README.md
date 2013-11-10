Task.JS
====

> The Simplest JavaScript Task Specification

Task is unit of execution. In the javascript world, there have existing hundreds of tasks that we can use, 
like `jshint`, `csslint`, `uglifyjs`, `jade`, `jasmine`, etc. But they are all unconnected, 
if we need execute a series of tasks, we should make the adapter for each type task within task runner like `grunt`. 
Then we got some modules named `grunt-jshint`, `grunt-csslint`, `grunt-uglifyjs`, `grunt-jade`, `grunt-jasmine`, etc.

Could we connect these tasks without task adapter? 
This specification addresses how tasks should be written in order to be connected without adapter that can be both client and server side.

### API

This specification only defines one API that a module should be exported：

```js
task.run([options [, done]])
```

* `options` should be a object
* `done` should be a function


Within Common.JS modules ecosystem, the entry point module like `main.js` should exports `.run()` method:

```js
// asyncTask.js
exports.run = function(options, done){
  setTimeout(function(){
    console.log("it's work")
    done()
  }, 2013)
}
```

When task is sync, `done` could be optional.

```js
// syncTask.js
exports.run = function(options){
  console.log("it's work")
}
```

### Runner Implementations
* [Mod.js](https://github.com/modulejs/modjs) - JavaScript Workflow Tooling For Web Application

