![Seneca](http://senecajs.org/files/assets/seneca-logo.png)
> A [Seneca.js][] transport plugin

# seneca-redis-sync-transport
[![Build Status][travis-badge]][travis-url]
[![Gitter][gitter-badge]][gitter-url]

This plugin provides the redis pub/sub synchronized transport channel for
micro-service messages.

NOTE: Listeners are synchronized via redis incr so that messages are handled
no more than once.

ALSO READ: The [seneca-transport](http://github.com/rjrodger/seneca-transport) readme has lots of introductory material about message transports. Start there if you have not used a message transport before.

- __Version:__ 0.1.0
- __Tested on:__ Seneca 0.7
- __Node:__ 0.10, 0.12, 4
- __License:__ [MIT][]

seneca-redis-sync-transport's source can be read in an annotated fashion by,

- running `npm run annotate`
- viewing [online](https://github.com/senecajs/seneca-redis-sync-transport/doc/redis-sync-transport.html).

The annotated source can be found locally at [./doc/redis-sync-transport.html]().

If you're using this module, and need help, you can:

- Post a [github issue][],
- Tweet to [@senecajs][],
- Ask on the [Gitter][gitter-url].

If you are new to Seneca in general, please take a look at [senecajs.org][]. We have everything from
tutorials to sample apps to help get you up and running quickly.


## Install
To install, simply use npm. Remember you will need to install [Seneca.js][] if you haven't already.

```
npm install seneca-redis-sync-transport
```

You'll also need [redis](http://redis.io/).

## Test
To run tests, simply use npm:

```
npm run test
```

## Quick Example

```js
require('seneca')()
  .use('redis-sync-transport')
  .add('foo:two',function(args,done){ done(null,{bar:args.bar}) })
  .client( {type:'redis-sync',pin:'foo:one,bar:*'} )
  .listen( {type:'redis-sync',pin:'foo:two,bar:*'} )
```

## Contributing
The [Senecajs org][] encourage open participation. If you feel you can help in any way, be it with
documentation, examples, extra testing, or new features please get in touch.

## License
Copyright Richard Rodger and other contributors 2015, Licensed under [MIT][].

[travis-badge]: https://travis-ci.org/senecajs/seneca-redis-sync-transport.svg
[travis-url]: https://travis-ci.org/senecajs/seneca-redis-sync-transport
[gitter-badge]: https://badges.gitter.im/Join%20Chat.svg
[gitter-url]: https://gitter.im/senecajs/seneca

[MIT]: ./LICENSE
[Senecajs org]: https://github.com/senecajs/
[Seneca.js]: https://www.npmjs.com/package/seneca
[senecajs.org]: http://senecajs.org/
[redis]: http://redis.io/
[github issue]: https://github.com/senecajs/seneca-redis-sync-transport/issues
[@senecajs]: http://twitter.com/senecajs
