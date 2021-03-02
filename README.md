# cf-access-jwt

Tiny lib for decoding Cloudflare Access JWTs and verifying signatures, using
native crypto APIs.

Currently supports `alg:'RS256'` only.

```js
const jwt = request.headers.get('Cf-Access-Jwt-Assertion');

const result = await parseJwt(jwt, issuer, audience);
if (!result.valid) {
  console.log(result.reason); // Invalid issuer/audience, expired, etc
} else {
  console.log(result.payload); // { iss, sub, aud, iat, exp, ...claims }
}
```

Code shamelessly stolen from: https://github.com/cfworker/cfworker/
