## WKT用途和含义
- wkt是Well Known Text,也是一种标记语言,用于表示地图上的矢量几何对象、空间对象的空间参考系统以及空间参考系统之间的转换。WKB是wkt的二进制形式,一般数据库存几何对象都用的wkb
### 几何要素
- 可以用WKT表示的几何对象有:点、线、多边形、三角形和多面体。多个几何图形可用于在单个对象中表示同一尺寸的多个几何图形，不同尺寸的几何图形可存储在一个几何图形集合中。
- 几何图形的坐标可以是2D (x，y)，三维(x，y，z)，4D (x，y，z，m)，m值是线性参考系统的一部分，或者2D具有m值(x，y，m)。三维几何图形在几何图形类型后用Z表示，线性参考系统的几何图形在几何图形类型后用M表示。不包含坐标的空几何图形可以通过在类型名称后使用符号Empty来指定。
- WKT几何在整个OGC规范中使用，并出现在实施这些规范的应用中。例如，邮政地理信息系统包含的功能可以将几何图形转换成WKT表示，并使其可读。
- 这里仅举几个例子:
-
  * 几何要素表示:
	- ``` bash
	    POINT(6 10)
	    LINESTRING(3 4,10 50,20 25)
	    POLYGON((1 1,5 1,5 5,1 5,1 1),(2 2, 3 2, 3 3, 2 3,2 2))
	    MULTIPOINT((3.5 5.6),(4.8 10.5))
	    MULTILINESTRING((3 4,10 50,20 25),(-5 -8,-10 -8,-15 -4))
	    MULTIPOLYGON(((1 1,5 1,5 5,1 5,1 1),(2 2, 3 2, 3 3, 2 3,2 2)),((3 3,6 2,6 4,3 3)))
	    GEOMETRYCOLLECTION(POINT(4 6),LINESTRING(4 6,7 10))
	    POINT ZM (1 1 5 60)
	    POINT M (1 1 80)
	    POINT EMPTY
	    MULTIPOLYGON EMPTY
	  ```
### 空间参考
- [WKT 空间参考标准](http://docs.opengeospatial.org/is/18-010r7/18-010r7.html) 可以参照链接进行查看
- 空间参考系统的WKT字符串描述了空间对象的大地基准、大地水准面、坐标系和地图投影。
- ``` bash
   COMPD_CS["OSGB36 / British National Grid + ODN",
       PROJCS["OSGB 1936 / British National Grid",
           GEOGCS["OSGB 1936",
               DATUM["OSGB_1936",
                   SPHEROID["Airy 1830",6377563.396,299.3249646,AUTHORITY["EPSG","7001"]],
                   TOWGS84[375,-111,431,0,0,0,0],
                   AUTHORITY["EPSG","6277"]],
               PRIMEM["Greenwich",0,AUTHORITY["EPSG","8901"]],
               UNIT["DMSH",0.0174532925199433,AUTHORITY["EPSG","9108"]],
               AXIS["Lat",NORTH],
               AXIS["Long",EAST],
               AUTHORITY["EPSG","4277"]],
           PROJECTION["Transverse_Mercator"],
           PARAMETER["latitude_of_origin",49],
           PARAMETER["central_meridian",-2],
           PARAMETER["scale_factor",0.999601272],
           PARAMETER["false_easting",400000],
           PARAMETER["false_northing",-100000],
           UNIT["metre",1,AUTHORITY["EPSG","9001"]],
           AXIS["E",EAST],
           AXIS["N",NORTH],
           AUTHORITY["EPSG","27700"]],
       VERT_CS["Newlyn",
           VERT_DATUM["Ordnance Datum Newlyn",2005,AUTHORITY["EPSG","5101"]],
           UNIT["metre",1,AUTHORITY["EPSG","9001"]],
           AXIS["Up",UP],
           AUTHORITY["EPSG","5701"]],
       AUTHORITY["EPSG","7405"]]
  ```
### 坐标转换
- 定义了WKT格式来描述用于在两个不同的空间参考系统之间转换坐标的转换方法和参数。
- ``` bash
   PARAM_MT["Mercator_2SP",
       PARAMETER["semi_major",6370997.0],
       PARAMETER["semi_minor",6370997.0],
       PARAMETER["central_meridian",180.0],
       PARAMETER["false_easting",-500000.0],
       PARAMETER["false_northing",-1000000.0],
       PARAMETER["standard parallel 1",60.0]]
   PARAM_MT["Affine",
       PARAMETER["num_row",3],
       PARAMETER["num_col",3],
       PARAMETER["elt_0_1",1],
       PARAMETER["elt_0_2",2],
       PARAMETER["elt 1 2",3]]
  ```