# Pelias: Finding places

Geocoding is the process of matching an address or other text to its corresponding geographic coordinates.

All Pelias requests share the same format:

```
   https://apis.wemap.asia/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay
   \____/  \_____________/\________/\_____/ \__________________________/ \_____________/
     |            |          /         |                 |                      |
  scheme       domain   version      path               key                   query
```

## Set the number of results returned

By default, Pelias returns up to 10 results. If you want a different number, set the `size` parameter to the desired number. This example shows returning only the first result.

| parameter | value |
| :--- | :--- |
| `text` | YMCA |
| `size` | 1 |

> [/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay&__size=1__](https://apis.wemap.asia/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay&__size=1__)

If you want 25 results, you can build the query where `size` is 25.

> [/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay&__size=25__](https://apis.wemap.asia/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay&__size=25__)

## Prioritize results by proximity
Many use cases call for the ability to promote nearby results to the top of the list, while still allowing important matches from farther away to be visible. Pelias allows you to prioritize results within geographic boundaries, including around a point, within a country, or within a region.

### Prioritize around a point

![Searching around a point](/images/focus_point.png)

By specifying a `focus.point`, results will be sorted in part by their proximity to the given coordinate. All else being equal, results closes to the point will show up higher. However, unlike a `boundary.circle` query, important results far from the given coordinate may still be returned. This allows, for example, [a query for places called Paris with a `focus.point` value in Texas to return both Paris, TX and Paris, France](http://pelias.github.io/compare/#/v1/autocomplete%3Ffocus.point.lat=33.7568&focus.point.lon=-95.5362&layers=locality&sources=wof&text=paris).

To find YMCAs again, but this time near a specific coordinate location (representing the Sydney Opera House) in Sydney, Australia, use `focus.point`.

> [/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay&focus.point.lat=105.5](https://apis.wemap.asia/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay&focus.point.lat=105.5&focus.point.lon=21.5)

| parameter | value |
| :--- | :--- |
| `text` | cau giay |
| `focus.point.lat` | 105.5 |
| `focus.point.lon` | 21.5 |

Looking at the results, you can see that the few locations closer to this location show up at the top of the list, sorted by distance. You also still get back a significant amount of remote locations, for a well balanced mix. Because you provided a focus point, Pelias can compute distance from that point for each resulting feature.

## Combine boundary search and prioritization

Now that you have seen how to use boundary and focus to narrow and sort your results, you can examine a few scenarios where they work well together.

## Filter your search

Pelias brings together data from multiple open sources and combines a variety of place types into a single database, allowing you options for selecting the dataset you want to search.

With Pelias, you can filter by:

* `sources`: the originating source of the data
* `layers`: the kind of place you want to find

### Filter by data source
The search examples so far have returned a mix of results from all the data sources available to Pelias. Here are the sources being searched:

| source | name | short name |
|---|---|---|
| [OpenStreetMap](http://www.openstreetmap.org/) | `openstreetmap` | `osm` |
| [OpenAddresses](http://openaddresses.io/) | `openaddresses` | `oa` |
| [Who's on First](https://whosonfirst.org) | `whosonfirst` | `wof` |
| [GeoNames](http://www.geonames.org/) | `geonames` | `gn` |

If you use the `sources` parameter, you can choose which of these data sources to include in your search. So if you're only interested in finding a YMCA in data from OpenAddresses, for example, you can build a query specifying that data source.

> [/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay&sources=oa](https://apis.wemap.asia/geocode-1/search?key=ZpIVSmYKNucNvxlHgRFRVBuj&text=cau%20giay&sources=oa)

| parameter | value |
| :--- | :--- |
| `text` | YMCA |
| `sources` | oa |

### Filter by data type
In Pelias, different types of results are given different `layer` values. This helps us differentiate, for example, an address from a point of interest from a country.

The Pelias layers are derived from the hierarchy created by the gazetteer [Who's on First](https://github.com/whosonfirst/whosonfirst-placetypes/blob/master/README.md) and can be used to help you filter for just the types of results you want.

Here's a list of the types of places you could find in the results, sorted by granularity:

|layer|description|
|----|----|
|`venue`|points of interest, businesses, things with walls|
|`address`|places with a street address|
|`street`|streets,roads,highways|
|`neighbourhood`|social communities, neighbourhoods|
|`borough`|a local administrative boundary, currently only used for New York City|
|`localadmin`|local administrative boundaries|
|`locality`|towns, hamlets, cities|
|`county`|official governmental area; usually bigger than a locality, almost always smaller than a region|
|`macrocounty`|a related group of counties. Mostly in Europe.|
|`region`|states and provinces|
|`macroregion`|a related group of regions. Mostly in Europe|
|`country`|places that issue passports, nations, nation-states|
|`coarse`|alias for simultaneously using all administrative layers (everything except `venue` and `address`)|
|`postalcode`|postal code used by mail services|

> [/v1/search?text=YMCA&__layers=venue,address__](https://pelias.github.io/compare/#/v1/search%3Flayers=venue,address&text=ymca)

| parameter | value |
| :--- | :--- |
| `text` | YMCA |
| `layers` | venue,address |

## Available search parameters

| Parameter | Type | Required | Default | Example |
| --- | --- | --- | --- | --- |
| `text` | string | yes | none | `Union Square` |
| `focus.point.lat` | floating point number | no | none | `48.581755` |
| `focus.point.lon` | floating point number | no | none | `7.745843` |
| `boundary.rect.min_lon` | floating point number | no | none | `139.2794` |
| `boundary.rect.max_lon` | floating point number | no | none | `140.1471` |
| `boundary.rect.min_lat` | floating point number | no | none | `35.53308` |
| `boundary.rect.max_lat` | floating point number | no | none | `35.81346` |
| `boundary.circle.lat` | floating point number | no | none | `43.818156` |
| `boundary.circle.lon` | floating point number | no | none | `-79.186484` |
| `boundary.circle.radius` | floating point number | no | 50 | `35` |
| `boundary.gid` | Pelias `gid` | no | none | `whosonfirst:locality:101748355` |
| `sources` | string | no | all sources: osm,oa,gn,wof | openstreetmap,wof |
| `layers` | string | no | all layers: address,venue,neighbourhood,locality,borough,localadmin,county,macrocounty,region,macroregion,country,coarse,postalcode | address,venue |
| `boundary.country` | string | no | none | 'GBR,FRA' |
| `size` | integer | no | 10 | 20 |
