!SLIDE
# An inflection point. #

!SLIDE
# Is Cassandra a tool for data processing? #

!SLIDE
# Or a MySQL replacement? #

!SLIDE
# Client disarray hurts the community. #

!SLIDE bullets incremental
# First class Java client #

* Data locality aware.
* Exposes a useful API.
* Designed for high throughput.
* Real map-reduce support.

!SLIDE bullets incremental
# REST Interface #

* Designed for frontend code.
* Content negotiation.
* Written using Java client.

!SLIDE code

    Accept: application/json
    GET /Keyspace/ColumnFamily/row/
        super_column/column

    {
      "name" : "column",
      "value" : "balls",
      "timestamp" : 80085
    }

!SLIDE bullets incremental
# RPC Interface (Thrift/Avro/*) #

* Simple verbs.
* Use base data types.
* Don't be clever.

!SLIDE
# API is UI. #

!SLIDE bullets incremental
# Look to other databases. #

* Riak
* MongoDB
* CouchDB
* HBase

!SLIDE bullets incremental
# Treat Cassandra like a product. #

* Not a hobby.