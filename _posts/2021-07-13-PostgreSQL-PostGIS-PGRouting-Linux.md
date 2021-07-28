Hi, this time I want to  give you instructions for installing all dependencies for geospatial database. 
In these instructions we will install postgreSQL, postGIS, and also pgrouting.

## Installing PostgreSQL
PostgreSQL is open-source relational databases systems that has amazing extensions for geospatial data like PostGIS and PGRouting.
To download and install PostgreSQL (I'm using Ubuntu 20.04):
```
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install postgresql
sudo apt-get -y install postgresql-server-dev-13
```
This will install latest version of postgreSQL (version 13)
To install pgadmin4 (GUI):
```
sudo apt-get install pgadmin4
```
Try logging in to database
```
sudo -i -u postgres (password using system pass)
psql
```
## Installing PostGIS
PostGIS is an extension for PostgreSQL database. It adds support for geographic objects allowing location queries to be run in SQL.
```
sudo apt install postgis postgresql-13-postgis-3
sudo -i -u postgres
```
Create user and database
```
createuser test_postgis
createdb postgisdb -0 test_postgis
```
Log in to database and enable PostGIS, also checking the version
```
psql -d postgisdb
CREATE EXTENSION postgis;
SELECT PostGIS_version();
```
## Installing PGRouting
PGRouting is an extension for PostgreSQL and PostGIS that allows you to provide geospatial routing functions.
Install the latest version:
```
wget -O pgrouting-3.1.3.tar.gz https://github.com/pgRouting/pgrouting/archive/v3.1.3.tar.gz
```
Untar and install:
```
tar xvfz pgrouting-3.1.3.tar.gz
cd pgrouting-3.1.3
mkdir build
cd build
cmake  ..
make
sudo make install
```
To create database with enabling postgis and pgrouting:
createdb routing
```
sudo -i -u postgres
psql routing -c 'CREATE EXTENSION PostGIS'
psql routing -c 'CREATE EXTENSION pgRouting'
```

