
# Web

## Adopt

  - [Play](https://www.playframework.com/)

## Trial

  - [http4s](http://http4s.org)/[circe](https://circe.github.io/circe)
    A purely functional web stack including HTTP server and client
    components, as well as JSON de/serialization. Developed and
    maintained by the [typelevel scala](http://typelevel.org)
    community. Suitable for backend services, the http4s stack is
    small in memory footprint, efficient and fast. A number of teams
    in Gilt have used it successfully and we think it is worth taking
    a closer look and assessing its suitability. Apidoc has recently
    added support for generating http4s/circe http client and json
    de/serialization code.

  - [doobie](https://github.com/tpolecat/doobie)
    A purely functional JDBC library for Scala, with a minimal and yet
    expressive and type safe API, that avoids the pitfalls of ORMs
    with higher levels of abstraction.

## Assess

  - [Akka HTTP](http://doc.akka.io/docs/akka/2.4.11/scala/http/)
    We think that for writing lean microservices without a web
    frontend Akka HTTP offers an interesting approach without all the
    (mostly not needed) baggage that Play brings. Its integration with
    Akka Stream and Akka Actors makes it the perfect fit for writing
    reactive, high-concurrent and resilient services.

## Hold

  - commons-service-core

  - Commons

    This library was conceived as a set of light clients and related
    domain objects intended to capture all the 'common' logic about
    the Gilt infrastructure. This made possible to focus on new
    business functionalities wout reinventing what (e.g.) a Sale was
    every time. However, with time a lot of new concerns have been
    added to the lib eroding its effectiveness.

    - The tech organization is strongly moving toward an api first
      approach where clients for a given service are defined and
      auto-generated using tools like Apidoc and/or Swagger. This is
      progressively making the idea of Commons client obsolete taking
      away one of the main reason of its existence.

    - We feel that shared code in a micro-services oriented
      architecture is an anti-pattern. In this kind of environment you
      are naturally incentivized to experiment with new things (new
      frameworks, new programming languages, etc.) eventually throwing
      away things if they don't turn out to be worth the effort. We
      found that introducing a 'Common' library deters innovation and
      discourage people to try new things; it imposes some
      technological choices right from the start. E.g: you know that
      you need to work with Scala (and not the latest version) or that
      you need a particular version of the Json
      marshalling/unmarshalling library.

    - The introduction of caching in Commons was a mistake. While at
      the time they were introduced they sounded as a good idea, now
      they are definitely in the way of completing our way to a fully
      elastic infrastructure. Everything that needs to know what a
      product is needs to start and house an humongous in-heap caches
      posing a significant burden on the GC, generating a lot of
      network traffic, slowing down the hosting application resulting
      in an overall degradation of reliability. HOLDing on Commons and
      on its internal caches will be a strong signal that people
      should try to do better instead on rely on a solution that is
      not scaling anymore.

    - More than once we got stuck in a dependency hell due to Commons
      importing some libraries that are in open conflict with some
      other libraries needed by other parts of the system (e.g. Play,
      Akka, etc.). This ended up getting in the way of an healthy
      update of the third part software we use introducing a dangerous
      situations where we are stuck with old and unsupported versions
      of critical infrastructure. Latest example of this thread is the
      inability to move to newest version of Scala (2.12.x) for
      anything that slightly depends on Commons given a conflict with
      its Json subsystem.

    - Slow acceptance of new versions (e.g. Commons 6 vs. Commons
      7). Once a goal of each Arch Board the acceptance ratio of new
      version of Commons are now passed under silence. At the time of
      the writing a significant portion of our infrastructure is still
      on Commons 6 despite version 7 has been released more than one
      year ago. This forces to maintain different branches of other
      libs: one for each version of Commons still out there.
