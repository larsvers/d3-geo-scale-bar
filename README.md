# d3-geo-scale-bar

Like [d3-axis](https://github.com/d3/d3-axis) but for maps, this module displays automatic scale bars for projected geospatial data.

Scale bars help viewers understand the geographic extent of maps. Printed maps, even those produced over a century ago, seldom lack them, yet scale bars are commonly missing from modern maps published on the internet. d3-geo-scale-bar makes it easy to add scale bars to maps created with [d3-geo](https://github.com/d3/d3-geo).

[See it in action](https://bl.ocks.org/HarryStevens/8c8d3a489aa1372e14b8084f94b32464).

## Installing

If you use NPM, `npm install d3-geo-scale-bar`. Otherwise, download the [latest release](https://github.com/HarryStevens/d3-geo-scale-bar/raw/master/build/d3-geo-scale-bar.zip). AMD, CommonJS, and vanilla environments are supported. In vanilla, a d3 global is exported:

```html
<script src="https://unpkg.com/d3-geo-scale-bar@0.1.0/build/d3-geo-scale-bar.min.js"></script>
<script>

var scaleBar = d3.geoScaleBar()
  .projection(d3GeoProjection)
  .fitSize([width, height], geoJsonObject);

d3.select("svg").append("g").call(scaleBar);

</script>
```

[Try d3-geo-scale-bar in your browser](https://npm.runkit.com/d3-geo-scale-bar).

## API Reference

<a name="geoScaleBar" href="#geoScaleBar">#</a> d3.<b>geoScaleBar</b>() [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L5 "Source")

Constructs a new scale bar generator.

<a name="_scaleBar" href="#_scaleBar">#</a> <i>scaleBar</i>(<i>context</i>) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L23 "Source")

Render the scale bar to the given *context*, which may be either a [selection](https://github.com/d3/d3-selection) of SVG containers (either SVG or G elements) or a corresponding [transition](https://github.com/d3/d3-transition). Configure the scale bar with [*scaleBar*.projection](#scaleBar_projection) and [*scaleBar*.fitSize](#scaleBar_fitSize) before rendering.

<a name="scaleBar_projection" href="#scaleBar_projection">#</a> <i>scaleBar</i>.<b>projection</b>([<i>projection</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L138 "Source")

If *projection* is specified, sets the [projection](https://github.com/d3/d3-geo#projections) and returns the scale bar. If *projection* is not specified, returns the current projection.

<a name="scaleBar_fitSize" href="#scaleBar_fitSize">#</a> <i>scaleBar</i>.<b>fitSize</b>(<i>size</i>, <i>object</i>) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L124 "Source")

A convenience method combining the setter functions of [*scaleBar*.extent](#scaleBar_extent) and [*scaleBar*.feature](#scaleBar_feature). The following two statements are equivalent:
```js
scaleBar.extent([width, height]).feature(object);
scaleBar.fitExtent([width, height], object);
```
<a name="scaleBar_extent" href="#scaleBar_extent">#</a> <i>scaleBar</i>.<b>extent</b>([<i>size</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L130 "Source")

If *size* is specified, sets the extent such that (1) the scale bar's default top-left corner aligns with the top-left corner of the projected geospatial data, and (2) you can position the scale bar vertically with [*scaleBar*.top](#scaleBar_top) and horizontally with [*scaleBar*.left](#scaleBar_left). If *size* is not specified, returns the current extent.

<a name="scaleBar_feature" href="#scaleBar_feature">#</a> <i>scaleBar</i>.<b>feature</b>([<i>object</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L134 "Source")

If *object<* is specified, passes the corresponding GeoJSON Feature or FeatureCollection to the scale bar to allow for calculation of mile and kilometer scales and for positioning of the scale bar on the projected geospatial data. If *object* is not specified, returns the current object.

<a name="scaleBar_kilometers" href="#scaleBar_kilometers">#</a> <i>scaleBar</i>.<b>kilometers</b>([<i>kilometers</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L142 "Source")

If *kilometers* is specifed, sets the number of kilometers of the scale bar. Defaults to the largest exponent of 10 that will fit on the map. If *kilometers* is not specified, returns the current number of kilometers of the scale bar.

<a name="scaleBar_kilometersRadius" href="#scaleBar_kilometersRadius">#</a> <i>scaleBar</i>.<b>kilometersRadius</b>([<i>kilometers</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L146 "Source")

If *kilometers* is specifed, sets the number of kilometers of the radius of the sphere on which the geospatial data is projected. Defaults to 6,371, [the radius of the Earth](https://www.google.com/search?q=radius+of+earth+in+kilometers). If *kilometers* is not specified, returns the current number of kilometers of the sphere's radius.

<a name="scaleBar_kilometersTickValues" href="#scaleBar_kilometersTickValues">#</a> <i>scaleBar</i>.<b>kilometersTickValues</b>([<i>values</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L150 "Source")

If a *values* array is specified, the specified values are used for ticks rather than using the scale bar’s automatic tick generator. Defaults to [0, kilometers / 4, kilometers / 2, kilometers]. If *values* is not specified, returns the current tick values.

<a name="scaleBar_miles" href="#scaleBar_miles">#</a> <i>scaleBar</i>.<b>miles</b>([<i>miles</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L154 "Source")

If *miles* is specified, sets the number of miles of the scale bar. Defaults to the largest exponent of 10 that will fit on the map. If *miles* is not specified, returns the current number of miles of the scale bar.

<a name="scaleBar_milesRadius" href="#scaleBar_milesRadius">#</a> <i>scaleBar</i>.<b>milesRadius</b>([<i>miles</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L158 "Source")

If *miles* is specified, sets the number of miles of the radius of the sphere on which the geospatial data is projected. Defaults to 3,959, [the radius of the Earth](https://www.google.com/search?q=radius+of+earth+in+miles). If *miles* is not specified, returns the current number of miles of the sphere's radius.

<a name="scaleBar_milesTickValues" href="#scaleBar_milesTickValues">#</a> <i>scaleBar</i>.<b>milesTickValues</b>([<i>values</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L162 "Source")

If a *values* array is specified, the specified values are used for ticks rather than using the scale bar’s automatic tick generator. Defaults to [0, miles / 4, miles / 2, miles]. If *values* is not specified, returns the current tick values.

<a name="scaleBar_height" href="#scaleBar_height">#</a> <i>scaleBar</i>.<b>height</b>([<i>height</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L166 "Source")

If *height* is specified, sets the height of the scale bar in pixels. Defaults to 4. If *height* is not specified, returns the current height of the scale bar.

<a name="scaleBar_left" href="#scaleBar_left">#</a> <i>scaleBar</i>.<b>left</b>([<i>left</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L170 "Source")

If *left* is specified, sets the left position to the specified value which must be in the range [0, 1], where 0 is the left-most side of the projected geospatial data and 1 is the right-most. If *left* is not specified, returns the current left position which defaults to 0.

<a name="scaleBar_top" href="#scaleBar_top">#</a> <i>scaleBar</i>.<b>top</b>([<i>top</i>]) [<>](https://github.com/HarryStevens/d3-geo-scale-bar/blob/master/src/geoScaleBar.js#L174 "Source")

If *top* is specified, sets the top position to the specified value which must be in the range [0, 1], where 0 is the top-most side of the projected geospatial data and 1 is the bottom-most. If *top* is not specified, returns the current top position which defaults to 0.