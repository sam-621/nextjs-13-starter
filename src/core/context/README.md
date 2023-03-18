# Contexts

folder to storage your React contexts

## File example

```tsx
//modal-context.tsx

import { createContext, FC, ReactNode, useCallback, useContext, useMemo, useState } from 'react';

export enum Modals {
  CART_TOOLTIP,
  NONE
}

interface ModalContextSchema<T = null> {
  isOpen: Modals;
  data: T | null;
  closeModal: () => void;
  openModal: (modal: Modals, data?: T) => void;
  toggleModal: (modal: Modals) => void;
}

const ModalContext = createContext<ModalContextSchema>({
  isOpen: Modals.NONE,
  data: null,
  closeModal: () => null,
  openModal: () => null,
  toggleModal: () => null
});

export const ModalProvider: FC<Props> = ({ children }) => {
  const [state, setState] = useState<Modals>(Modals.NONE);
  const [data, setData] = useState<ModalContextSchema['data']>(null);

  const closeModal = useCallback(() => {
    setState(Modals.NONE);
    setData(null);
  }, []);

  const openModal = useCallback((modal: Modals, modalData?: ModalContextSchema['data']) => {
    setState(modal);
    setData(modalData || null);
  }, []);

  const toggleModal = useCallback(
    (modal: Modals) => setState(state === Modals.NONE ? modal : Modals.NONE),
    // eslint-disable-next-line react-hooks/exhaustive-deps
    []
  );

  const contextValues = useMemo(
    () => ({
      isOpen: state,
      data,
      closeModal,
      openModal,
      toggleModal
    }),
    [state, data, closeModal, openModal, toggleModal]
  );

  return <ModalContext.Provider value={contextValues}>{children}</ModalContext.Provider>;
};

type Props = {
  children: ReactNode;
};

export function useModalContext<T>() {
  return useContext(ModalContext) as ModalContextSchema<T | null>;
}

```

## Structure example

```
|-- context
    |-- modal-context.ts
    |-- products-context.ts
    |-- page-context.ts
```