# hillshade.json


## What's this?

hillshade.json is a global hillshade layer in GeoJSON format, designed for use in world- and continent-level web maps.

![Demo image of rendered hillshade](docs/assets/demo.png?raw=true)

## What's it for?

A hillshade (or 'shaded relief') layer can indicate the broad topography of an area and serve as a nice base texture for a map. Conventionally, these layers are distributed as raster files however, and as such they typically have to be preprojected to align with other layers of the map.

hillshade.json offers a vectorised layer instead, which means it can be loaded and reprojected with libraries such as [d3-geo](https://github.com/d3/d3-geo).

## How does it work?

The file contains 3 GeoJSON features which represent shadows of different intensity and stack on top of each other.

The three layers are designed to be drawn on top of a base layer of land, eg from [world-atlas](https://www.npmjs.com/package/world-atlas). One way to generate a smooth texture is to give the layers a low opacity and apply `mix-blend-mode: multiply`. I like to give the bottom layer a lower opacity while emphasizing the peaks:

```scss
.land {
    fill: #eaeaea;
}

.shadows {

    fill: #eaeaea;
    mix-blend-mode: multiply;

    &.shadows--1 {
        fill-opacity: 0.2;
    }
    &.shadows--2 {
        fill-opacity: 0.3;
    }
    &.shadows--3 {
        fill-opacity: 0.4;
    }

}
```

## Sources

This vector hillshade was created from [Natural Earth's 1:50m shaded relief raster](https://www.naturalearthdata.com/downloads/50m-raster-data/50m-shaded-relief/). Shoutout to Gavin Kistner's [svg2geojson](https://github.com/Phrogz/svg2geojson) without which I couldn't have created the vector version!