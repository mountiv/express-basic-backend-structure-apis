# API DOCUMENTATION for express-basic-backend-structure

## POST APIs [/api/post]

**SUMMARY**
Implemented simple features for blog site using REST API.
Auth middleware implemented.
Request will include token retrieved via login as Bear Token.

### POST SCHEMA

```
const PostSchema = new Schema(
  {
    title: { type: String, required: true },
    content: { type: String, required: true },
    keywords: [String],
    author: { type: String, required: true },
    vote: {
      like: { count: { type: Number, default: 0 }, users: [String] },
      dislike: { count: { type: Number, default: 0 }, users: [String] },
    },
  },
  { timestamps: true }
);
```

### General features

- create a post (POST)

- get post by id (GET)

- update title and content (PUT)

- delete post by id (DELETE)

- vote a post (POST)

- get posts with limit and offset (GET)

- search posts in title and content text filed (POST)

### CREATE A POST: post request [/api/post/create]

- request in body as json

```
{
    "title":"hello world",
    "content":"this is my first article",
    "keywords":["hello","world", "article"],
    "username":"testuser"
}
```

### GET A POST BY ID: get request [/api/post/:id]

### UPDATE TITLE and CONTENT: put request [/api/post/:id]

- request in body as json

```
{
    "title":"hello world",
    "content":"this is my updated article."
}
```

### DELETE A POST BY ID: delete request [/api/post/:id]

### VOTE A POST: post request [/api/post/vote/:id]

- request in body as json

```
{
    "type": "dislike",
    "username": "testuser"
}
```

### GET POST WITH LIMIT and OFFSET: get request [/api/post/all]

- request with params(limit, offset)

```
http://localhost:8000/api/post/all?limit=10&offset=30
```

### SEARCH POSTS IN TITLE and CONTENT TEXT FIELDS: post request [/api/post/search]

- request with params(search)

```
http://localhost:8000/api/post/search?search=world
```

## Author

© me
