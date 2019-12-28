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

## [Photon](./Examples/Geocoding/Photon/README.md)

Result:
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

## [Pelias](./Examples/Geocoding/Pelias/README.md)

Result:
```json
{
    "geocoding": {
        "version": "0.2",
        "attribution": "http://over.wemap.vn:3100/attribution",
        "query": {
            "text": "cau giay",
            "size": 10,
            "layers": [
                "venue",
                "street",
                "country",
                "macroregion",
                "region",
                "county",
                "localadmin",
                "locality",
                "borough",
                "neighbourhood",
                "continent",
                "empire",
                "dependency",
                "macrocounty",
                "macrohood",
                "microhood",
                "disputed",
                "postalcode",
                "ocean",
                "marinearea"
            ],
            "private": false,
            "focus.point.lat": 48.8625,
            "focus.point.lon": 2.359,
            "lang": {
                "name": "Vietnamese",
                "iso6391": "vi",
                "iso6393": "vie",
                "defaulted": false
            },
            "querySize": 20,
            "parser": "libpostal",
            "parsed_text": {
                "county": "cau giay"
            }
        },
        "warnings": [
            "performance optimization: excluding 'address' layer",
            "Invalid Parameter: key"
        ],
        "engine": {
            "name": "Pelias",
            "author": "Mapzen",
            "version": "1.0"
        },
        "timestamp": 1577518423805
    },
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    105.788482,
                    21.029632
                ]
            },
            "properties": {
                "id": "1108780793",
                "gid": "whosonfirst:county:1108780793",
                "layer": "county",
                "source": "whosonfirst",
                "source_id": "1108780793",
                "name": "Cau Giay",
                "confidence": 1,
                "match_type": "exact",
                "distance": 9202.358,
                "accuracy": "centroid",
                "country": "Việt Nam",
                "country_gid": "whosonfirst:country:85632763",
                "country_a": "VNM",
                "region": "Ha Tay",
                "region_gid": "whosonfirst:region:85680653",
                "region_a": "HI",
                "county": "Cau Giay",
                "county_gid": "whosonfirst:county:1108780793",
                "continent": "Châu Á",
                "continent_gid": "whosonfirst:continent:102191569",
                "label": "Cau Giay, Việt Nam"
            },
            "bbox": [
                105.760935988,
                20.9983256584,
                105.808189102,
                21.0575505015
            ]
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    105.80073,
                    21.03228
                ]
            },
            "properties": {
                "id": "1326949247",
                "gid": "whosonfirst:locality:1326949247",
                "layer": "locality",
                "source": "whosonfirst",
                "source_id": "1326949247",
                "name": "Cầu Giấy",
                "confidence": 0.6,
                "match_type": "fallback",
                "distance": 9202.954,
                "accuracy": "centroid",
                "country": "Việt Nam",
                "country_gid": "whosonfirst:country:85632763",
                "country_a": "VNM",
                "region": "Ha Tay",
                "region_gid": "whosonfirst:region:85680653",
                "region_a": "HI",
                "county": "Cau Giay",
                "county_gid": "whosonfirst:county:1108780793",
                "locality": "Cầu Giấy",
                "locality_gid": "whosonfirst:locality:1326949247",
                "continent": "Châu Á",
                "continent_gid": "whosonfirst:continent:102191569",
                "label": "Cầu Giấy, Việt Nam"
            },
            "bbox": [
                105.80073,
                21.03228,
                105.80073,
                21.03228
            ]
        }
    ],
    "bbox": [
        105.760935988,
        20.9983256584,
        105.808189102,
        21.0575505015
    ]
}
```


# Routing

## [OSRM_Leaflet](./Examples/Routing/OSRM_Leaflet/README.md)

## [OSRM_Mapbox](./Examples/Routing/OSRM_Mapbox/README.md)