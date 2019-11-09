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

## Api Routes
```
GET /api/comment

Params {
  offset: Number<increments of 4>
  sort: String<'asc' | 'desc'>
}

<!-- Success -->
returns Array<Comments>

Comments {
  name: String
  title: String
  body: String
  avatar: String
}

<!-- Error -->
returns Array<>

```
```
POST /api/comment/new

Body {
  name: String
  title: String
  body: String
  avatar: String
}

<!-- Success -->
returns null

<!-- Error -->
returns null
```
