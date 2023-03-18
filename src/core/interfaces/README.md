# Interfaces

folder to storage your interfaces related to entities, concepts or utility interfaces form your application

## File example

```ts
// order-interfaces.ts

import { Customer } from '../customer';
import { CommonProduct, ProductVariantOption, StockLevel } from '../products';
import { ShippingAddress } from '../shipping';

export interface Order {
  id: string;
  code: string;
  state: OrderStates;
  couponCodes: string[];
  subTotal: number;
  total: number;
  totalQuantity: number;
  customer: Customer;
  shippingAddress: ShippingAddress;
  lines: OrderLine[];
}

export interface OrderLine {
  id: string;
  quantity: number;
  productVariant: OrderLineProduct;
}

export interface OrderLineProduct {
  id: string;
  product: Pick<CommonProduct, 'assets' | 'name' | 'customFields'>;
  price: number;
  stockLevel: StockLevel;
  options: ProductVariantOption[];
}

export enum OrderStates {
  CREATED = 'Created',
  DRAFT = 'Draft',
  ADDING_ITEMS = 'AddingItems',
  ARRANGING_PAYMENT = 'ArrangingPayment',
  PAYMENT_AUTHORIZED = 'PaymentAuthorized',
  PAYMENT_SETTLED = 'PaymentSettled',
  PARTIALLY_SHIPPED = 'PartiallyShipped',
  SHIPPED = 'Shipped',
  PARTIALLY_DELIVERED = 'PartiallyDelivered',
  DELIVERED = 'Delivered',
  MODIFYING = 'Modifying',
  ARRANGING_ADDITIONAL_PAYMENT = 'ArrangingAdditionalPayment',
  CANCELLED = 'Cancelled'
}

```


## Structure example

```
|-- interfaces
    |-- orders
        |-- index.ts
        |-- order-interfaces.ts
    |--common
       |-- index.ts
       |-- utils-interfaces.ts
       |-- http-interfaces.ts
```