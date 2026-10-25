---
name: postgis-geofence-architect
description: Designs geospatial tracking, geofencing queries, and spatial indexing using PostGIS and Uber H3 hexagonal spatial indexes without paid third-party APIs.
---

# GeoSpatial & GPS Fleet Tracking Architect

This skill directs the spatial schema modeling, boundary geofencing, and proximity queries for ride-hailing, fleet management, and delivery logistics using PostGIS and Uber H3.

## 1. Zero-Cost Spatial Architecture

- Operates purely within PostgreSQL (`CREATE EXTENSION postgis;`) and open-source H3 libraries without paid external geocoding APIs.
- Uses OpenStreetMap and Leaflet/MapLibre for frontend rendering.

## 2. Spatial Indexing & Proximity Queries

1. **Geometry vs Geography**:
   - Use `geography(Point, 4326)` for true spherical GPS coordinates (WGS 84) to compute accurate distances in meters (`ST_Distance`).
   - Use `geometry` with projected coordinate systems when performing high-speed 2D planar math.
   - Enforce GiST indexing (`CREATE INDEX idx_drivers_location ON drivers USING GIST(current_location);`).
2. **Uber H3 Hexagonal Binning**:
   - Convert GPS coordinates to H3 indexes (e.g. Resolution 8 or 9) to group drivers and orders into discrete spatial hexagons.
   - Run O(1) hexagonal neighbor lookups (`h3.gridDisk`) for sub-millisecond driver matching during surge traffic.

## 3. Real-Time Geofencing
- Check point-in-polygon inclusions (`ST_Contains(geofence_polygon, driver_point)`) for instant entry/exit trigger events.
