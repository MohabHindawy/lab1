# Lab 1

The backend `getTodos` controller now reads the optional `done` query parameter from `req.query` and builds a MongoDB filter from it.

The API supports:

- `GET /api/todos` – returns all todos
- `GET /api/todos?done=false` – returns active todos
- `GET /api/todos?done=true` – returns completed todos

If no `done` parameter is provided, the filter stays empty and the original behavior of returning all todos is preserved.

On the frontend, `fetchTodos` now accepts a filter and sends the appropriate query parameter using Axios. `App.jsx` stores the current filter as `all`, `active`, or `done`, and the `useEffect` fetches the todos again whenever this filter changes.

Three buttons were added for **All**, **Active**, and **Done**, allowing the user to change the current filter.

The filtering is done on the server rather than filtering the already-loaded React array. This requires a new request whenever the filter changes, but means the server only returns the todos that are actually needed.
