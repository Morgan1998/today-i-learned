# State Management in good ol' React

## The 4 main aspects of managing state

1. Storage Providers (they create and hold state)
   `useState`: Best for simple, localized state (e.g., toggling a modal).
   `useReducer`: Best for complex local state with multiple moving parts or complex business logic.
2. The Delivery Mechanisms (Pass Data Only)
   These are not state containers. They are architectural patterns used to move data from point A to point B.
   **Prop Drilling**: Passing data explicitly down through every layer of the tree.
   **Composition**: Passing components as props (like children). This completely avoids drilling by letting you instantiate the child right where the state lives.
3. The Hybrid Systems (Store and Deliver Globally)
   These systems do both: they hold the data in a central place and provide a built-in mechanism to broadcast that data to any component, bypassing the intermediate tree.
   `useContext`: Built into React. It broadcasts a useState or useReducer value to an entire sub-tree.
   `useOutletContext`: Built into React Router. It acts exactly like useContext, but specifically delivers state from a parent route down to its child route layout.
   **Zustand & Redux**: External global stores. They hold state completely outside of the React component tree and use optimized subscription systems to deliver data directly to any component that asks for it.
4. Server State Managers. These handle data fetched from an API.
   **TanStack Query (React Query)**
   **RTK Query**: (this is kinda like the answer from Redux to the creation of TanStack Query, at least to my understanding haha. Here's another way to put it that I read: "RTK Query wraps server state cache logic directly into the Redux ecosystem to match TanStack's capabilities")
   Route Loaders: Best for data needed exactly when a route changes (Just-In-Time server state).
