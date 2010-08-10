!SLIDE
# The HBase API #

!SLIDE
# Setup #

    @@@ Java
    HBaseConfiguration config = 
      new HBaseConfiguration();

    HTable table = new HTable(config, 
      "myLittleHBaseTable");

!SLIDE
# Put #

    @@@ Java
    Put p = new Put(
      Bytes.toBytes("myLittleRow"));
    p.add(Bytes.toBytes("myLittleFamily"), 
      Bytes.toBytes("someQualifier"),
      Bytes.toBytes("Some Value"));
    table.put(p);
    
!SLIDE
# Get #

    @@@ Java
    Get g = new Get(
      Bytes.toBytes("myLittleRow"));
    Result r = table.get(g);
    byte [] value = r.getValue(
      Bytes.toBytes("myLittleFamily"),
      Bytes.toBytes("someQualifier"));

!SLIDE
# Scanning #

    @@@ Java
    Scan s = new Scan();
    s.addColumn(
      Bytes.toBytes("myLittleFamily"), 
      Bytes.toBytes("someQualifier"));
    ResultScanner scanner = 
      table.getScanner(s);

    for (Result rr : scanner) {
      System.out.println("Found row: " + rr);
    }
    
    scanner.close();

!SLIDE bullets incremental
# Design Principles #

* Table and command abstraction.
* Composable pieces.
* Consistent interfaces.

