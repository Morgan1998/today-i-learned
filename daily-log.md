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