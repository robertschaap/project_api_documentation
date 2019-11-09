# BulletinBoard v2
## Front-end Repositories
- React

## Back-end Repositories
- Python
- Go
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

ResponseData {
  comments: Array<{
    id: String
    name: String
    title: String
    body: String
  }>
}
```
```
POST /api/comments

Body {
  name: String
  title: String
  body: String
}
```
