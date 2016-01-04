# Simple request based parse.com REST wrapper, middleware for managing users in express. (WIP)

Environement variables:

PARSE_APPLICATION_ID
PARSE_REST_API_KEY
PARSE_MASTER_KEY

`var users = require('parse-rest');`

## User manipulation methods

```
users.get('username', function(err, user) { ... })
users.all(function(err, users) { ... })
users.find({ 'userattribute' : 'value' }, , function(err, user) { ... })
users.login(username, password, function(err, user) { ... })
users.update(id, updates, function(err) { ... }))
users.checkToken(parseAuthenticationToken, function(err, user) { ... });
```

## Express authentication middleware

The middleware expects a "token" attribute in posted json, or a "token" query parameter. 
Un-authenticated requests will receive a response with http code 403, and a json body of "{ error : 403 }".

```
var express = require('express');
var app = express(); 

var users = require('parse-rest');
app.use(users.auth);
```
