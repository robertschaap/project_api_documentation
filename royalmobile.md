# RoyalMobile
## Front-end Repositories
- React

## Back-end Repositories
- Go
- Python

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
ApiResponse.data = Array<{
  id: number
  manufacturer: string
  model: string
  modelId: string
  variants: Array<{
    id: number
    variantId: string
    color: string
    colorHex: string
    capacity: string
    is_in_stock: boolean
    is_preorder: boolean
    regular_price: string
    discounted_price: string
    has_discounts: boolean
  }>
  specifications?: {}
}>

<!-- Error -->
returns ApiResponse
ApiResponse.status = 'error'
ApiResponse.message = 'Products could not be found'
```
