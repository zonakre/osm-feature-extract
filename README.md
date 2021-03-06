# osm-feature-extract [![Build Status](https://travis-ci.org/lukasmartinelli/osm-feature-extract.svg)](https://travis-ci.org/lukasmartinelli/osm-feature-extract) [![BSD-3 license](https://img.shields.io/badge/license-BSD--3-blue.svg)](https://tldrlegal.com/license/mit-license)

A [Tile Reduce](https://github.com/mapbox/tile-reduce) processor to extract GeoJSON features from the [OSM QA Tiles](osmlab.github.io/osm-qa-tiles/)
using [Mapbox GL feature filters](https://www.mapbox.com/mapbox-gl-style-spec/#types-filter).

## Run yourself

First install the required dependencies. You need a new Node version (`> 5`).

```bash
npm install
```

Now download the [Mapbox QA Tiles](https://www.mapbox.com/blog/osm-qa-tiles/).
You can either download the entire planet or a smaller country extract.

```bash
wget https://s3.amazonaws.com/mapbox/osm-qa-tiles/latest.country/liechtenstein.mbtiles.gz
gunzip liechtenstein.mbtiles.gz
```

Invoke the `index.js` file with the planet file and output GeoJSON file.

```bash
node index.js -m planet.mbtiles -o postbox.geojson \
    --filter '["all", ["==", "amenity", "post_box"], ["$type", "==", "Point"]]'
```
