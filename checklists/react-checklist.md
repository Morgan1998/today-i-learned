# Core React Project Setup Checklist

## 1. Environment and Tooling

- [ ] Initialize the project using Vite with the TypeScript template.
- [ ] Enable strict type checking in tsconfig.json by setting `"strict": true`.
- [ ] Configure ESLint and Prettier for automated code linting and formatting.
- [ ] Create a `.env.example` file to document all required frontend environment variables.

## 2. Architecture and Routing

- [ ] Organize the `src/` directory using a clear feature-module layout.
- [ ] Initialize navigation using React Router Data APIs (`createBrowserRouter`).
- [ ] Implement Route Loaders to prefetch critical server state before components render.
- [ ] Handle frontend form submissions and data mutations via Route Actions.

## 3. Resilience and UX Essentials

- [ ] Design and implement explicit loading states or skeleton screens for asynchronous operations.
- [ ] Wrap route components in Error Boundaries to capture and handle API failures gracefully.
- [ ] Enforce strict TypeScript typing across all components, avoiding the use of `any`.

# Other Stuff To Consider

## State

Here's an overview of how to delegate the way you manage stage:
![Ways to Manage State](images/ways-to-manage-state.png)

Also try to use a mix of these:

1. Storage Providers (they create and hold state)
   useState: Best for simple, localized state (e.g., toggling a modal).
   useReducer: Best for complex local state with multiple moving parts or complex business logic.
2. The Delivery Mechanisms (Pass Data Only)
   These are not state containers. They are architectural patterns used to move data from point A to point B.
   Prop Drilling: Passing data explicitly down through every layer of the tree.
   Composition: Passing components as props (like children). This completely avoids drilling by letting you instantiate the child right where the state lives.
3. The Hybrid Systems (Store and Deliver Globally)
   These systems do both: they hold the data in a central place and provide a built-in mechanism to broadcast that data to any component, bypassing the intermediate tree.
   useContext: Built into React. It broadcasts a useState or useReducer value to an entire sub-tree.
   useOutletContext: Built into React Router. It acts exactly like useContext, but specifically delivers state from a parent route down to its child route layout.
   Zustand & Redux: External global stores. They hold state completely outside of the React component tree and use optimized subscription systems to deliver data directly to any component that asks for it.
4. Server State Managers. These handle data fetched from an API.
   TanStack Query (React Query)
   RTK Query: (this is kinda like the answer from Redux to the creation of TanStack Query, at least to my understanding haha. Here's another way to put it that I read: "RTK Query wraps server state cache logic directly into the Redux ecosystem to match TanStack's capabilities")
   Route Loaders: Best for data needed exactly when a route changes (Just-In-Time server state).

In case you forget, here's a reminder to how you can think about designing your state handling system:

> I break state down into local UI state, global UI state, and server state. For local state, I use useState or useReducer for complex logic. To pass that data, I prefer component composition to keep things clean, but I'll use prop drilling if it's only going down one or two levels. For global UI state like themes, I use Zustand, and for server state, I rely on TanStack Query or Route Loaders to handle caching and avoid redundant network requests.
