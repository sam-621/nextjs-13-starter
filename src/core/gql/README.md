# Gql

folder to storage your queries and mutations from your graphql server

## File example

```ts
// order-queries.ts

import {gql} from 'graphql-request';

import { COMMON_ACTIVE_ORDER } from './order-fragments';

export const ACTIVE_ORDER_QUERY = gql`
  ${COMMON_ACTIVE_ORDER}

  query ActiveOrder {
    activeOrder {
      ...CommonActiveOrder
    }
  }
`;

```


## Structure example

```
|-- gql
    |-- orders
        |-- index.ts
        |-- order-queries.ts
        |-- order-mutations.ts
        |-- order-fragments.ts
```