## Creating Spatial Database in PostgreSQL
In this tutorial we will use pgAdmin4 because the GUI is easy to understand. To create new database right click on server then click Create > Database

![image](https://user-images.githubusercontent.com/43196730/130584948-8e731fc0-bec4-4913-bcf1-9c35335148a8.png)

I name this database as poi

![image](https://user-images.githubusercontent.com/43196730/130585467-5bd2685d-324c-4ed7-a0b5-8327bcb30dc5.png)

Click on sql tools to use query on this database

![image](https://user-images.githubusercontent.com/43196730/130585892-28274f2c-8632-4c21-951f-c3ce2579e84b.png)

Type this to enable postgis on the database:
```
CREATE EXTENSION postgis;
```
Click run button or just press F5
To check if postgis is enabled you can use this:
```
SELECT postgis_full_version();
```
### Import Shapefile
You can use this to import shapefile into your database:
```
export PGPASSWORD=mydatabasepassword
ogr2ogr -f "PostgreSQL" PG:"dbname=poi user=postgres" -nlt PGEOMETRY /path/to/file.shp
```
You can view the table you just create on Schemas > Public > Tables
Right click and view data. You can view your entire table.

![image](https://user-images.githubusercontent.com/43196730/130587682-9dc64f67-2fbd-4bca-8cea-f25692fc43f8.png)
























