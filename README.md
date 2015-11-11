# Passport-Linkedin-OAuth-Token

[Passport](http://passportjs.org/) strategy for authenticating with [Linkedin](http://www.linkedin.com/)
access tokens using the OAuth 2.0 API.

This module lets you authenticate using Linkedin in your Node.js applications.
By plugging into Passport, Linkedin authentication can be easily and
unobtrusively integrated into any application or framework that supports
[Connect](http://www.senchalabs.org/connect/)-style middleware, including
[Express](http://expressjs.com/).

P.S. The special use case for this library is to use with [ember-cli-simple-auth-torii](https://github.com/simplabs/ember-cli-simple-auth-torii),
are very similar to [passport-facebook-token](https://github.com/drudge/passport-facebook-token).
There is a passport-linkedin-token exists which isn't worked with OAuth2 and can't get user keeping client-side flow.

## Installation

    $ npm install passport-linkedin-oauth-token

## Usage

#### Configure Strategy

The Linkedin authentication strategy authenticates users using a Linkedin
account and OAuth token.

```js
passport.use(new LinkedinTokenStrategy({
    clientID: LINKEDIN_APP_ID,
    clientSecret: LINKEDIN_APP_SECRET
  },
  function(accessToken, refreshToken, profile, done) {
    User.findOrCreate({ linkedinId: profile.id }, function (err, user) {
      return done(err, user);
    });
  }
));
```

```js
app.post('/auth/linkedin/token',
  passport.authenticate('linkedin-oauth-token'),
  function (req, res) {
    // do something with req.user
    res.send(req.user? 200 : 401);
  }
);
```

## Author

  [Vladimir Katansky](http://github.com/Blackening999)
  [Roger Kuo](https://github.com/b96705008)

## License

(The MIT License)

Copyright (c) 2014 Vladimir Katansky

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
