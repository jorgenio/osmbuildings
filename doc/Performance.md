# Performance

What's done & why in terms of performance.


## Projection cache

Looks like this has been a bad idea - removed.
Probably develop the concept into rendering pipelines.
(http://jsperf.com/projcache)


## Readable keys (for compact data structures)

Seemed to be a good idea making these a bit more readable.
Loss expected but turned out to be a slight gain.
http://jsperf.com/readable-keys/2
TODO: Not true anymore. Refactor to objects/properties.


## Combined 2d faces

iPhone4, iOS5: seperate faces are 56% slower
MBA 2010, Chrome: combined faces are 68% slower
Staying with combined so far, probably add system detection.
(http://jsperf.com/canvas-polygon-combiner)


## Typed arrays

Using slice() is not worth it, but it turned out dropping some typed arrays is a good idea.
Especially when these are created on each rendering pass.
(http://jsperf.com/slice-access)


## Canvas anti alias

While looking slick, it eats performance.
Not so on iPhone4, iOS5: it doesn't matter
MBA 2010, Chrome: anti alias is 24% slower
Node: for *any* test, stroking lines eats ~60% performance
(http://jsperf.com/canvas-anti-alias)


## Math round

Using ~~ for a while, it turns out, bit shift << 0 is even faster.
iPad4, iOS6: 12% faster
MBA 2010, Chrome: 25% faster
(http://jsperf.com/math-round-vs-hack/3)