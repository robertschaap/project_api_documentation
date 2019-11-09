# General
To make development a bit easier and mimic real life circumstances, some of the projects I've been working on that I've repeatedly used to test out different technologies have been split into separate repositories for front-end and back-end (where possible). The documentation per project notes the technologies used and API routes and responses. This ensures that any front-end repo could talk to any back-end repo. It makes any change to either a bit more painful, but the lessons learned there are exactly the point.

## Ports
- Front-end port  `3000`
- Back-end port   `4000`

## Projects Covered
- Blog
- BulletinBoard v1
- BulletinBoard v2

## Type Notation
Routes are denoted by HTTP verb and a route string: `GET /api/myroute`. Any query parameters, request body, or anything attached to the request that needs documenting is described in a typed object-like fashion.

```
Params {
  myParam: Type
}
```

Each such object consists of keys and types and keeps a format loosely based on FlowJS and TypeScript. Primitive type examples are Number, String, Array, Object, Boolean. If any of these primitive types needs a value or another type, it is put in angle brackets.

```
Params {
  myParam1: String
  myParam2: String<'option a' | 'option b'>
  myParam3: String<AnotherType>
}
```
