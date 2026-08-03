<details>
<summary>🔵 <b>hooks</b></summary>

### 🟣 What are they?
In vanilla js, we need to write out dedicated controllers for each state variable (color, toggles, etc.) of our elements, either as a class or a factory function. However, we can use useState, a hook, to handle them all in one place. The state variables are stored in a linked list of hook objects that is assigned to the component where the state variables were defined. The hook object contains the value (via its memoizedState property) for the state variable. So how does React know which hook object is for which state variable that we defined in the component? Well, each hook object is assigned an index based on the order you defined each state variable via useState in your component. Because React uses this initial order to know exactly which state variable matches to which hook object, we cannot use conditional blocks or loops to execute hooks to set up state variables. 

</details>

---