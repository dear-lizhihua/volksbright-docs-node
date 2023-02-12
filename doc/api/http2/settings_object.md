### Settings object

<!-- YAML
added: v8.4.0
changes:
  - version: v12.12.0
    pr-url: https://github.com/nodejs/node/pull/29833
    description: The `maxConcurrentStreams` setting is stricter.
  - version: v8.9.3
    pr-url: https://github.com/nodejs/node/pull/16676
    description: The `maxHeaderListSize` setting is now strictly enforced.
-->

The `http2.getDefaultSettings()`, `http2.getPackedSettings()`,
`http2.createServer()`, `http2.createSecureServer()`,
`http2session.settings()`, `http2session.localSettings`, and
`http2session.remoteSettings` APIs either return or receive as input an
object that defines configuration settings for an `Http2Session` object.
These objects are ordinary JavaScript objects containing the following
properties.

* `headerTableSize` {number} Specifies the maximum number of bytes used for
  header compression. The minimum allowed value is 0. The maximum allowed value
  is 2<sup>32</sup>-1. **Default:** `4096`.
* `enablePush` {boolean} Specifies `true` if HTTP/2 Push Streams are to be
  permitted on the `Http2Session` instances. **Default:** `true`.
* `initialWindowSize` {number} Specifies the _sender's_ initial window size in
  bytes for stream-level flow control. The minimum allowed value is 0. The
  maximum allowed value is 2<sup>32</sup>-1. **Default:** `65535`.
* `maxFrameSize` {number} Specifies the size in bytes of the largest frame
  payload. The minimum allowed value is 16,384. The maximum allowed value is
  2<sup>24</sup>-1. **Default:** `16384`.
* `maxConcurrentStreams` {number} Specifies the maximum number of concurrent
  streams permitted on an `Http2Session`. There is no default value which
  implies, at least theoretically, 2<sup>32</sup>-1 streams may be open
  concurrently at any given time in an `Http2Session`. The minimum value
  is 0. The maximum allowed value is 2<sup>32</sup>-1. **Default:**
  `4294967295`.
* `maxHeaderListSize` {number} Specifies the maximum size (uncompressed octets)
  of header list that will be accepted. The minimum allowed value is 0. The
  maximum allowed value is 2<sup>32</sup>-1. **Default:** `65535`.
* `maxHeaderSize` {number} Alias for `maxHeaderListSize`.
* `enableConnectProtocol`{boolean} Specifies `true` if the "Extended Connect
  Protocol" defined by [RFC 8441][] is to be enabled. This setting is only
  meaningful if sent by the server. Once the `enableConnectProtocol` setting
  has been enabled for a given `Http2Session`, it cannot be disabled.
  **Default:** `false`.

All additional properties on the settings object are ignored.
