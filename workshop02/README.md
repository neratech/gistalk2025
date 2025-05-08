# GIS Talk 2025

### Workshop 02
- creazione di uno foglio di lavoro (LibreOffice) denominato "__gistalk2025_w02.ods__"
- link [Comuni italiani](https://www.comuni-italiani.it/)
  - [Provincia di Brescia](https://www.comuni-italiani.it/017/index.html)
  - [Breno](https://www.comuni-italiani.it/017/028/clima.html)
  - [Cividate Camuno](https://www.comuni-italiani.it/017/055/clima.html)
  - [Esine](https://www.comuni-italiani.it/017/070/clima.html)
- [](https://gdal.org/en/stable/drivers/vector/csv.html)
- [Lat Lon Tools](https://plugins.qgis.org/plugins/latlontools/)
- [Zenodo](https://zenodo.org)
- Zenodo [download](https://zenodo.org/records/14288612/files/CollectionProbability&HazardMapsforSVLahars.tar.gz.zip?download=1)

### comuni
```
cd workshop02/data

ogrinfo -ro -al \
     -oo X_POSSIBLE_NAMES='lon*' \
     -oo Y_POSSIBLE_NAMES='lat*' \
     -oo KEEP_GEOM_COLUMNS=YES \
     comuni.csv

ogr2ogr -f GeoJSON \
     -oo X_POSSIBLE_NAMES='lon*' \
     -oo Y_POSSIBLE_NAMES='lat*' \
     -oo KEEP_GEOM_COLUMNS=YES \
     comuni.json comuni.csv 
```
### QGIS: conversione XY a geometria puntuale
```
# campo virtuale "lat" (floating)
string_to_array(replace(latlon, ',', '.'), ';')[0]
# campo virtuale "lon" (floating)
string_to_array(replace(latlon, ',', '.'), ';')[1]
```

### ESRI Ascii GRID
```
cd workshop02/data
ZIP_PATH=CollectionProbability_and_HazardMapsforSVLahars.tar.gz.zip

# 0.1 m (10 cm)
gdalinfo "/vsizip/${ZIP_PATH}/Prob_Tmax0.1m.asc" > Prob_Tmax0.1m.gdalinfo.txt

gdal_translate "/vsizip/${ZIP_PATH}/Prob_Tmax0.1m.asc" Prob_Tmax0.1m.gdalinfo.tif

# 20 m
gdalinfo "/vsizip/${ZIP_PATH}/Prob_Tmax20m.asc" > Prob_Tmax20m.gdalinfo.txt

gdal_translate "/vsizip/${ZIP_PATH}/Prob_Tmax20m.asc" Prob_Tmax20m.gdalinfo.tif
```