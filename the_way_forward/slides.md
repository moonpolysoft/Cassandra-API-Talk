!SLIDE
# An inflection point. #

!SLIDE
# Is Cassandra a tool for data processing? #

!SLIDE
# Or a MySQL replacement? #

!SLIDE
# Client disarray hurts the community. #

!SLIDE
# Fundamentally redo the API. #

!SLIDE bullets incremental
# First class Java client #

* Data locality aware.
* Exposes a useful API.
* Designed for high throughput.
* Real map-reduce support.

!SLIDE
# Java interface is a foundation. #

!SLIDE
# Build other interfaces on the Java client. #

!SLIDE bullets incremental
# REST Interface #

* Design it for frontend code.
* Should do content negotiation.
* Separate daemon.

!SLIDE code
    GET /Keyspace/ColumnFamily/row/
        super_column/column
    Accept: application/json

    X-Timestamp: 80085
    {
      "name" : "column",
      "value" : "balls"
    }

!SLIDE bullets incremental
# RPC Interface (Thrift/Avro/*) #

* Simple verbs.
* Use base data types.
* Don't be clever.
* Separate daemon.
