# gracenode-session Module

Session management module for gracenode framework.

This is designed to function within gracenode framework.

## How to include it in my project

To add this package as your gracenode module, add the following to your package.json:

```
"dependencies": {
	"gracenode": "",
	"gracenode-session": ""
}
```

To use this module in your application, add the following to your gracenode bootstrap code:

```
var gracenode = require('gracenode');
// this tells gracenode to load the module
gracenode.use('gracenode-session');
```

To access the module:

```
// the prefix gracenode- will be removed automatically
gracenode.session
```

Access
<pre>
gracenode.session
</pre>

Configurations
```javascript
"modules": {
	"session": {
		"ttl": int (in seconds)
	}
}
```

Session module itself does NOT handle reading and writting of the session data.
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

#####API: *setGetter*
Used to read data for getSession
<pre>
void setGetter(Function getterFunction);
</pre>

#####API: *setSetter*
Used to store data for setSession
<pre>
void setSetter(Function setterFunction);
</pre>

#####API: *setRemover*
Used to delte data for delSession
<pre>
void setRemover(Function removerFunction);
</pre>

#####API: *setFlusher*
Used to flush data for flush
<pre>
void setFlusher(Function flusherFunction);
</pre>

####API: *get*
Shorthand for getSession.

####API: *set*
Shorthand for setSession.

####API: *replace*
Shorthand for replaceSession.

####API: *del*
Shorthand for delSession.

####API: *flush*
Shorthand for flushSession.

#####API: *getSession*

<pre>
void getSession(String sessionId, Function callback)
</pre>
> Passes a session object to the callback

#####API: *setSession*
<pre>
void setSession(String, keyForNewSessionId, mixed value, Function callback)
</pre>

#####API: *replaceSession*
<pre>
void replaceSession(String sessionId, mixed value, Function callback)
</pre>

#####API: *delSession*
<pre>
void delSession(String sessionId, Function callback)
</pre>

#####API: *flushSession*
<pre>
void flush(Function callback)
</pre>
