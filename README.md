# organel | 

Organelle responsible for mounting route handlers to ExpressHttpServer instance passed via HttpServer chemical. 

It also mounts any client-side javascript or less entry points and all their dependencies via require/import calls as bundles.

More details can be found at (ExpressHttpPages wisdom page)[http://wisdom.camplight.net/wisdom/511126818db3ebbc0d000006/Organic---ExpressHttpPages]


* `mount`: String

  *optional* value to be used for prefixing all routes. Useful for mounting all actions found to specific root url

* `cwd`: Object

  * optional * , Object containing key:value pairs, where all values will be prefixed with `process.cwd()` and set with their coressponding keys directly to the DNA of the organelle.

* `pages`: String

  provided full path to directory containing `pages` defined within javascript files with source code definition similar to ExpressHttpActions.

  Furthermore any files matching defined patterns will be mounted as client-side code or style.

* `pageHelpers`: String

  provided full path to directory containing `pageHelpers` defined within commonjs modules. Any exports from them will be attached to context of the `pages` within object with the same name as the corresponding page helper.

* `page` : Object
  * extname : ".jade"

* `pageStyle` : Object
  * extname : ".less"
  * urlName : "/style.css"

* `pageCode` : Object
  * extname : ".jade.js"
  * urlName : "/code.js"

* `prebuildAssets` : false

  Instructs the organelle to prebuild any found assets (client-side code or style) by emitting the corresponding chemicals and capturing their output either to memory or to given `assetsBuildDir`. 

  In case there is existing file corresponding to the asset been build, no compilation/prebuild occurs.

* `assetsBuildDir` : String

  If provided prebuild assets will be stored at given directory by its full path. 

  In addition providing value to this option instructs the organelle to try fetching the asset's contents from that directory. If the file is missing, the asset will be prebuild and then served. Having `prebuildAssets` option enabled, will instruct any compilation to be written at the given file location.

* `log`: false

  flag for instructing logging to stdout any found pages and client-side bundles (js/css).

* `debug` : false

  Providing `true` to this option will disable browser caching. This is useful during development.


# incoming | HttpServer

* data - ExpressHttpServer instance


# outgoing | BundleCode

Chemical is emitted from the organelle upon need to bundle specific client-side javascript (`.jade.js` or what is configured is used as entry point).

* code : full path*/

/* outgoing | BundleStyle

Chemical is emitted from the organelle upon need to bundle specific client-side javascript (`.less` or what is configured is used as entry point).

* style : full path

# outgoing | RenderPage

Chemical is emitted from the organelle upon need to render specific template.

Usually that is either static `.jade` file without page handler or page handler issuing `res.sendPage` or `res.renderPage` 

Checkout [this](http://wisdom.camplight.net/wisdom/511126818db3ebbc0d000006/Organic---ExpressHttpPages) for more details

* page : full path
* ... : data