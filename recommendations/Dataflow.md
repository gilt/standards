# Stream Handling

## Assess

### Dataflow APIs

Systems which are designed to handle large (possibly infinite) streams of data, while considering stack space, memory size, and managing back-pressure (when a sink processes data more slowly than the source), are a valuable tool for any organisation that wants to process large amounts of data reliably.

All the Scala libraries/frameworks in this area are relatively new and immature (in particular, APIs are not expected to be stable), which is something to bear in mind if adopting one of these within your service.

The current front runners here are:
 - [Akka Streams (Scala and Java)](http://doc.akka.io/docs/akka-stream-and-http-experimental/1.0/)
 - [scalaz-stream (Scala)](https://github.com/scalaz/scalaz-stream)
