# BulletinBoard v2
## Front-end Repositories
- React
- Svelte

## Back-end Repositories
- Python
- Rust
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
GET /api/comments

Params {
  offset: Number<increments of 4>
  sort: String<'asc' | 'desc'>
}

<!-- Success -->
returns ApiResponse
ApiResponse.status: 'success'
ApiResponse.data {
  comments: Array<{
    id: String
    name: String
    title: String
    body: String
  }>
}

<!-- Error -->
returns ApiResponse
ApiResponse.status: 'error'
```
```
POST /api/comments

Body {
  name: String
  title: String
  body: String
}

<!-- Success -->
returns ApiResponse
ApiResponse.status: 'success'

<!-- Error -->
returns ApiResponse
ApiResponse.status: 'error'

```
