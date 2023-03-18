# Constants

folder to storage your guards to manage the security, protected routes, user roles, etc...

## File example

```ts
// auth-guard.ts

/* eslint-disable react/jsx-no-useless-fragment */
import React, { FC } from 'react';
import { useRouter } from 'next/router';

import { cookiesKeys, getToken } from '@helpers';
import { useUsersMe } from '@hooks';
import { useQueryClient } from '@tanstack/react-query';
import jsCookie from 'js-cookie';

import { UserKeys } from 'src/services/config/query-key-factory';

import { PageLoader } from '../atoms/PageLoader';

const ProtectedRoutes = ['/cotizacion-pendiente', '/cotizacion-realizada', '/cotizar'];

export const AuthLayout: FC<Props> = ({ children }) => {
  const router = useRouter();
  const queryClient = useQueryClient();
  const { data: user, isLoading } = useUsersMe();

  if (!ProtectedRoutes.includes(router.pathname)) return <>{children}</>;

  if (isLoading && !!getToken()) return <PageLoader />;

  if (!user) {
    if (typeof window === 'undefined') return <PageLoader />;

    queryClient.invalidateQueries({ queryKey: UserKeys.all });
    jsCookie.remove(cookiesKeys.token);
    jsCookie.set(cookiesKeys.redirectUrl, router.asPath);
    router.push('/sign-in');

    return <PageLoader />;
  }

  return <>{children}</>;
};


type Props = {
  children: JSX.Element | JSX.Element[];
};

```

## Structure example

```
|-- guards
    |-- auth-guard.ts
    |-- permissions-guard.ts
```