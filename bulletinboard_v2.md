# BulletinBoard v2
## Front-end Repositories
- React
- Svelte

## Back-end Repositories
- Python
- Rust
- Java
- Nest

## API Response
```typescript
type ApiResponse<ResponseData> {
  status: 'success' | 'error';
  data: Object<ResponseData> | null;
  message: null | string;
};

```

## API Routes
### `GET /api/comments`

```typescript
type QueryParams = {
  offset: number; // increments of 4
  sort: 'asc' | 'desc';
}

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: {
    comments: Array<{
      id: string;
      name: string;
      title: string;
      body: string;
    }>
  };
  message: null;
}>;

type ErrorResponse = ApiResponse<{
  status: 'error';
  data: null;
  message: '';
}>;

```

### `POST /api/comments`

```typescript
type Params = {
  name: string;
  title: string;
  body: string;
}

type SuccessRespone = ApiResponse<{
  status: 'success';
  data: null;
  message: null;
}>;

type ErrorResponse = ApiResponse<{
  status: 'error';
  data: null;
  message: '';
}>;

```
