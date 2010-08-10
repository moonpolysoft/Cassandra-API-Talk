!SLIDE
# The Cassandra API #

!SLIDE
# Setup #

    @@@ Java
    TTransport tr = new TSocket("localhost", 
      9160);
    TProtocol proto = 
      new TBinaryProtocol(tr);
    Cassandra.Client client = 
      new Cassandra.Client(proto);
    tr.open();
    
!SLIDE
# Insert #

    @@@ Java
    long timestamp = System.currentTimeMillis();
    client.insert("Keyspace1",
        key_user_id,
        new ColumnPath("Standard1", null, 
          "name".getBytes("UTF-8")),
        "Chris Goffinet".getBytes("UTF-8"),
        timestamp,
        ConsistencyLevel.ONE);

!SLIDE
# Read Column #

    @@@ Java
    ColumnPath path = new ColumnPath("Standard1", 
      null, "name".getBytes("UTF-8"));
    System.out.println(client.get("Keyspace1", 
      key_user_id, path, ConsistencyLevel.ONE));
      
!SLIDE
# Read Rows #

    @@@ Java
    SlicePredicate predicate = 
      new SlicePredicate(null, 
        new SliceRange(new byte[0], 
          new byte[0], false, 10));
    ColumnParent parent = new ColumnParent(
      "Standard1", null);
    List<ColumnOrSuperColumn> results = 
      client.get_slice("Keyspace1", key_user_id, 
      parent, predicate, ConsistencyLevel.ONE);
      
!SLIDE
# Read Rows (cont) #

    @@@ Java
    for (ColumnOrSuperColumn result : results)
    {
      Column column = result.column;
      System.out.println(new String(column.name, 
        "UTF-8") + " -> " + 
        new String(column.value, "UTF-8"));
    }
    
!SLIDE bullets incremental
# Design Principals #

* Lowest common denominator.
* Tightly coupled to implementation.
* Completely punts on connection handling.

!SLIDE bullets incremental
# 3rd Party Clients #

* All clients implement different connection strategies.
* Many dead clients.
* Abstractions all tend to be use case specific.

!SLIDE center

![Coda Hale](codahale.jpg)
## "The Cassandra API actively hides the capabilities of the database." - Coda Hale ##

!SLIDE
# Scromium solves my problem. #

!SLIDE
# Did not solve Coda's problem. #

!SLIDE bullets
# Hence, Cassie. #

* http://github.com/codahale/cassie

!SLIDE
# Yet another dead client. #
