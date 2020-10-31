# RoyalMobile
## Front-end Repositories
- React

## Back-end Repositories
- Go
- Python
- Java

## Api Response
```typescript
type ApiResponse<ResponseData> = {
  status: 'success' | 'error';
  data: ResponseData;
  message: string | null;
};

```

## Api Routes
### `GET /api/cart/{id}`
```typescript
type Params = {
  id: string // UUIDv4 or new-cart for the dummy cart
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
```typescript
type SuccessResponse = ApiResponse<{
  status: 'success';
  data: Array<Subscription>;
  message: null;
}>;

```

## Types
### Cart, CartItem
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

### Product
```typescript
type Product = {
  id: number;
  manufacturer: string;
  model: string;
  modelId: string; // manufacturer-model
  variants: Array<ProductVariant>;
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
