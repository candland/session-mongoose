## Changes from fork
	* uses the same mongoose instance
	* Changed to work with new npm
	* Connect instance must be passed into the require instance

`session-mongoose` module is an implementation of `connect` session store using [Mongoose](http://mongoosejs.com).

## Implementation Note:

Uses [mongeese](https://github.com/donpark/mongeese) module to isolate session database from app's default Mongoose database.

## Install

    npm install session-mongoose

## Usage

Create session store:

    var SessionMongoose = require("session-mongoose")(express);
    var mongooseSessionStore = new SessionMongoose({
        url: "mongodb://localhost/session",
        interval: 120000 // expiration check worker run interval in millisec (default: 60000)
    });

Configure Express

    var express = require("express");
    ...
    // configure session provider
    app.use(express.session({
        store: mongooseSessionStore,
        ...
    });
    ...

That's it.
