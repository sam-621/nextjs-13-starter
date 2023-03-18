# Constants

folder to storage your constants like env variables, dates, some business constants and more

## File example

```ts
// env.ts

export const BASE_API_URL = process.env.NEXT_PUBLIC_BASE_API_URL || 'http://localhost:5000/api'

```

## Structure example

```
|-- constants
    |-- env.ts
    |-- states.ts
    |-- storage.ts
```