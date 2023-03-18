# Libs

folder to storage your code related to your libraries to avoid leaving crumbs of the library in your project and keep that code in one place in case you want to change the library in the future

## File example

```ts
// graphql-request.ts

import { GraphQLClient, Variables } from 'graphql-request';

import { API_URL } from '@/constants/env';

const client = new GraphQLClient(API_URL, {
  credentials: 'include',
});

export const gqlRequest: GqlRequest = ({ query, variables }) => {
  return client.request(query, variables);
};

type GqlRequest = <R, V = Variables>(input: GqlRequestInput<V>) => Promise<R>;

type GqlRequestInput<V> = {
  query: string;
  variables?: V;
};

```


## Structure example

```
|-- libs
    |-- graphql-request
        |-- index.ts
        |-- graphql-request.ts
    |-- react-query
        |-- index.ts
        |-- react-query.ts
```