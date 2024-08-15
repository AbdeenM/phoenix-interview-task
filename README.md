# Task 6

You are building a simple apollo graphql server that exposes a single query `getUser` and a mutation `updateUser` as well as setting up a background service that on an interval of 1 minute updates a field from the `user` object to a scheduled value for `message` that is prefixed by `automated -`
Initially upon the server running make a single request to `https://random-data-api.com/api/v2/users` to retrieve the user object and store the user details in memory database for later usage, note that we are not interested in all the data provided by the API end-point thus store only the properties that are needed by your `user` object
```typescript
// The user object
interface User {
  id: number
  uid: string
  first_name: string
  last_name: string
  username: string
  email: string
  message: string
}
```

## Notes

1. You can use any packages to achieve the task as long as you comment your reasoning behind it
2. The server you are building should be scalable and adheres with latest best practices
3. The mutation `updateUser` should only accept a `string` value, anything else should throw an error

## Requirements

1. Use TypeScript to build the server application
2. Set up a background service that runs every 1 min and updates the `user` object that is stored in memory property `message` to a value of `automated - [DateNow]`
3. When calling the `getUser` query you should be able to retrieve the current `user` details in memory
4. When calling the `updateUser` mutation you should be able to update the `message` property of the current `user` details in memory with a value of `manual - [Message]` were the `[Message]` is whatever the value sent by the mutation
5. Implement error handling to gracefully handle any issues that may arise

## Examples

1. When calling the `getUser` query and requesting all the user object properties a response similar to the one below should be retrieved:
   ```json
    {
      "id": 3108,
      "uid": "c60f4629-14e8-4bcf-bfc8-00e92222ddb2",
      "first_name": "Chauncey",
      "last_name": "Mann",
      "username": "chauncey.mann",
      "email": "chauncey.mann@email.com",
      "message": "[some-message]"
    }
    ```
2. When calling the `updateUser` mutation with a given message such that `message: "Hello world!"` the user object in the servers memory database should update the `message` property with a value of `manual - Hello world!`
3. Whenever a minute passes your background service should update the `user` object `message` property with a value of `automated - [DateNow]` where `[DateNow]` is the current time in UTC format

## Assessment Criteria

1. Code quality and maintainability
2. Understanding of TypeScript, Node.js, Background services and Apollo GraphQL
3. Integration skills with third-party APIs
4. Error handling and unit testing
5. Understanding of schedule-based tasks and implementation
