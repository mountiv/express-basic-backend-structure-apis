# API DOCUMENTATION for express-basic-backend-structure

## POST APIs [/api/post]

Implemented simple features for blog site using REST API.
Auth middleware implemented.
Request will include token retrieved via login as Bear Token.


- POST [/api/post/create] : CREATE A POST

- GET [/api/post/:id] : GET A POST BY ID

- PUT [/api/post/:id] : UPDATE A POST

- DELETE [/api/post/:id] : DELETE A POST

- POST [/api/post/vote/:id] : LIKE OR UNLIKE A POST

- GET [/api/post/all] : GET POSTS WITH LIMIT AND OFFSET

- POST [/api/post/search] : SEARCH POSTS WITH KEYWORD


### POST SCHEMA

```
const PostSchema = new Schema(
  {
    title: {
      type: String,
      required: true,
    },
    content: {
      type: String,
      required: true,
    },
    keywords: [String],
    author: {
      type: String,
      required: true,
    },
    vote: {
      like: {
        count: {
          type: Number,
          default: 0,
        },
        users: [String],
      },
      dislike: {
        count: {
          type: Number,
          default: 0,
        },
        users: [String],
      },
    },
  },
  { timestamps: true }
);

```


## Author

© me
