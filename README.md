# Next.js starter

A [Next.js](https://nextjs.org/) starter fully configured with solution for tailwind, eslint, prettier, file structure paths aliases and more

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

- Support for common development tools like eslint, prettier, typescript and husky
- Tailwind integrated
- Solution for file structure
- Path aliases

## General explanation

This file structure pretends to separate the logic of the application and the markup and styles, this to let us modify the logic without affect the markup and styling and also modify the markup and styling without affect the logic of the application.

Is designed to maintain medium and large frontend applications thanks to modularization by concepts and entities which allows us to have both the business logic, internal logic of the application and the markup organized by entities or concepts of our system making easy the search of files, naming and system understanding.

There are 3 main folders

- core: has all the business an application logic
- pages: Next.js page folder
- ui: All the markup, jsx and styling of the application

## Deep explanation

This folder structure is based on **concepts or entities**, for example you only going to have 1 hooks folder, but in there is going to be a customer folder which is going to store all hooks related to customer entity o concept and this is going to happen in all other folder.

An entity or concept make reference to an entity of a system or in a class diagram, some examples could be: Customer, Order, Collections, Payments, Carriers, Shipments and more or less depending on your business logic.

- Common folder

Sometime you have code which is not related to any entity or concept, this is where the **common folder** comes in, in the common folder you are going to have all the code which is not related to any entity or concept, for example in the hooks folder if you have a hook which make the logic for a toggle, you are going to put in in the common folder because the toggle logic is not related to any entity or concept

- Path aliases and index file

Path aliases are designed to work with **index.ts file** in these files you are going to export all components from your entity or concept

```ts
// index.ts

export * from './useActiveOrder'
export * from './useAdjustOrder'
export * from './useAddToOrder'
```

we recommend add the index file by concept and not in de root folder, for example, you have a folder with only 2 files, here is not needed to have an index file because theres is only 2 files and the imports paths will be @/constants instead of being @/constants/env which is more readable and understandable.

But if you have a folder which has these entities folder like order, customer o shipping, we recommend use the index file in each entity folder for the paths to be @/hooks/order instead of being @/hooks

Here is a visual example about what we explained above

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