# gracenode-session Module

gracenode-session is designed to work within the Gracenode framework. It can not function without the Gracenode framework.

## Installation

```
npm install gracenode-session
```

Or add it to your package.json

```
"dependencies": {
	"gracenode": "",
	"gracenode-session": ""
}
```

Gracenode does not automatically detect middleware. To add the session module to your framework you have to call `use`.

```
var gracenode = require('gracenode');
gracenode.use('gracenode-session');
```

Loading the session module like this will expose it in `gracenode.session`.

## Configuration
This module requires you to have a configuration parameter set for the TTL. Below is a configuration example.
```
"modules": {
	"session": {
		"ttl": int (in seconds)
	}
}
```

##Version 1.0.0
Since version 1.0.0 there is a backward compatability break. When calling `getSession` a data object is no longer returned, instead an instantiated Session class is returned which allows for more control over the session data without having to query your datastore.

##API

###Session Object
When calling `getSession` an instance of the Session class is returned to retrieve and set data to the session.

####Session.get
Returns a value for key if this has been stored.
```
session.get('key');
```

####Session.set
Set a value for key.
```
session.set('foo', 'bar');
```

####Session.save
Save the current data to your datastore.
```
session.save(function (error) {
	//Your magic
});
```

###Methods

####session.setGetter(getterFunction {function})
Used to read data for getSession

####session.setSetter(setterFunction {function})
Used to store data for setSession

####session.setRemover(deleteFunction {function})
Used to delte data for delSession

####session.setFlusher(flusherFunction {function})
Used to flush data for flush

####session.get
Shorthand for `getSession`.

####session.set
Shorthand for `setSession`.

####session.replace
Shorthand for `replaceSession`.

####session.del
Shorthand for `delSession`.

####session.flush
Shorthand for `flushSession`.

####session.getSession(sessionId {string, int}, callback {function})
Retrieve a new Session object from sessionId.

####session.setSession(sessionId {string, int}, data {object}, callback {function})
Start a new session

####session.replaceSession(sessionId {string, int}, callback {function});
Replace the session with data in `data`. It is prefered you call `Session.save` instead.

####session.delSession(sessionId {string, int}, callback {function})
Destroy a session

####session.flushSession(callback {function})
Flush a session
