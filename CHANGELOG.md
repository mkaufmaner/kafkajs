# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [1.9.3] - 2019-06-27
### Fixed
  - Fix AWS-IAM mechanism name #411 #412

## [1.9.2] - 2019-06-26
### Fixed
  - Fix typescript types for Logger, consumer pause and resume, eachMessage and EachBatch interfaces #409

## [1.9.1] - 2019-06-25
### Fixed
  - Fix typescript types for SSL, SASL and batch #407

## [1.9.0] - 2019-06-25
### Added
  - Add typescript declaration file #362 #385 #390
  - Add `requestTimeout` to apiVersions #369
  - Discard messages saw a seek operation during a fetch or batch processing #367
  - Include fetched offset metadata retrieved with `admin.fetchOffsets` #389
  - Allow offset metadata to be written as part of OffsetCommit requests #392
  - Prevent the consumption of messages for topics paused while fetch is in-flight #397
  - Add `AWS-IAM` SASL mechanism #402
  - Add `batch.offsetLagLow` #405

### Changed
  - Don't modify `global.crypto` #365
  - Change log level about producer without metadata #382
  - Update encoder to write arrays as single `Buffer.concat` where possible #394

### Fixed
  - Log error message on connection errors #400
  - Make sure runner has connected brokers and fresh metadata before it starts #404

## [1.8.1] - 2019-06-25
### Fixed
  - Make sure runner has connected brokers and fresh metadata before it starts #404

## [1.8.0] - 2019-05-13
### Added
  - Add partition-aware concurrent mode for `eachMessage` #332
  - Add `JavaCompatiblePartitioner` #358
  - Add `consumer.subscribe({ topic: RegExp })` #346
  - Update supported protocols to latest of Kafka 1 #343 #347 #348

### Changed
  - Add documentation link to `REBALANCE_IN_PROGRESS` error #341

### Fixed
  - Fix crash on offline replicas in metadata v5 response #350

## [1.7.0] - 2019-04-12
### Fixed
  - Improve compatibility with terserjs #338

### Added
  - Add `admin#fetchTopicMetadata` #331

### Changed
  - Deprecated `admin#getTopicMetadata` #331
  - `admin#fetchTopicOffsets` returns the low and high watermarks #333

## [1.6.0] - 2019-04-01
### Added
  - Allow providing a socketFactory on client creation #263
  - Add fetchTopicOffsets method #314

## [1.5.2] - 2019-04-01
### Fixed
  - Process a fixed number of lock releases per iteration on `lock#release` #323

### Changed
  - Use the max between the default request timeout and the protocol override #318
  - Only emit events if there are listeners #321

## [1.5.1] - 2019-03-14
### Fixed
  - Handle `null` keys on isAbortMarker #312

### Changed
  - Prevent subsequent calls to `consumer#run` to override the running consumer #305
  - Improve browser compatibility #300
  - Add custom `requestTimeout` for protocol fetch #310
  - Make `requestTimeout` optional, the current implementation is behind the flag `enforceRequestTimeout` #313

## [1.5.0] - 2019-03-05
### Changed
  - See `1.5.0-beta.X` versions

## [1.5.0-beta.4] - 2019-02-28
### Fixed
  - Abort old transactions on protocol error `CONCURRENT_TRANSACTIONS` #299

## [1.5.0-beta.3] - 2019-02-20
### Fixed
  - Missing default restart time on crashes due to retriable errors #283
  - Add custom requestTimeout for JoinGroup v0 #293
  - Fix propagation of custom retry configs #295

### Changed
  - Allow calling `Producer.sendBatch` with empty list #287
  - Encode non-buffer key as string by default #291

## [1.5.0-beta.2] - 2019-02-13
### Fixed
  - Handle undefined message key when producing with 0.11 #247
  - Fix consumer restart on find coordinator errors #253
  - Crash consumer on codec not implemented error #256
  - Fix error message on invalid username or password #270
  - Restart consumer on crashes due to retriable error #269
  - Remove deleted topics from the cluster target group #273

