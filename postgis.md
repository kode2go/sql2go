# Installation

# Get PostGIS Version
SELECT PostGIS_version();

# Create Table
CREATE TABLE geometries2 (name varchar, geom geometry);

# Add Values

INSERT INTO geometries2 VALUES
  ('A1', 'LINESTRING ZM (-84.44 33.634 800 1642028771463, -84.44 33.63508 1200 1642028794402)')


INSERT INTO geometries2 VALUES
  ('A2', 'LINESTRING ZM (-159.33333 21.98333 2200 1641943015000, -159.13333 22.24000 2800 1641943255000)')
  
# Read Values

SELECT name,ST_AsText(geom) FROM geometries2
