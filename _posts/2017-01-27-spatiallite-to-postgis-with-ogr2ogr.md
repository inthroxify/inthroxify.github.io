---
layout: post
title: "Convert spatialite to postgis with ogr2ogr"
---

    > ogr2ogr --config PG_USE_COPY YES --config SQLITE_LIST_ALL_TABLES NO -lco GEOMETRY_NAME=geometry -lco SPATIAL_INDEX=YES -lco CREATE_SCHEMA=OFF -lco POSTGIS_VERSION=2.2 -lco DROP_TABLE=OFF -lco FID="gid" -f "PGDump" /vsistdout/ -lco SCHEMA=fooschema foofile.sqlite > foofile.sql
    > psql -h example.com database_name_here
    database_name_here=# \i foofile.sql

| Option | Description |
|=+=|
|PG_USE_COPY YES | copies are faster than inserts, but change to no to use the sql in non-psql imports. |
|SQLITE_LIST_ALL_TABLES NO | stop it from exporting all of the spatialite structure tables. only export "real" tables |
|GEOMETRY_NAME=geometry | name of the geometry column in the final table. same as shp2pgsql. |
|SPATIAL_INDEX=YES | make it build a needed gist index on geometry. same as shp2pgsql. |
|CREATE_SCHEMA=OFF | odds are your schema exists already. lets not break it. |
|POSTGIS_VERSION=2.2 | use the latest postgis version. |
|DROP_TABLE=OFF | table won't exist on an initial import. change to YES if the tables need to be replaced. |
|FID="gid" | change the primary key column name to "gid". same as shp2pgsql |
|-f "PGDump" /vsistdout/ | use the pgdump driver so that this even works, and make it output to stdout, which we capture below |
|SCHEMA=fooschema | name of the schema in the postgis database that the table should go into. don't use "public", otherwise upgrading postgis in the future will be your worst nightmare! |
|foofile.sqlite | source sqlite file |
|> foofile.sql | output sql file |