### Changed
  - Change Node engine requirement to >=8.6.0 #250
  - Don't include lockfile and vscode files in package #264

### Added
  - Allow configuring log level at runtime #278

## [1.5.0-beta.1] - 2019-01-17
### Fixed
  - Rolling upgrade from 0.10 to 0.11 causes unknown magic byte errors #246

### Changed
  - Validate consumer groupId #244

### Added
  - Expose network queue size event to consumers, producers and admin #245

## [1.5.0-beta.0] - 2019-01-08
### Changed
  - Add transactional attributes to record batch #199
  - Ignore control records #208
  - Filter aborted messages on the consumer #223 #210 #228
  - Make Round robin assigner forward `userdata` #231

### Added
  - Protocol `FindCoordinator` v1 #189
  - Protocol `InitProducerId` v0 #190
  - Protocol `AddPartitionsToTxn` v0 #191
  - Protocol `AddOffsetsToTxn` v0 #194
  - Protocol `TxnOffCommit` v0 #195
  - Protocol `EndTxn` v0 #198
  - Protocol `ListOffsets` v1 and v2 #217 #209
  - Accept max in-flight requests on the connection #216
  - Idempotent producer #203
  - Transactional producer #206
  - Protocol `SASLAuthenticate` #229
  - Add SendOffsets to consumer `eachBatch` #232
  - Add network instrumentation events #233
  - Allow users to provide offsets to the `commitOffsetsIfNecessary` #235

## [1.4.8] - 2019-02-18
### Fixed
  - Handle undefined message key when producing with 0.11 #247
  - Fix consumer restart on find coordinator errors #253
  - Crash consumer on codec not implemented error #256
  - Fix error message on invalid username or password #270

## [1.4.7] - 2019-01-17
### Fixed
  - Rolling upgrade from 0.10 to 0.11 causes unknown magic byte errors #246

## [1.4.6] - 2018-12-03
### Fixed
  - Always assign partitions based on subscribed topics #227

## [1.4.5] - 2018-11-28
### Fixed
  - Fix crash in mitigation for receiving metadata for unsubscribed topics #221

### Added
  - Add `CRASH` instrumentation event for the consumer #221

## [1.4.4] - 2018-10-29
### Fixed
  - Protocol produce v3 wasn't filtering `undefined` timestamps and was sending timestamp 0 (`NaN` converted) for all messages #188

## [1.4.3] - 2018-10-22
### Changed
  - Version `1.4.2` without test files

## [1.4.2] - 2018-10-22
### Changed
  - Allow messages with a value of `null` to support tombstones #185

## [1.4.1] - 2018-10-17
### Fixed
  - Decode multiple RecordBatch on protocol Fetch v4 #179
  - Skip incomplete record batches #182
  - Producer with `acks=0` never resolve #181

### Added
  - Runtime flag for displaying buffers in debug output #176
  - Add ZSTD to compression codecs and types #157
  - Admin get topic metadata #174

### Changed
  - Add description to lock instances #178

## [1.4.0] - 2018-10-09
### Fixed
  - Potential offset loss when updating offsets for resolved partitions #124
  - Refresh metadata on lock timeout #131
  - Cleans up stale brokers on metadata refresh #131
  - Force metadata refresh on `ECONNREFUSED` #134
  - Handle API version not supported #135
  - Handle v0.10 messages on v0.11 Fetch API #143

### Added
  - Admin delete topics #117
  - Update metadata api and allow to disable auto topic creation #118
  - Use highest available API version #135 #146
  - Admin describe and alter configs #138
  - Validate message format in producer #142
  - Consumers can detect that a topic was updated and force a rebalance #136

### Changed
  - Improved stack trace for `KafkaJSNumberOfRetriesExceeded` #123
  - Enable Kafka v0.11 API by default #141 (Can still be disabled with `allowExperimentalV011=false`)
  - Replace event emitter Lock #154
  - Add member assignment to `GROUP_JOIN` instrumentation event #136

