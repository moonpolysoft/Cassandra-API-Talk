!SLIDE
#  Scromium #
## With a name like that, it better be good. ##

!SLIDE bullets incremental
# Design Goals #

* Provide a DSL for Cassandra access
* Abstract away from connection handling
* Abstract away from serialization/deserialization
* Provide a plugin mechanism for conn pool strategies

!SLIDE

# Get API #

!SLIDE
    @@@ Scala
    import scromium.serializers.Serializers.__

    val cassandra = Cassandra.start
    cassandra.keyspace("fuck") { ks =>
      implicit val c = ReadConsistency.One
  
      val column = ks.get("row","CF") % "c"!;
      val sub = ks.get("row","SCF") % "sc" % "c"!;
      val sup = ks.get("row","SCF") / "sc"!;
    }

