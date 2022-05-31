# Installation

Install postgis

https://postgis.net/install/

drop extenstion:
https://www.postgresql.org/docs/current/sql-dropextension.html

# Get PostGIS Version
```sql
SELECT PostGIS_version();
```

# Create Table

http://postgis.net/workshops/postgis-intro/geometries.html

```sql
CREATE TABLE geometries2 (name varchar, geom geometry);
```

# Linestring

https://postgis.net/workshops/postgis-intro/3d.html

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

https://postgis.net/docs/ST_AsText.html

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

# Get Values of Points

Note ST_AsText does not work with ST_X... :

```sql
SELECT name, 
   ST_X(ST_PointN(
	  geom::geometry,
	  generate_series(1, ST_NPoints(geom))
   )) AS Long,  ST_Y(ST_PointN(
	  geom::geometry,
	  generate_series(1, ST_NPoints(geom))
   )) AS Lat, ST_Z(ST_PointN(
	  geom::geometry,
	  generate_series(1, ST_NPoints(geom))
   )) AS Alt, ST_M(ST_PointN(
	  geom::geometry,
	  generate_series(1, ST_NPoints(geom))
   )) AS TimeZone
					  
FROM geometries2
```

# Delete Entry
```sql
DELETE FROM public.geometries2
	WHERE name='A1';
```