## [1.3.1] - 2018-08-20
### Fixed
  - Client logger accessor #106
  - Producer v3 decode format #114
  - Parsing multiple responses #115
  - Fetch v4 for partial messages on record batch #116

### Added
  - Connection instrumentation events #110

## [1.3.0] - 2018-08-06
### Fixed
  - Skip unsubscribed topic assignment #86
  - Refresh metadata when producing to a topic without metadata #87
  - Discard messages with a lower offset than requested #100

### Added
  - Add consumer auto commit policies #89
  - Notify user when setting heartbeat interval to same or higher than session timeout #91
  - Constantly refresh metadata based on `metadataMaxAge` #94
  - New instrumentation events #95
  - Expose loggers #97 #102
  - Add offset management operations to the admin client #101
  - Support to record batch compression #103
  - Handle missing username/password during authentication #104

## [1.2.0] - 2018-07-02
### Fixed
  - Make sure authentication handshake remains consistent event when `broker.connect` is called concurrently #81

### Added
  - Add `producer.sendBatch` to produce to multiple topics at once #82
  - Experimental support to native Kafka 0.11 (`allowExperimentalV011`) #61 #68 #75 #76 #78
  - Enabled protocol `fetch` v3

## [1.1.0] - 2018-06-14
### Added
  - Support to SASL SCRAM (`scram-sha-256` and `scram-sha-512`) #72
  - Admin client with support to create topics #73

## [1.0.1] - 2018-05-18
### Fixed
  - Prevent crash when re-producing after metadata refresh #62

## [1.0.0] - 2018-05-14
### Changed
  - Updated readme

## [0.8.1] - 2018-04-10
### Fixed
  - Throw unretriable error for incompatible message format #49
  - Producer can't reconnect after broker disconnection #48

## [0.8.0] - 2018-04-05
### Removed
  - Backwards compatibility with the old member assignment protocol (<= 0.6.x). __v0.7.x__ is the last version with support for both protocols (commit f965e91cf883bff74332e53a8c1d25c2af39e566)

### Fixed
  - Only retry failed brokers #38

### Changed
  - Use selected assigner on consumer sync #35
  - Add validations to consumer subscribe and producer send #41

### Added
  - Consumer pause and resume #41
  - Allow `partitionAssigners` to be configured
  - Allow auto-resolve to be disabled for eachBatch #44

## [0.7.1] - 2018-01-22
### Fixed
  - Fix member assignment protocol #33

## [0.7.0] - 2018-01-19
### Fixed
  - Fix retry on error for message handlers #30

### Changed
  - Use decoder offset for validating response length #21
  - Change log creator to improve interoperability #24
  - Add support to `KAFKAJS_LOG_LEVEL` #24
  - Improved assigner protocol #27 #29

### Added
  - Add seek API to consumer #23
  - Add experimental describe group to consumer #31

## [0.6.8] - 2017-12-27
### Fixed
  - Only use seed brokers to bootstrap consumers (introduced a broker pool abstraction) #19
  - Don't include the size of the size field when determining if the buffer has enough bytes to read the full response #20

## [0.6.7] - 2017-12-18
### Fixed
  - Don't throw KafkaJSOffsetOutOfRange on every protocol error

## [0.6.6] - 2017-12-15
### Fixed
  - Fix index out of range errors when decoding partial messages #11
  - Don't rely on seed broker for finding group coordinator #13

## [0.6.5] - 2017-12-14
### Fixed
  - Fix partial message decode #10
  - Throw not implemented error for Snappy and LZ4 compression #10
  - Don't crash when setting offsets to default #10

## [0.6.4] - 2017-12-13
### Added
  - Add stack trace to connection error logs

### Changed
  - Skip consumer callback error logs for kafkajs errors

