# BulletinBoard v1
## Front-end Repositories
- React
- Vue

## Back-end Repositories
- Node & Mongo
- Go

## Full Stack Repositories
- Next
- Node & Pug

## API Routes
### `GET /api/comment`
```typescript
type QueryParams = {
  offset: number; // increments of 4
  sort: 'asc' | 'desc';
};

type SuccessResponse = Array<Comment>;

type ErrorResponse = Array<>;

```

### `POST /api/comment/new`
```typescript
type Params = {
  name: string;
  title: string;
  body: string;
  avatar: string;
};

type SuccessResponse = null;

type ErrorResponse = null;
```

## Types
### Comment
```typescript
type Comment = {
  name: string;
  title: string;
  body: string;
  avatar: string;
};

```
