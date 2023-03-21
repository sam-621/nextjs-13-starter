# Next.js starter

A modern [Next.js](https://nextjs.org/) starter fully configured with a solution for Tailwind, ESLint, Prettier, file structure, paths aliases, and more


## Getting started

- Install all dependencies

```bash
yarn
# or
npm i
# or
pnpm install
```
- Run the development server:

```bash
yarn dev
# or
npm run dev
# or
pnpm dev
```
You can start editing the page by modifying `pages/index.tsx`. The page auto-updates as you edit the file.

## Features

- Support for common development tools like ESLint, prettier, typescript, and husky
- Tailwind integrated
- Solution for file structure
- Path aliases

## General explanation

This file structure pretends to separate the logic of the application and the markup and styles, to let us modify the logic without affecting the markup and styling and also modify the markup and styling without affecting the logic of the application.

Is designed to maintain medium and large frontend applications thanks to modularization by concepts and entities which allows us to have both the business logic, the internal logic of the application, and the markup organized by entities or concepts of our system making easier the files searching, naming, and system understanding.

There are 3 main folders

- core: has all the business an application logic
- pages: Next.js page folder
- ui: All the markup, jsx, and styling of the application

## Deep explanation

This folder structure is based on **concepts or entities**, for example, you only going to have 1 hooks folder, but in there is going to be a customer folder that is going to store all hooks related to the customer entity o concept and this is going to happen in all other folders.

An entity or concept makes reference to an entity of a system or in a class diagram, some examples could be: Customer, Order, Collections, Payments, Carriers, Shipments and more or less depending on your business logic.

- Common folder

Sometimes you have code that is not related to any entity or concept, this is where the **common folder** comes in, in the common folder you are going to have all the code which is not related to any entity or concept, for example in the hooks folder if you have a hook which makes the logic for a toggle, you are going to put in in the common folder because the toggle logic is not related to any entity or concept

- Path aliases and index file

Path aliases are designed to work with **index.ts file** in these files you are going to export all components from your entity or concept

```ts
// index.ts

export * from './useActiveOrder'
export * from './useAdjustOrder'
export * from './useAddToOrder'
```

We recommend adding the index file by the concept and not in the root folder, for example, if you have a folder with only 2 files, here is not needed to have an index file because there are only 2 files and the imports paths will be @/constants instead of being @/constants/env which is more readable and understandable.

But if you have a folder that has these entities folder like order, customer o shipping, we recommend using the index file in each entity folder for the paths to be @/hooks/order instead of being @/hooks

Here is a visual example of what we explained above

*No index file needed*

```
|-- constants
    |-- env.ts
    |-- states.ts
    |-- storage.ts
```

*Index file needed*

```
|-- hooks
    |-- orders
        |-- index.ts
        |-- useActiveOrder.ts
        |-- useAddToOrder.ts
    |-- customer
        |-- index.ts
        |-- useSetCustomer.ts
        |-- useUpdateCustomer
    |-- common                  
        |-- index.ts
        |-- useToggle.ts
        |-- useElement.ts
```