### Fixed
  - Use the connection timeout callback for socket timeout
  - Check if still connected before writing to the socket

## [0.6.3] - 2017-12-11
### Added
  - Add error logs for user errors in `eachMessage` and `eachBatch`

### Fixed
  - Recover from rebalance in progress when starting the consumer

## [0.6.2] - 2017-12-11
### Added
  - Add `logger: "kafkajs"` to log lines

## [0.6.1] - 2017-12-08
### Added
  - Add latest Kafka error codes

### Fixed
  - Add fallback error for unsupported error codes

## [0.6.0] - 2017-12-07
### Added
  - Expose consumer group `isRunning` to `eachBatch`
  - Add `offsetLag` to consumer batch

## [0.5.0] - 2017-12-04
### Added
  - Add ability to subscribe to events (heartbeats and offsets commit) #4

## [0.4.1] - 2017-11-30
### Changed
  - Add heartbeat after each message
  - Update default heartbeat interval to a better value

### Fixed
  - Accept all consumer properties from create consumer

## [0.4.0] - 2017-11-23
### Added
  - Commit previously resolved offsets when `eachBatch` throws an error
  - Commit previously resolved offsets when `eachMessage` throws an error
  - Consumer group recover from offset out of range

## [0.3.2] - 2017-11-23
### Fixed
  - Stop consuming messages when the consumer group is not running

## [0.3.1] - 2017-11-20
### Fixed
  - NPM bundle (add .npmignore)
  - Fix package.json reference to main file

## [0.3.0] - 2017-11-20
### Added
  - Add cluster method to fetch offsets for a list of topics
  - Add offset resolution to the consumer group

### Changed
  - Rename protocol Offsets to ListOffsets
  - Update cluster fetch topics offset to allow different configurations per topic
  - Create different instances of the cluster for producers and consumers

### Fixed
  - Fix the use of timestamp in the ListOffsets protocol
  - Fix create topic script
  - Prevent unnecessary reconnections on cluster connect

## [0.2.0] - 2017-11-13
### Added
  - Expose consumer groups
  - Message and MessageSet V0 and V1 decoder
  - Protocol fetch V0, V1, V2 and V3
  - Protocol find coordinator V0
  - Protocol join group V0
  - Protocol sync group V0
  - Protocol leave group V0
  - Protocol offsets V0
  - Protocol offset commit V0, V1 and V2
  - Protocol offset fetch V1 and V2
  - Protocol heartbeat V0
  - Support to compressed message sets in protocol fetch
  - Add find coordinator group to cluster
  - Set timestamp for compressed messages
  - Travis integration
  - Eslint and prettier

### Changed
  - Throw an error when cluster findBroker doesn't find a broker
  - Move `KafkaProtocolError` to errors file
  - Convert encode, decode and parse to async functions
  - Update producer to use async compressor
  - Update fetch to use async decompressor
  - Create a separate error class for SASL errors
  - Accepts a list of brokers instead of host and port
  - Move retry logic out of connection and create namespaces for the logger
  - Retry when refresh metadata throws leader not available

### Fixed
  - Fix broker maxWaitTime default value
  - Take OS differences when asserting gzip results
  - Clear the connection timeout when the connection ends or fails due to an error

## [0.1.2] - 2017-10-17
### Added
  - Expose if the cluster is connected

### Fixed
  - Reconnect the cluster if it is not connected when producing messages
  - Throw error if metadata is still not loaded when finding the topic partition
  - Refresh metadata in case it is not loaded
  - Make connection throw a retriable error when not connected

## [0.1.1] - 2017-10-16
### Changed
  - Only retry retriable errors
  - Propagate clientId and connectionTimeout to Cluster

### Fixed
  - Typo when loading the SASL Handshake protocol

## [0.1.0] - 2017-10-15
### Added
  - Producer compatible with Kafka 0.10.x
  - GZIP compression
  - Plain, SSL and SASL_SSL implementations
  - Published on Github
