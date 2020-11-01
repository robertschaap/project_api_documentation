# RoyalMobile
## Front-end Repositories
- React

## Back-end Repositories
- Go
- Python
- Java

## API Response
API responses that are handled properly (i.e. do not result in 4xx, 5xx, etc responses) are of the type/shape `ApiResponse`. Depending on the implementation this may have more specific types. Regardless there are two key responses:

* `success`: status is `success`, data is set, message is `null`
* `error`: status is `error`, data is null, message is set

```typescript
type ApiResponse<ResponseData> = {
  status: 'success' | 'error';
  data: ResponseData | null;
  message: null | string;
};

```

Responses are expected to be served from `:4000/api/`

## API Routes
### `GET /api/cart/{id}`
```typescript
type Params = {
  id: string // UUIDv4 or 'new-cart'
};

type SuccessReponse = ApiResponse<{
  status: 'success';
  data:  Cart;
  message: null;
}>;

type ErrorResponse = ApiResponse<{
  status: 'error';
  data: null;
  message: 'Could not get cart'
}>;
```

### `GET /api/product/{id}`
```typescript
type Params = {
  id: String;
};

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: Product;
  message: null;
}>;

type ErrorResponse = ApiResponse<{
  status: 'error';
  data: null;
  message: 'Could not get product';
}>;

```

### `GET /api/products`
A successful response returns `Array<Product>`. In case no products are found, it returns an empty `Array`. There is no specific error handling.

```typescript
type QueryParams = {
  page: number; // increments of 1
};

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: Array<Product>;
  message: null;
}>;

```

### `GET /api/subscriptions`
A successful response returns `Array<Subscription>`. In case no subscriptions are found, it returns an empty `Array`. There is no specific error handling.

```typescript
type SuccessResponse = ApiResponse<{
  status: 'success';
  data: Array<Subscription>;
  message: null;
}>;

```

## Types
### Cart, CartItem
A cart contains `Array<CartItem>` of 0 or more `CartItem`s. The `id` field of the cart should be formatted as a v4 UUID type, with exception of the `new-cart` which is only used for easy debugging.

A `CartItem` has to contain both a `Product` and a `Subscription`. The `Product` is reduced to only having a single `ProductVariant` in it's `variants` attribute.
```typescript
type Cart = {
  id: string; // UUIDv4 or 'new-cart'
  items: Array<CartItem>;
  totals: {
    monthly_price: string;
    onetime_price: string;
  };
};

type CartItem = {
  id: string; // UUIDv4
  product: Product; // only pass relevant ProductVariant
  subscription: Subscription;
  totals: {
    monthly_price: string;
    onetime_price: string;
  };
};
```

### Product, ProductVariant
A `Product` must include at least 1 `ProductVariant`. The variant has a `variantId` which is built up from the `manufacturer` and `model` attributes from which appear in the `Product`, and the `color` and `capacity` attributes from the `ProductVariant` itself.

```typescript
type Product = {
  id: number;
  manufacturer: string;
  model: string;
  modelId: string; // manufacturer-model
  variants: Array<ProductVariant>; // at least 1
};

type ProductVariant = {
  id: number;
  variantId: string; // manufacturer-model-xxgb-colorname
  color: string; // colorname
  colorHex: string;
  capacity: string; // xxgb
  is_in_stock: boolean;
  is_preorder: boolean;
  regular_price: string;
  discounted_price: string;
  has_discounts: boolean;
};

```

### Subscription
A `Subscription` has a `subscriptionId` which is built up from the `data` and `durationId` attributes, prefixed with the name of the project; `royalmobile`.

```typescript
type Subscription = {
  id: number;
  subscriptionId: string; // royalmobile-xxgb-xduration
  durationId: string; // xduration
  data: string; // xxgb
  benefits_long: Array<string>;
  benefits_short: string;
  regular_price: string;
};

```
