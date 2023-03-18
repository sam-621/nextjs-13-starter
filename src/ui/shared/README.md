# Modules

Folder to storage your jsx and React components which are used in more than 1 module or which not are related to any entity or concept

## File example

```tsx
// SimpleReactComponent.tsx

export const SimpleReactComponent = () => {
  return <h1>SimpleReactComponent</h1>
}

```

## Structure example

```
|-- shared
    |-- carousel
        |-- index.ts
        |-- Carousel.tsx
        |-- ProductsCarousel.tsx
        |-- Slider.tsx
    |-- products
        |-- index.ts
        |-- ProductCard.tsx
        |-- ProductsList.tsx
    |-- ui
        |-- index.ts
        |-- button
            |-- ...
        |-- input
            |-- ...
```