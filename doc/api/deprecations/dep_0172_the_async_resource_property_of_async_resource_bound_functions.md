### DEP0172: The `asyncResource` property of `AsyncResource` bound functions

<!-- YAML
changes:
  - version: REPLACEME
    pr-url: https://github.com/nodejs/node/pull/46432
    description: Runtime-deprecation.
-->

Type: Runtime

In a future version of Node.js, the `asyncResource` property will no longer
be added when a function is bound to an `AsyncResource`.

[NIST SP 800-38D]: https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38d.pdf
[RFC 6066]: https://tools.ietf.org/html/rfc6066#section-3
[RFC 8247 Section 2.4]: https://www.rfc-editor.org/rfc/rfc8247#section-2.4
[WHATWG URL API]: url.md#the-whatwg-url-api
[`"exports"` or `"main"` entry]: packages.md#main-entry-point-export
[`'uncaughtException'`]: process.md#event-uncaughtexception
[`--force-node-api-uncaught-exceptions-policy`]: cli.md#--force-node-api-uncaught-exceptions-policy
[`--pending-deprecation`]: cli.md#--pending-deprecation
[`--throw-deprecation`]: cli.md#--throw-deprecation
[`--trace-atomics-wait`]: cli.md#--trace-atomics-wait
[`--unhandled-rejections`]: cli.md#--unhandled-rejectionsmode
[`Buffer.allocUnsafeSlow(size)`]: buffer.md#static-method-bufferallocunsafeslowsize
[`Buffer.from(array)`]: buffer.md#static-method-bufferfromarray
[`Buffer.from(buffer)`]: buffer.md#static-method-bufferfrombuffer
[`Buffer.isBuffer()`]: buffer.md#static-method-bufferisbufferobj
[`Cipher`]: crypto.md#class-cipher
[`Decipher`]: crypto.md#class-decipher
[`REPLServer.clearBufferedCommand()`]: repl.md#replserverclearbufferedcommand
[`ReadStream.open()`]: fs.md#class-fsreadstream
[`Server.getConnections()`]: net.md#servergetconnectionscallback
[`Server.listen({fd: <number>})`]: net.md#serverlistenhandle-backlog-callback
[`SlowBuffer`]: buffer.md#class-slowbuffer
[`WriteStream.open()`]: fs.md#class-fswritestream
[`assert`]: assert.md
[`asyncResource.runInAsyncScope()`]: async_context.md#asyncresourceruninasyncscopefn-thisarg-args
[`buffer.subarray`]: buffer.md#bufsubarraystart-end
[`child_process`]: child_process.md
[`clearInterval()`]: timers.md#clearintervaltimeout
[`clearTimeout()`]: timers.md#cleartimeouttimeout
[`console.error()`]: console.md#consoleerrordata-args
[`console.log()`]: console.md#consolelogdata-args
[`crypto.Certificate()` constructor]: crypto.md#legacy-api
[`crypto.DEFAULT_ENCODING`]: crypto.md#cryptodefault_encoding
[`crypto.createCipher()`]: crypto.md#cryptocreatecipheralgorithm-password-options
[`crypto.createCipheriv()`]: crypto.md#cryptocreatecipherivalgorithm-key-iv-options
[`crypto.createDecipher()`]: crypto.md#cryptocreatedecipheralgorithm-password-options
[`crypto.createDecipheriv()`]: crypto.md#cryptocreatedecipherivalgorithm-key-iv-options
[`crypto.fips`]: crypto.md#cryptofips
[`crypto.pbkdf2()`]: crypto.md#cryptopbkdf2password-salt-iterations-keylen-digest-callback
[`crypto.randomBytes()`]: crypto.md#cryptorandombytessize-callback
[`crypto.scrypt()`]: crypto.md#cryptoscryptpassword-salt-keylen-options-callback
[`decipher.final()`]: crypto.md#decipherfinaloutputencoding
[`decipher.setAuthTag()`]: crypto.md#deciphersetauthtagbuffer-encoding
[`diagnostics_channel.subscribe(name, onMessage)`]: diagnostics_channel.md#diagnostics_channelsubscribename-onmessage
[`diagnostics_channel.unsubscribe(name, onMessage)`]: diagnostics_channel.md#diagnostics_channelunsubscribename-onmessage
[`dns.lookup()`]: dns.md#dnslookuphostname-options-callback
[`dnsPromises.lookup()`]: dns.md#dnspromiseslookuphostname-options
[`domain`]: domain.md
[`ecdh.setPublicKey()`]: crypto.md#ecdhsetpublickeypublickey-encoding
[`emitter.listenerCount(eventName)`]: events.md#emitterlistenercounteventname
[`events.listenerCount(emitter, eventName)`]: events.md#eventslistenercountemitter-eventname
[`fs.FileHandle`]: fs.md#class-filehandle
[`fs.access()`]: fs.md#fsaccesspath-mode-callback
[`fs.appendFile()`]: fs.md#fsappendfilepath-data-options-callback
[`fs.appendFileSync()`]: fs.md#fsappendfilesyncpath-data-options
[`fs.createReadStream()`]: fs.md#fscreatereadstreampath-options
[`fs.createWriteStream()`]: fs.md#fscreatewritestreampath-options
[`fs.exists(path, callback)`]: fs.md#fsexistspath-callback
[`fs.lchmod(path, mode, callback)`]: fs.md#fslchmodpath-mode-callback
[`fs.lchmodSync(path, mode)`]: fs.md#fslchmodsyncpath-mode
[`fs.lchown(path, uid, gid, callback)`]: fs.md#fslchownpath-uid-gid-callback
[`fs.lchownSync(path, uid, gid)`]: fs.md#fslchownsyncpath-uid-gid
[`fs.read()`]: fs.md#fsreadfd-buffer-offset-length-position-callback
[`fs.readSync()`]: fs.md#fsreadsyncfd-buffer-offset-length-position
[`fs.stat()`]: fs.md#fsstatpath-options-callback
[`fs.write()`]: fs.md#fswritefd-buffer-offset-length-position-callback
[`fs.writeFile()`]: fs.md#fswritefilefile-data-options-callback
[`fs.writeFileSync()`]: fs.md#fswritefilesyncfile-data-options
[`http.ClientRequest`]: http.md#class-httpclientrequest
[`http.IncomingMessage`]: http.md#class-httpincomingmessage
[`http.ServerResponse`]: http.md#class-httpserverresponse
[`http.get()`]: http.md#httpgetoptions-callback
[`http.request()`]: http.md#httprequestoptions-callback
[`https.get()`]: https.md#httpsgetoptions-callback
[`https.request()`]: https.md#httpsrequestoptions-callback
[`message.connection`]: http.md#messageconnection
[`message.headersDistinct`]: http.md#messageheadersdistinct
[`message.headers`]: http.md#messageheaders
[`message.socket`]: http.md#messagesocket
[`message.trailersDistinct`]: http.md#messagetrailersdistinct
[`message.trailers`]: http.md#messagetrailers
[`module.createRequire()`]: module.md#modulecreaterequirefilename
[`os.networkInterfaces()`]: os.md#osnetworkinterfaces
[`os.tmpdir()`]: os.md#ostmpdir
[`process.env`]: process.md#processenv
[`process.exit()`]: process.md#processexitcode
[`process.exitCode`]: process.md#processexitcode_1
[`process.getActiveResourcesInfo()`]: process.md#processgetactiveresourcesinfo
[`process.mainModule`]: process.md#processmainmodule
[`punycode`]: punycode.md
[`readable.readableEnded`]: stream.md#readablereadableended
[`request.abort()`]: http.md#requestabort
[`request.connection`]: http.md#requestconnection
[`request.destroy()`]: http.md#requestdestroyerror
[`request.socket`]: http.md#requestsocket
[`require.extensions`]: modules.md#requireextensions
[`require.main`]: modules.md#accessing-the-main-module
[`response.connection`]: http.md#responseconnection
[`response.end()`]: http.md#responseenddata-encoding-callback
[`response.finished`]: http.md#responsefinished
[`response.socket`]: http.md#responsesocket
[`response.writableEnded`]: http.md#responsewritableended
[`response.writableFinished`]: http.md#responsewritablefinished
[`script.createCachedData()`]: vm.md#scriptcreatecacheddata
[`setInterval()`]: timers.md#setintervalcallback-delay-args
[`setTimeout()`]: timers.md#settimeoutcallback-delay-args
[`socket.bufferSize`]: net.md#socketbuffersize
[`timeout.ref()`]: timers.md#timeoutref
[`timeout.refresh()`]: timers.md#timeoutrefresh
[`timeout.unref()`]: timers.md#timeoutunref
[`tls.CryptoStream`]: tls.md#class-tlscryptostream
[`tls.SecureContext`]: tls.md#tlscreatesecurecontextoptions
[`tls.SecurePair`]: tls.md#class-tlssecurepair
[`tls.TLSSocket`]: tls.md#class-tlstlssocket
[`tls.checkServerIdentity()`]: tls.md#tlscheckserveridentityhostname-cert
[`tls.createSecureContext()`]: tls.md#tlscreatesecurecontextoptions
[`url.format()`]: url.md#urlformaturlobject
[`url.parse()`]: url.md#urlparseurlstring-parsequerystring-slashesdenotehost
[`url.resolve()`]: url.md#urlresolvefrom-to
[`util._extend()`]: util.md#util_extendtarget-source
[`util.getSystemErrorName()`]: util.md#utilgetsystemerrornameerr
[`util.inspect()`]: util.md#utilinspectobject-options
[`util.inspect.custom`]: util.md#utilinspectcustom
[`util.isArray()`]: util.md#utilisarrayobject
[`util.isBoolean()`]: util.md#utilisbooleanobject
[`util.isBuffer()`]: util.md#utilisbufferobject
[`util.isDate()`]: util.md#utilisdateobject
[`util.isError()`]: util.md#utiliserrorobject
[`util.isFunction()`]: util.md#utilisfunctionobject
[`util.isNull()`]: util.md#utilisnullobject
[`util.isNullOrUndefined()`]: util.md#utilisnullorundefinedobject
[`util.isNumber()`]: util.md#utilisnumberobject
[`util.isObject()`]: util.md#utilisobjectobject
[`util.isPrimitive()`]: util.md#utilisprimitiveobject
[`util.isRegExp()`]: util.md#utilisregexpobject
[`util.isString()`]: util.md#utilisstringobject
[`util.isSymbol()`]: util.md#utilissymbolobject
[`util.isUndefined()`]: util.md#utilisundefinedobject
[`util.log()`]: util.md#utillogstring
[`util.types`]: util.md#utiltypes
[`util`]: util.md
[`worker.exitedAfterDisconnect`]: cluster.md#workerexitedafterdisconnect
[`worker.terminate()`]: worker_threads.md#workerterminate
[`writable.writableLength`]: stream.md#writablewritablelength
[`zlib.bytesWritten`]: zlib.md#zlibbyteswritten
[alloc]: buffer.md#static-method-bufferallocsize-fill-encoding
[alloc_unsafe_size]: buffer.md#static-method-bufferallocunsafesize
[from_arraybuffer]: buffer.md#static-method-bufferfromarraybuffer-byteoffset-length
[from_string_encoding]: buffer.md#static-method-bufferfromstring-encoding
[legacy URL API]: url.md#legacy-url-api
[legacy `urlObject`]: url.md#legacy-urlobject
[static methods of `crypto.Certificate()`]: crypto.md#class-certificate
[subpath exports]: packages.md#subpath-exports
[subpath imports]: packages.md#subpath-imports
[subpath patterns]: packages.md#subpath-patterns
