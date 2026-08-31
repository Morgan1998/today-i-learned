<details>
<summary>🔵 <b>useState hook!</b></summary>

In vanilla js, we need to write out dedicated controllers for each state variable (color, toggles, etc.) of our elements, either as a class or a factory function. However, we can use useState, a hook, to handle them all in one place. The state variables are stored in a linked list of hook objects that is assigned to the component where the state variables were defined. The hook object contains the value (via its memoizedState property) for the state variable. So how does React know which hook object is for which state variable that we defined in the component? Well, each hook object is assigned an index based on the order you defined each state variable via useState in your component. Because React uses this initial order to know exactly which state variable matches to which hook object, we cannot use conditional blocks or loops to execute hooks to set up state variables.

</details>

---

<details>
<summary>🔵 <b>useEffect</b></summary>

For keeping our component in sync with stuff outside of our application and dealing with side effects.

- For your separate front-end/back-end projects, using route loaders is a lot better than using useEffect for fetching data
- From what I've read, useEffect isn't the best option for most stuff these days. Only use it for specific cases where you're bridging React state to an outside browser system AND you've verified that useEffect is appropriate.
- Make sure to include a cleanup function if your callback uses any of these: `addEventListener`, `setInterval`, `fetch()`, and Opening a WebSocket. There may be more that I'm not aware of, so always check if you need one when writing a useEffect hook.

</details>

---

<details>
<summary>🔵 <b>useReducer</b></summary>

Pretty much does the same thing as useState but better ergonomics for the developer for when you have lots of stuff going on. I'll write in more detail about this later once I actually get some hands on practice with useReducer.

</details>

---

<details>
<summary>🔵 <b>useMemo</b></summary>

Caches the result of the callback you pass to it. It's for only running an expensive calculation over again when something in your dependency array changes. Otherwise, you don't have to rerun that calculation over and over again every time your component rerenders.

</details>

---

<details>
<summary>🔵 <b>memo</b></summary>

You wrap you component in it. This allows your component to NOT rerender even if the parent rerenders (which by default results in children rerendering). Of course, the props of the component also must not change in order to skip the rerender. That's where useMemo and useCallback come in handy, because of that fact that objects get remade in memory every rerender (primitives don't apply to this), they'll always be flagged as changed, which triggers a rerender. But when we memoize them with useMemo or useCallback, we're good to good!

</details>

---

<details>
<summary>🔵 <b>useCallback</b></summary>

Pretty much the same as useMemo except instead of storing the result of the callback, the callback itself is what's memoized.

</details>

---

<details>
<summary>🔵 <b>useContext</b></summary>

One of the ways to pass data to child components without prop drilling. You create the context (which is like a special component), wrap a parent component in the context component, declare what value you want to pass via the value prop of that component, and then go use it in a child by calling the useContext hook with the context component you defined earlier as the argument.

</details>

---
