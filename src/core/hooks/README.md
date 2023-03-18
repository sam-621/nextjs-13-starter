# Hooks

folder to storage your utility hooks and petitions hooks 

## File example

- utility hook

```ts
// useToggle.ts

import { useState } from 'react';

export const useToggle = (initialValue = false) => {
  const [state, setState] = useState(initialValue);

  const toggle = () => {
    setState(!state);
  };

  return {
    state,
    toggle,
    setState
  };
};

```

- petition hook

```ts
// useActiveOrder.ts

/**
 * Implementation made with react-query but here you are going to have your useFetch generic hook
**/

import { useQuery } from '@tanstack/react-query';
import { GraphQLError } from 'graphql';

import { Order } from '@/interfaces/orders';
import { getOrder, OrdersKeys } from '@/services/orders';

type QueryFnData = Order | undefined;
type TError = GraphQLError;

export const useActiveOrder = () => {
  return {
    ...useQuery<QueryFnData, TError>(OrdersKeys.detail, getOrder)
  };
};

```


## Structure example

```
|-- hooks
    |-- orders
        |-- index.ts
        |-- useActiveOrder.ts
        |-- useAddToOrder.ts
    |-- common                  
        |-- index.ts
        |-- useToggle.ts
        |-- useElement.ts
```