<details>
  <summary><b>Promises — July 17, 2026</b></summary>
  <br>

  ### Why promises were made?
  Callback hell. With promises, we no longer have to deal with passing ugly callback pyramids to our APIs. 

  ### Difference between `.then` syntax and `async/await`
  Every time a `.then` method is executed, it adds a new callback to the internal `[[PromiseFulfillReactions]]` list. `async/await`, on the other hand, optimizes your code via a generator. The generator doesn't append callbacks to the list; instead, it just passes a pointer to the spot in your async function that it needs to pick up at after the promise is fulfilled. 

  ### Are most modern promise-based APIs in Node.js just wrappers for old-school callback-based APIs?
  Yep.

</details>

---