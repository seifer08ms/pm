# Particulate matter projects: PM 2.5 and BC (Black Carbon)
  - Requirements: 
    - Conda (https://conda.io/docs/index.html)
  	- PostGRES/PostGIS (https://www.enterprisedb.com/)
  	- All the scripts are set to run on a Windows OS, if you are planning to run them on a different OS
  	  make sure that all the data and software path are correct.
  	- Create a folder that holds all the shapefile dataset.
  	- The shapefile dataset must be projected in the   

# PM 2.5 Korea:
0. **pm.sql**
	- Follow the instrcution within the sql
1. **pmkorea.sql**
	- Follow the instrcution within the sql

# BC New England:

0. **shape_proj.py**
	- Reproject all the shapefile in the data folder to [NAD83 / Conus Albers ( https://epsg.io/5070# )]
1. **import_csv.py**
	- Covert a csv file (exampledata.csv) to a shapefile (addresses.shp), and store it in the same data folder.
	- Change projection to the shapefile using ogr2ogr command line, and create a new shapefile ("_addresses.shp").
2. **raster_to_point_value.py**
	- Import the raster values to the shapefile ("_addresses.shp").
3. **createdb.py**
	- Create a new DB, and add the PostGIS extension.
	- The coordinate system required 5070 is already into PostGRES/PostGIS [NAD83 / Conus Albers ( https://epsg.io/5070# )].
4. **shape_to_postgis.py**
	- Import all the shapefile to PostGIS:
		- Make sure all the shapefile are stored in the same folder.
		- The name of the shapefile will be the name of the table, rename the shapefile if need it.
		- Make sure they all have the same coordinate system, by default should be (NAD83 / Conus Albers).
		- Force 2D
		- Create a spatial index for all tables.
5. **bc_newengland_2.sql**
	- Run all sql statement to perform the data analysis.	




