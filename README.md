# promise-batch
Batch process of list of promises.

```javascript
batcher(paramList, promiseFunc, size, [debug], [onEachChunkComplete])
```
parameters
----------
* **paramList**: Array of parameters will be passed to promiseFunc.
* **promiseFunc**: the promise function.
* **size**: size of concurrent thread.
* **debug** (optional): it log status when necessary.
* **onEachChunkComplete** (optional): Helper function for keep tracking the progress.


Usage
-----
```javascript
var batcher = require('promise-batch');

batcher([[1,'apple'],[2,'orange'],[3,'grape']],function(num,fruit){
  return promise.resolve(num+1);
},2,false,function(currentIndex,totalCount){
  //optional parameter, used to track status
})
.then(function(results){
  console.log('Everything has been completed!!','and the result has been collected in here -->', results);
})
.catch(function(e){
  // capture exception...
})
```

TODOs
-----
- [ ] rewrite using es2015
- [ ] maximize the performance, maintain number of cosncurrent threads.
