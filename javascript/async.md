<details>
<summary>🔵 <b>Promises</b></summary>

<details>
<summary>🔴 <b>Mockup of what a Promise class would look like in Javascript</b></summary>

```js
class MockPromise {
  constructor(executor) {
    // Hidden internal slots (represented by [[SlotName]] in specifications)
    this._status = "pending";          // [[PromiseState]]
    this._result = undefined;          // [[PromiseResult]]
    this._fulfillReactions = [];       // [[PromiseFulfillReactions]]
    this._rejectReactions = [];        // [[PromiseRejectReactions]]

    // The internal resolve function handed to the executor
    const resolve = (value) => {
      if (this._status !== "pending") return; // Promises can only settle once

      // Promise Flattening: If a user returns a Promise, wait for it!
      if (value && typeof value.then === "function") {
        value.then(resolve, reject);
        return;
      }

      this._status = "fulfilled";
      this._result = value;
      this._queueMicrotasks(this._fulfillReactions);
    };

    // The internal reject function handed to the executor
    const reject = (reason) => {
      if (this._status !== "pending") return;

      this._status = "rejected";
      this._result = reason;
      this._queueMicrotasks(this._rejectReactions);
    };

    // Run the user's executor function immediately and synchronously
    try {
      executor(resolve, reject);
    } catch (err) {
      reject(err); // Auto-reject if the executor synchronously crashes
    }
  }

  // Helper method to simulate pushing callbacks to the V8 Microtask Queue
  _queueMicrotasks(reactionsList) {
    while (reactionsList.length > 0) {
      const nextReaction = reactionsList.shift();
      
      // queueMicrotask is a real native JS global utility!
      queueMicrotask(() => {
        nextReaction(this._result);
      });
    }
  }

  then(onFulfilled, onRejected) {
    // Rule: Every .then() call must return a brand-new Promise instantly
    return new MockPromise((nextResolve, nextReject) => {
      
      // 1. Create the wrapper handler for success
      const fulfilledReactionWrapper = (value) => {
        if (typeof onFulfilled !== "function") {
          // If no success handler was provided, pass the value down the chain
          nextResolve(value);
          return;
        }
        try {
          const callbackResult = onFulfilled(value);
          nextResolve(callbackResult); // This resolves the NEXT promise in the chain!
        } catch (err) {
          nextReject(err); // If the callback crashes, reject the NEXT promise
        }
      };

      // 2. Create the wrapper handler for failure
      const rejectedReactionWrapper = (reason) => {
        if (typeof onRejected !== "function") {
          // If no error handler was provided, cascade the rejection down the chain
          nextReject(reason);
          return;
        }
        try {
          const callbackResult = onRejected(reason);
          nextResolve(callbackResult); // If catch succeeds, recover and resolve next!
        } catch (err) {
          nextReject(err);
        }
      };

      // 3. Execution Phase: Are we checking a pending chain, or a pre-settled promise?
      if (this._status === "pending") {
        this._fulfillReactions.push(fulfilledReactionWrapper);
        this._rejectReactions.push(rejectedReactionWrapper);
      } else if (this._status === "fulfilled") {
        queueMicrotask(() => fulfilledReactionWrapper(this._result));
      } else if (this._status === "rejected") {
        queueMicrotask(() => rejectedReactionWrapper(this._result));
      }
    });
  }

  // .catch() is literally just syntactic sugar!
  catch(onRejected) {
    return this.then(null, onRejected);
  }
}
```

</details>


### 🟣 Why promises were made?
Callback hell. With promises, we no longer have to deal with passing ugly callback pyramids to our APIs. 

### 🟣 Difference between `.then` syntax and `async/await`
Every time a `.then` method is executed, it adds a new callback to the internal `[[PromiseFulfillReactions]]` list. `async/await`, on the other hand, optimizes your code via a generator. The generator doesn't append callbacks to the list; instead, it just passes a pointer to the spot in your async function that it needs to pick up at after the promise is fulfilled. 

### 🟣 Are most modern promise-based APIs in Node.js just wrappers for old-school callback-based APIs?
Yep.

### 🟣 In javascript method chaining, a variable is only assigned to the last returned thing in the chain
I was confused with .then chaining. I figured the first promise returned by something like fetch() gets assigned to your variable even if we use .then chaining. I then couldn't understand how the final promise return by the final .then got assigned to the variable. Now I know. (The header of this section is the answer!) So what happens to the other promises higher up in the chain? The are just floating anonymous promises in the heap. 

### 🟣 How do the .then callback(s) in the internal `[[PromiseFulfillReactions]]` list actually get executed? 
Libuv pushes (or literally has node.js have v8 to push it) your async API's callback onto the stack, which then executes its inner resolve function. Thanks to lexical scoping via The resolve function then switches the promise's status from 'pending' to 'fulfilled'. Another internal V8 operation then pushes the fulfillreactions (your .then callbacks) onto the native v8 microtask queue. They are put on right away after the current synchronous execution context on the stack finishes. They essentially cut in line ahead of the outer blink/libuv c++ macro task queue. 

### 🟣 The magic of await
I've realized that `await` does the job of .then AND it automatically unwraps and exposes the promises result to the variable that you assign to your await api.

</details>

---

<details>
<summary>🔵 <b>try/catch blocks</b></summary>

### 🟣 When to use them?
When your executed functions deal with outside factors that you have no control of. Examples include network requests, disk I/O operations, database 


</details>
