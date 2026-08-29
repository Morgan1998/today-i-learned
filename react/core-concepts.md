# Core Concepts of Good ol' React

## 3 primary triggers that cause re-rerenders (Internal to the Component)

1. `State changes` like a local useState setter function or a useReducer dispatch function
2. `Context changes`. So, this is like when a value that your component is 'subscribed' to changes. For example,
   when your component consumes from hooks like useLoaderData() and useParams()
3. `Props change`. Simple. It's just when your parent passes down new data as props to your component.

But don't forget the **cascade rule**! Haha. If a parent re-renders (via one of the above triggers), then by default all of it's children will re-render as well, unless you use a combo of `useMemo/useCallback` on non-primitive props (so objects, arrays, functions) and using `React.memo` (or I suppose the modern way to write it is just `memo()`) directly on the child component.
