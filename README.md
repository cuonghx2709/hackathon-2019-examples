# Hackathon 2019 Examples
Phát triển ứng dụng dựa trên nền tảng Bản đồ số Việt Nam WeMap

# Bắt đầu

# Hiển thị

## Bản đồ Raster

### Raster Tiles API
```
https://apis.wemap.asia/raster-tiles/styles/osm-bright/{z}/{x}/{y}@2x.png?key=ZpIVSmYKNucNvxlHgRFRVBuj
```

### Thư viện cần dùng để hiển thị wemap-raster: [Leaflet-js](https://leafletjs.com/examples/quick-start/)



## Bản đồ Vector

### Vector Style API
```
https://apis.wemap.asia/vector-tiles/styles/osm-bright/style.json?key=ZpIVSmYKNucNvxlHgRFRVBuj
```

### Thư viện cần dùng để hiển thị wemap-vector: [Mapbox-gl-js](https://docs.mapbox.com/mapbox-gl-js/api/)


# Geocoding

## Search API

```
https://apis.wemap.asia/geocode-3/api?key=ZpIVSmYKNucNvxlHgRFRVBuj
```

### Search
```
https://apis.wemap.asia/geocode-3/api?key=ZpIVSmYKNucNvxlHgRFRVBuj&q=cau%20giay
```

### Search with Location Bias
```
https://apis.wemap.asia/geocode-3/api?key=ZpIVSmYKNucNvxlHgRFRVBuj&q=cau%20giay&lon=21.5&lat=105.5
```

Increase this bias (range is 0.1 to 10, default is 1.6)

```
https://apis.wemap.asia/geocode-3/api?key=ZpIVSmYKNucNvxlHgRFRVBuj&q=cau%20giay&location_bias_scale=2&lon=21.5&lat=105.5
```

### Reverse geocode a coordinate
```
https://apis.wemap.asia/we-tools/reverse?key=ZpIVSmYKNucNvxlHgRFRVBuj&lat=$lon=21.5&lat=105.5
```

### Adapt Number of Results
```
https://apis.wemap.asia/geocode-3/api?key=ZpIVSmYKNucNvxlHgRFRVBuj&q=cau%20giay&limit=2
```

### Filter results by [tags and values](http://taginfo.openstreetmap.org/projects/nominatim#tags) 
*Note: not all tags on [link in the title](http://taginfo.openstreetmap.org/projects/nominatim#tags) are supported. Please see [nominatim source](https://github.com/openstreetmap/osm2pgsql/blob/master/output-gazetteer.cpp#L81) for an accurate list.*
If one or many query parameters named ```osm_tag``` are present, photon will attempt to filter results by those tags. In general, here is the expected format (syntax) for the value of osm_tag request parameters.

1. Include places with tag: ```osm_tag=key:value```
2. Exclude places with tag: ```osm_tag=!key:value```
3. Include places with tag key: ```osm_tag=key```
4. Include places with tag value: ```osm_tag=:value```
5. Exclude places with tag key: ```osm_tag=!key```
6. Exclude places with tag value: ```osm_tag=:!value```

For example, to search for all places named ```berlin``` with tag of ```tourism=museum```, one should construct url as follows:
```
https://apis.wemap.asia/geocode-3/api?key=ZpIVSmYKNucNvxlHgRFRVBuj&q=cau%20giay&osm_tag=tourism:museum
```

Or, just by they key

```
https://apis.wemap.asia/geocode-3/api?key=ZpIVSmYKNucNvxlHgRFRVBuj&q=cau%20giay&osm_tag=tourism
```

### Results as GeoJSON
```json
{
    "features": [
        {
            "geometry": {
                "coordinates": [
                    105.79133320228829,
                    21.029727
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 9421132,
                "osm_type": "R",
                "extent": [
                    105.7677002,
                    21.0588951,
                    105.8134918,
                    21.0007401
                ],
                "country": "Việt Nam",
                "osm_key": "boundary",
                "city": "Hà Nội",
                "osm_value": "administrative",
                "name": "Quận Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7908549,
                    21.028299
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 4888779416,
                "osm_type": "N",
                "country": "Việt Nam",
                "osm_key": "leisure",
                "city": "Hà Nội",
                "osm_value": "park",
                "postcode": "122000",
                "name": "Công viên Cầu Giấy"
            }
        }
    ],
    "type": "FeatureCollection"
}
```