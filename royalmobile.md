# RoyalMobile
## Front-end Repositories
- React

## Back-end Repositories
- Go
- Python
- Java

## Api Response
```
ApiResponse<ResponseData> {
  status: String<'success' | 'error'>
  data: Object<ResponseData>
  message: String
}
```

## Api Routes
```
GET /api/products

Params {
  page: Number<increments of 1>
}

<!-- Success -->
returns ApiResponse
ApiResponse.status = 'success'
ApiResponse.data = Array<Product>
```

```
GET /api/product/{id}

Params {
  id: String
}

<!-- Success -->
returns ApiResponse
ApiResponse.status = 'succes'
ApiResponse.data = Product

<!-- Error -->
returns ApiResponse
ApiResponse.status = 'error'
ApiResponse.data = Null
ApiResponse.message = 'Product could not be found'
```

## Types
```
Product {
  id: Number
  manufacturer: String
  model: String
  modelId: String
  variants: Array<{
    id: Number
    variantId: String
    color: String
    colorHex: String
    capacity: String
    is_in_stock: Boolean
    is_preorder: Boolean
    regular_price: String
    discounted_price: String
    has_discounts: Boolean
  }>
}
```
