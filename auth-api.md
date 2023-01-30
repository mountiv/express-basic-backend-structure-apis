# API DOCUMENTATION for express-basic-backend-structure

## AUTH APIs [/api/auth]

To create an account, it is needed to check email and username are already registered or not in database.
POST request [/api/auth/check/...] will check in front-end when a user input his/her email and username and let him/her know to choose other ones.

### USER SCHEMA

```
const UserSchema = new Schema(
  {
    email: { type: String, required: true, unique: true },
    username: { type: String, required: true, unique: true },
    socialMediaHandles: {
      type: Map,
      of: String,
    },
    securityQueries: { type: Map, of: String },
    password: { type: String, required: true },
  },
  { timestamps: true }
);
```

### CHECK EMAIL: post request [/api/auth/check/email]

- request parameters as json

```
{
    "email": "testuser@example.com"
}
```

- response parameters as json
```
{
    "msg": "that email already taken!"
}
```

### CHECK USERNAME: post request [/api/auth/check/username]

- request parameters as json as req.body

```
{
    "username": "testuser1"
}
```

- response parameters as json

```
{
    "msg": "available username"
}
```


### SIGNUP: post request [/api/auth/signup]

- send parameters as json

```
{
    "username":"testuser", 
    "email":"testuser@example.com", 
    "social":{
        "git":"@github.testuser",
        "medium":"@medium.testuser"
        },
    "securityQueries":{
        "Where ware you born?":"Earth",
        "What is your favorite pet name?":"Zemma"
        },
    "password":"testpassword"
}
```

- response as a simple string

if email or username was duplicated you can see following message:

```
Email or Username duplicated!
```

successfully signed up with following messsage:

```
successfully created account
```

### LOGIN: post request [/api/auth/login]

- send parameters as json:

```
{
    "username":"testuser", 
    "password":"testpassword"
}
```

- response as json
successfully logged in with following json data:

```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3R1c2VyQGV4YW1wbGUuY29tIiwidXNlcm5hbWUiOiJ0ZXN0dXNlciIsIl9pZCI6IjYzZDYyOWU2Mzk2ZGU1MDE4NmQ3ZGQxMSIsImlhdCI6MTY3NDk4MjE3MiwiZXhwIjoxNjc1MDY4NTcyfQ.ggI3Ui7KkaZr1cqR5wYbLrn_7UZcTo2GPDe8gGaQ_Xg"
}
```

if user not found:

```
{
    "message": "user not found."
}
```

if password is incorrect:

```
{
    "message": "invalid password!"
}
```

## Author

© me
