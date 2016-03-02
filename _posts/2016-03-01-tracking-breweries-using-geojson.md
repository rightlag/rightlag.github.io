---
layout:     post
title:      Tracking Breweries Using GeoJSON
date:       2016-03-01 15:09:00
summary:    Mapping breweries via GeoJSON formatted documents
categories: github geojson mapping
---

I recently read an [article](https://help.github.com/articles/mapping-geojson-files-on-github/) explaining that GitHub now supports mapping [GeoJSON](http://geojson.org/) files. Any repository containing a file with a `.geojson` or `.topojson` extension will render an [OpenStreetMap](http://www.openstreetmap.org/). So, since I like beer and have been to quite a few breweries, I decided to create a `.geojson` file with all of the breweries that I visited.

Here's an example of the JSON formatted data:

```json
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    -74.945533,
                    42.62758
                ]
            },
            "properties": {
                "title": "Brewery Ommegang",
                "marker-size": "medium",
                "marker-symbol": "beer"
            }
        }
    ]
}
```

The formatting is relatively simple. This will basically plot a marker given the longitude and latitude coordinates for the particular feature. You can also specify custom [markers](https://www.mapbox.com/maki/), and sure enough, there's an marker icon for beer!

Here's an example of what the output looks like:

[https://github.com/rightlag/beers/blob/master/breweries.geojson](https://github.com/rightlag/beers/blob/master/breweries.geojson)

This will be a neat project to continue with!
