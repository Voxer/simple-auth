# Simple-auth

[![Build Status](https://secure.travis-ci.org/sentientwaffle/simple-auth.png?branch=master)](http://travis-ci.org/sentientwaffle/simple-auth)

Framework-agnostic HTTP Basic authentication for Node.js (no need for
express/connect/insert-web-framework).

# Example

    var http = require('http')
      , basic_auth = require('simple-auth')('username123', 'password456')

    http.createServer(function (req, res) {
      basic_auth(req, res, function() {
        res.writeHead(200, {'Content-Type': 'text/plain'})
        res.end('Your username & password were correct\n')
      })
    }).listen(31337, '127.0.0.1')

    console.log('Server running at http://127.0.0.1:31337/')

# Installation

    $ npm install simple-auth

# API
## `basic_auth(username, password[, fail_delay])`

Returns a function that receives `(req, res, next)`, where `next` will only
be called if the user authenticates.

`fail_delay` is the number of milliseconds that the user will be prevented from
retrying after a failed authentication (defaults to 5000).

# License

MIT
