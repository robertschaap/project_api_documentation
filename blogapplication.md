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
POST /api/comments/new

Body {
  body: String
  userId: String
  postId: String
}

<!-- Success -->
returns ApiResponse

ApiResponse.status: 'success'
ApiResponse.data {
  comment: {
    body: String
    userId: String
    postId: String
  }
}
```
```
GET /api/posts/
<!-- Success -->
returns ApiResponse

ApiResponse.status: 'success'
ApiResonse.data {
  posts: Array<{
    title: String
    body: String
    category: String
    userId: String
    author: String
  }>
}
```
```
GET /api/posts/{category}

Params {
  category: String
}

<!-- Success -->
returns ApiResponse

ApiResponse.status: 'success'
ApiResonse.data {
  posts: Array<{
    title: String
    body: String
    category: String
    userId: String
    author: String
  }>
}
```
```
GET /api/posts/{id}

Params {
  id: String
}

<!-- Success -->
returns ApiResponse

ApiResponse.status: 'success'
ApiResonse.data {
  posts: Array<{
    postAuthor: String
    postBody: {
      title: String
      body: String
      category: String
      userId: String
    }
    comments: Array<{
      body: String
      userId: String
      postId: String
      author: String
    }>
  }>
}
```
```
POST /api/posts/new

Body {
  title: String
  body: String
  category: String
  userId: String
}

<!-- Success -->
returns ApiResponse

ApiResponse.status: 'success'
ApiResponse.data {
  post: {
    title: String
    body: String
    category: String
    userId: String
  }
}
```
```
POST /users/new

Body {
  firstName: String
  lastName: String
  email: String
  userName: String
  bio: String
  password: String
}

<!-- Success -->
return ApiResponse

ApiResponse.status: 'success'
ApiResponse.data {
  user {
    firstName: String
    lastName: String
    email: String
    userName: String
    bio: String
    password: String
  }
}
```
```
POST /users/login

Body {
  userName: String
  password: String
}

<!-- Success -->
return ApiResponse

ApiResponse.status
ApiResponse.data {
  user {
    id: String
    firstName: String
    lastName: String
  }
  token: String
}

<!-- Error -->
return ApiResponse

ApiResponse.status: 'error'
ApiResponse.message: 'access denied'
```

TODO: check `users/new` for return of password or clarify here
