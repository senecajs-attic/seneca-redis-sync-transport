# seneca-redis-sync-transport - a [Seneca](http://senecajs.org) plugin

## Seneca Redis Synchronized Transport Plugin

This plugin provides the redis pub/sub synchronized transport channel for
micro-service messages.

NOTE: Listeners are synchronized via redis incr so that messages are handled
no more than once.

ALSO READ: The [seneca-transport](http://github.com/rjrodger/seneca-transport) readme has lots of introductory material about message transports. Start there if you have not used a message transport before.

For a gentle introduction to Seneca itself, see the
[senecajs.org](http://senecajs.org) site.

For questions:
[@rjrodger](http://twitter.com/rjrodger)
[@zbangazbanga](http://twitter.com/zbangazbanga)

Current Version: 0.1.0

Tested on: Seneca 0.6.1, Node 0.10.36


### Install

```sh
npm install seneca-redis-sync-transport
```

You'll also need [redis](http://redis.io/).


## Quick Example

```js
require('seneca')()
  .use('redis-sync-transport')
  .add('foo:two',function(args,done){ done(null,{bar:args.bar}) })
  .client( {type:'redis-sync',pin:'foo:one,bar:*'} )
  .listen( {type:'redis-sync',pin:'foo:two,bar:*'} )
```



