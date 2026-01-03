# AWS Amplify React+Vite Starter Template

[Link on to do](https://docs.amplify.aws/vue/start/quickstart/)

This repository provides a starter template for creating applications using React+Vite and AWS Amplify, emphasizing easy setup for authentication, API, and database capabilities.

## Overview

This template equips you with a foundational React application integrated with AWS Amplify, streamlined for scalability and performance. It is ideal for developers looking to jumpstart their project with pre-configured AWS services like Cognito, AppSync, and DynamoDB.

## Features

- **Authentication**: Setup with Amazon Cognito for secure user authentication.
- **API**: Ready-to-use GraphQL endpoint with AWS AppSync.
- **Database**: Real-time database powered by Amazon DynamoDB.

## Deploying to AWS

For detailed instructions on deploying your application, refer to the [deployment section](https://docs.amplify.aws/react/start/quickstart/#deploy-a-fullstack-app-to-aws) of our documentation.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

### Create a login and authorization

In the file: src/main.tsx, wrap auth around the app

```tsx


  <React.StrictMode>
    <Authenticator>
      <App />
    </Authenticator>
  </React.StrictMode>
);

```

### How to make the data per login user

In the file: amplify/data/resource.ts

```ts
const schema = a.schema({
  Todo: a
    .model({
      content: a.string(),
    })
    .authorization((allow) => [allow.owner()]),
});

export type Schema = ClientSchema<typeof schema>;

export const data = defineData({
  schema,
  authorizationModes: {

    // This tells the data client in your app (generateClient())
    // to sign API requests with the user authentication token.
    defaultAuthorizationMode: 'userPool',
    },
});
```


## License

This library is licensed under the MIT-0 License. See the LICENSE file.