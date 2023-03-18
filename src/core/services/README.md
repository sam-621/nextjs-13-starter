# Services

folder to storage your services which are the intermediary between your api and your frontend application, here your are going to add the logic of the request and also the library to make them

## File example

```ts
// order-service.ts

import { ACTIVE_ORDER_QUERY } from '@/gql/orders';
import { Query } from '@/interfaces/gql';
import { Order } from '@/interfaces/orders';
import { gqlRequest } from '@/libs/graphql-request';

type ActiveOrderQuery = Pick<Query<Order>, 'activeOrder'>;

export const getOrder = async (): Promise<Order | undefined> => {
  const { activeOrder } = await gqlRequest<ActiveOrderQuery>({
    query: ACTIVE_ORDER_QUERY
  });

  return activeOrder;
};

```


## Structure example

```
|-- services
    |-- orders
        |-- index.ts
        |-- order-service.ts
        |-- query-keys.ts
    |-- customer
        |-- index.ts
        |-- customer-service.ts
        |-- query-keys.ts
```