## Reproducing the bug

- Run `yarn` and `yarn dev`
- Navigate to `http://localhost:4000/tasks`

## Expected behaviour

The tasks list view will finish loading as soon as the graphql request for tasks returns.

## Actual behaviour

The task list never finishes loading, as useQuery never returns data and is perpetually in a loading state.

## Reason

`@keystone-next@23.0.2` internally depends on `@apollo/client@^3.4.0`.
Pinning the apollo client version to `3.3.21` and running through the reproduction steps results in the expected behaviour.

```json
"resolutions": {
    "@apollo/client": "3.3.21"
}
```
