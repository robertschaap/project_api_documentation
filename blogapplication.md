# Blog
## Front-end Repositories
- React
- Vue

## Back-end Repositories
- Node & Mongo
- Go

## Full Stack Repositories
- Node & Pug

TODO: write out responses

## API Response
```typescript
type ApiResponse<ResponseData> = {
  status: 'success' | 'error';
  data: Object<ResponseData>;
  message: string;
}

```

## API Routes
### `POST /api/comments/new`
```typescript
type Params = {
  body: string;
  userId: string;
  postId: string;
}

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: {
    comment: {
      body: string;
      userId: string;
      postId: string;
    };
  };
}>;

```

### `GET /api/posts/`
```typescript
type ApiResponse = ApiResponse<{
  status: 'success';
  data: {
    posts: Array<{
      title: string;
      body: string;
      category: string;
      userId: string;
      author: string;
    }>;
  };
}>;

```

### `GET /api/posts/{category}`
```typescript
type Params = {
  category: string;
}

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: {
    posts: Array<{
      title: string;
      body: string;
      category: string;
      userId: string;
      author: string;
    }>;
  };
}>;

```

### `GET /api/posts/{id}`
```typescript
type Params =  {
  id: string;
}

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: {
    posts: Array<{
      postAuthor: string;
      postBody: {
        title: string;
        body: string;
        category: string;
        userId: string;
      };
      comments: Array<{
        body: string;
        userId: string;
        postId: string;
        author: string;
      }>;
    }>
  };
}>;

```

### `POST /api/posts/new`
```typescript
type Params = {
  title: string;
  body: string;
  category: string;
  userId: string;
}

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: {
    post: {
      title: string;
      body: string;
      category: string;
      userId: string;
    };
  };
}>;

```

### `POST /users/new`
```typescript
type Params = {
  firstName: string;
  lastName: string;
  email: string;
  userName: string;
  bio: string;
  password: string;
};

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: {
    user: {
      firstName: string;
      lastName: string;
      email: string;
      userName: string;
      bio: string;
      password: string;
    };
  };
}>;

```

### `POST /users/login`
```typescript
type Params = {
  userName: string;
  password: string;
};

type SuccessResponse = ApiResponse<{
  status: 'success';
  data: {
    user: {
      id: string;
      firstName: string;
      lastName: string;
    };
    token: string;
  };
}>;

type ErrorResponse = ApiResponse<{
  status: 'error';
  message: 'access denied';
}>;

```

TODO: check `users/new` for return of password or clarify here
