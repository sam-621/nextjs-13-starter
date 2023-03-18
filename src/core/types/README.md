# Types

folder to storage your type declarations, if you have to extend some library type or add to it, here is the place

## File example

```ts
// env.d.ts

declare namespace NodeJS {
  export interface ProcessEnv {
    NEXT_PUBLIC_API_DOMAIN: string;
  }
}

```


## Structure example

```
|-- types
    |-- env.d.td
    |-- library.d.ts
```