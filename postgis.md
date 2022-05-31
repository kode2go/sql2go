# Installation

# Get PostGIS Version
```sql
SELECT PostGIS_version();
```

# Create Table
```sql
CREATE TABLE geometries2 (name varchar, geom geometry);
```

# Add Values

```sql
INSERT INTO geometries2 VALUES
  ('A1', 'LINESTRING ZM (-84.44 33.634 800 1642028771463, -84.44 33.63508 1200 1642028794402)')
```

```sql
INSERT INTO geometries2 VALUES
  ('A2', 'LINESTRING ZM (-159.33333 21.98333 2200 1641943015000, -159.13333 22.24000 2800 1641943255000)')
```

# Read Values

```sql
SELECT name,ST_AsText(geom) FROM geometries2
```

# Get Points
```sql
SELECT ST_AsText(
   ST_PointN(
	  column1,
	  generate_series(1, ST_NPoints(column1))
   ))
FROM ( VALUES ('LINESTRING(0 0, 1 1, 2 2)'::geometry) ) AS foo;
```



