<details>
  <summary><b>Promises</b></summary>
  <br>

  ### Why promises were made?
  Callback hell. With promises, we no longer have to deal with passing ugly callback pyramids to our APIs. 

  ### Different between .then syntax and async/await
  Every time a .then method is executed, it adds as new callback to the internal `[[PromiseFulfillReactions]]` list. Async/await, on the otherhand, optimizes your code via a generator. The generator doesn't append callbacks to the list, instead it just passes a pointer to the spot in your async function that it needs to pick up at after the promise is fulfilled. 

  ### Are most modern promise-based APIs in node.js just wrappers for old school callback-based APIs?
  Yep

</details>

---