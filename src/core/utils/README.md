# Types

folder to storage your utilities or also known as helpers, here is going to be the functions or class helpers for your project

## File example

```ts
// products-util.ts

export const getAddToCartButtonText = (isInStock: boolean, isAddingToCart: boolean) => {
  if (!isInStock) return 'Producto no disponible';
  if (isAddingToCart) return 'Agregando...';

  return 'Agregar al carrito';
};

```


## Structure example

```
|-- utils
    |-- products
        |-- index.ts
        |-- products-util.ts
    |-- common
        |-- index.ts
        |-- arrays-util.ts
        |-- errors-util.ts
```
