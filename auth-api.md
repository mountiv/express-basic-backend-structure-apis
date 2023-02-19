# API DOCUMENTATION for express-basic-backend-structure

## AUTH APIs [/api/auth]

To create an account, it is needed to check email and username are already registered or not in database.
POST request [/api/auth/check/...] will check in front-end when a user input his/her email and username and let him/her know to choose other ones.


### API

- POST [/api/auth/check/email] : CHECK EMAIL

- POST [/api/auth/check/username] : CHECK USERNAME

- POST [/api/auth/signup] : SIGNUP

- POST [/api/auth/login] : LOGIN


### USER SCHEMA

```
const UserSchema = new Schema(
  {
    email: {
      type: String,
      required: true,
      unique: true,
    },
    username: {
      type: String,
      required: true,
      unique: true,
    },
    name: {
      firstname: { type: String },
      lastname: { type: String },
    },
    title: { type: String },
    summary: { type: String },
    address: {
      street: { type: String },
      city: { type: String },
      state: { type: String },
      country: { type: String },
    },
    mobile: { type: String },
    telephone: { type: String },
    zipcode: { type: String },
    interest: [{ type: String }],
    socialMediaHandles: {
      type: Map,
      of: String,
    },
    securityQueries: {
      type: Map,
      of: String,
    },
    password: {
      type: String,
      required: true,
    },
    isAllowed: {
      type: Boolean,
      default: true,
    },
  },
  { timestamps: true }
);
```


## Author

© me
