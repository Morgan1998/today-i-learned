<details>
  <summary><b>August 3, 2026 — summary</b></summary>
  <br>

  * React: Today I learned about React useState. Still processing the way it works, but it lead me to learning about how to do something similar with vanilla js via factory functions.
  * js: Learned about writing explicit methods that act as getters and setters vs using `get` and `set` attributes of accessor properties. It certainly is easier for my brain to read the explicit methods way, but I learned about a few key reasons developers sometimes use `get` and `set` attributes. I also learned about how a property must either be a data property or an accessor property. And each, depending on their type/descriptor, get 4 attributes. Both always get enumerable and configurable, but only data properties get the writable and value attributes, and only accessor properties get the set and get attributes. 
  * git: I've decided to stick to English commit messages only for the time being. I've started to feel a little bit of friction with my studies due to having to spend time on translating my commit messages. However, I will return to writing Japanese commit message translations when I'm over the hump with studying React and Node.js/Express every day. 


</details>

---

<details>
  <summary><b>July 18, 2026 — summary</b></summary>
  <br>

  * js: Learned about immutable data patterns. We assign an array to a variable via let. Instead of directly modifying the original array, we instead create a shallow copy of it with spread operator (or structured clone for deep nested object trees), and then change the reference of the variable to the copy and let the old array get garbage collected. 


</details>

---


<details>
  <summary><b>July 17, 2026 — Path Resolution, JS Compiler Internals, & Bundler Architecture</b></summary>
  <br>

  Today was a massive deep-dive day! Refined my understanding of Node pathing, explored V8 compiler performance optimizations (monomorphism), mapped out a refactor plan for "Kanji Wizard," and figured out what Docker actually does using a Node/npm analogy.

  * Node.js: Mastered `process.cwd()` vs. ES Modules Import Attributes for file reading.
  * Performance: Learned how the JS JIT compiler handles optimization/deoptimization loops, and why keeping object shapes identical (monomorphism) prevents costly bailouts.
  * DevOps: Created a strong mental model for Docker using `package.json` as an analogy.
  * Kanji Wizard: Planned a modular ES6 refactor utilizing `esbuild` to solve "single-file development" headaches.

</details>

---
