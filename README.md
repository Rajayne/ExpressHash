# ExpressHash

npm install bcrypt
import with const bcrypt = require("bcrypt")

1. bcrypt.hash(password-to-hash, work-factor)
   Hash password, using work factor (12 is a good choice).
   Returns promise — resolve to get hashed password.

2. bcrypt.compare(password, hashed-password)
   Check if password is valid.
   Returns promise — resolve to get boolean.

# Login

- Try to find user first
- If exists, compare hashed password to hash of login password
  bcrypt.compare()

```
Example
---
if (user) {
      if (await bcrypt.compare(password, user.password) === true) {
        return res.json({ message: "Logged in!" });
      }
}
throw new ExpressError("Invalid user/password", 400)
```

# JWT (JSON Web Tokens)

Comprised of:

1. Header containing metadata (signing algorithm & token type)
2. Payload typically containing object data like user id (encoded, not encrypted)
3. Signature with secret key

# Using JWTs

npm install jsonwebtoken

1. jwt.sign(payload, secret-key, jwt-options)
   payload: object to store as payload of token
   secret-key: secret string used to “sign” token
   jwt-options: optional object of settings for making the token

# Decoding / Verifying Tokens

1. jwt.decode(token)
   Return the payload from the token (works without secret key. Remember, the tokens are signed, not enciphered!)

2. jwt.verify(token, secret-key)
   Verify token signature and return payload is valid. If not, raise error.
