# Wrappers

folder to storage your wrappers or also known as HOC

## File example

```tsx
// app-config-wrapper.ts

import { FC, PropsWithChildren } from 'react';

import { QueryClientProvider } from '@tanstack/react-query';
import { Provider } from 'react-redux';

import { ModalProvider } from '@/contexts';
import { queryClient } from '@/libs/react-query';
import { store } from '@/store/root-state';

export const AppConfigWrapper: FC<PropsWithChildren> = ({ children }) => {
  return (
    <Provider store={store}>
      <ModalProvider>
        <QueryClientProvider client={queryClient}>{children}</QueryClientProvider>
      </ModalProvider>
    </Provider>
  );
};


```


## Structure example

```
|-- wrappers
    |-- app-config-wrapper.td
    |-- ui-wrapper.ts
    |-- hoc-wrapper.ts
```
