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
https://apis.wemap.asia/geocode-3/api?key=ZpIVSmYKNucNvxlHgRFRVBuj&q=cau%20giay&lon=21.5&lat=105.5&location_bias_scale=2
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
        },
        {
            "geometry": {
                "coordinates": [
                    105.79790917480739,
                    21.03877435
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 420754269,
                "osm_type": "W",
                "extent": [
                    105.7978295,
                    21.0389481,
                    105.7981526,
                    21.0386236
                ],
                "country": "Việt Nam",
                "osm_key": "leisure",
                "city": "Hà Nội",
                "osm_value": "park",
                "postcode": "122000",
                "name": "Đài tưởng niệm Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    106.0489853,
                    10.6088978
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 529009465,
                "osm_type": "W",
                "extent": [
                    106.0489853,
                    10.6089826,
                    106.049811,
                    10.6088978
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Tân Thạnh",
                "osm_value": "residential",
                "name": "Cầu Giây",
                "state": "Tỉnh Long An"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.801387,
                    21.0301145
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 158829325,
                "osm_type": "W",
                "extent": [
                    105.8011393,
                    21.0302877,
                    105.801387,
                    21.0301145
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "primary",
                "postcode": "122000",
                "name": "Đường Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7997299,
                    21.0335281
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 156898453,
                "osm_type": "W",
                "extent": [
                    105.7989667,
                    21.0348078,
                    105.8002721,
                    21.0324555
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 132 Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7969673,
                    21.0305774
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 163053433,
                "osm_type": "W",
                "extent": [
                    105.7952963,
                    21.0323988,
                    105.7988794,
                    21.0282916
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 155 - Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7971532,
                    21.0322005
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 195070972,
                "osm_type": "W",
                "extent": [
                    105.7960693,
                    21.0327359,
                    105.7985224,
                    21.030653
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 165 Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7972384,
                    21.0334233
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 683890146,
                "osm_type": "W",
                "extent": [
                    105.7972384,
                    21.03367,
                    105.7975156,
                    21.0334233
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 209 Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7992241,
                    21.032211
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 684061192,
                "osm_type": "W",
                "extent": [
                    105.7992241,
                    21.0326378,
                    105.799794,
                    21.032211
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 118 Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7998031,
                    21.0316512
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 684084659,
                "osm_type": "W",
                "extent": [
                    105.7998031,
                    21.0321452,
                    105.8003333,
                    21.0316512
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 106 Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7997372,
                    21.0308789
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 163053422,
                "osm_type": "W",
                "extent": [
                    105.799402,
                    21.0310722,
                    105.8002682,
                    21.0306887
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 93 Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7955774,
                    21.0308128
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 570594285,
                "osm_type": "W",
                "extent": [
                    105.7948157,
                    21.0309894,
                    105.7960693,
                    21.030653
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 165 - Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.80165354278921,
                    21.029964800000002
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 221297387,
                "osm_type": "W",
                "extent": [
                    105.8014028,
                    21.0302015,
                    105.8019046,
                    21.0297348
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "primary",
                "postcode": "+842435373535",
                "name": "Vòng xoay Cầu Giấy"
            }
        },
        {
            "geometry": {
                "coordinates": [
                    105.7973313,
                    21.0331296
                ],
                "type": "Point"
            },
            "type": "Feature",
            "properties": {
                "osm_id": 601865063,
                "osm_type": "W",
                "extent": [
                    105.7967225,
                    21.0334281,
                    105.7977773,
                    21.0329869
                ],
                "country": "Việt Nam",
                "osm_key": "highway",
                "city": "Hà Nội",
                "osm_value": "residential",
                "postcode": "122000",
                "name": "Ngõ 201 Cầu Giấy"
            }
        }
    ],
    "type": "FeatureCollection"
}
```