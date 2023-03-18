# Modules

folder to storage your jsx about one page

## File example

```tsx
// HomeView.tsx

export const HomeView = () => {
  return <h1>Home View</h1>
}

```

## Structure example

```
|-- modules
    |-- home
        |-- components      # Components which are only used in this module
        |-- HomeView.ts
        |-- index.ts
    |-- checkout
        |-- components      # Components which are only used in this module
        |-- CheckoutView.ts
        |-- index.ts
```