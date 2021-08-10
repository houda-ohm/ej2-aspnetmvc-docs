# Bing Maps

Bing maps is a online map provider owned by Microsoft. As like OSM, it provides map tile images based on our requests and combines those images into a single one to display the map area.

## Adding Bing Maps

The Bing Maps can be rendered by setting the `LayerType` property as "**Bing**" and the key for the Bing Maps must be set in the [`Key`](../api/maps/layerSettingsModel/#key) property. The Bing Maps key can be obtained from [here](https://www.microsoft.com/en-us/maps/create-a-bing-maps-key).

{% aspTab template="maps/map-providers/bing", sourceFiles="bing.cs" %}

{% endaspTab %}

> Specify Bing map key in the `key` property.

## Types of Bing maps

Bing Maps provides different types of maps and it is supported in the Maps component.

* **Aerial** - Displays satellite images to highlight roads and major landmarks for easy identification.
* **AerialWithLabel** - Displays aerial map with labels for the continent, country, ocean, etc.
* **Road** - Displays the default map view of roads, buildings, and geography.
* **CanvasDark** - Displays dark version of the road maps.
* **CanvasLight** - Displays light version of the road maps.
* **CanvasGray** - Displays grayscale version of the road maps.

To render the light version of the road maps, set the `BingMapType` to `CanvasLight` as demonstrated in the following code sample.

{% aspTab template="maps/map-providers/bing", sourceFiles="bing.cs" %}

{% endaspTab %}

> Specify Bing maps key in the `key` property.

## Zooming and panning

Bing maps layer can be zoomed and panned. Zooming helps to get a closer look at a particular area on a map for in-depth analysis. Panning helps to move a map around to focus the targeted area.

{% aspTab template="maps/map-providers/bingzoom", sourceFiles="bingzoom.cs" %}

{% endaspTab %}

> Specify Bing map key in the `key` property.

## Adding markers and navigation line

Markers can be added to the layers of Bing maps by setting the corresponding location's coordinates of latitude and longitude using `MarkerSettings` property. Navigation lines can be added on top of an Bing maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the `NavigationLineSettings` property.

{% aspTab template="maps/map-providers/bingmarker", sourceFiles="bingmarker.cs" %}

{% endaspTab %}

> Specify Bing map key in the `Key` property.

## Sublayer

Any GeoJSON shape can be rendered as a sublayer on top of the Bing maps layer for highlighting a particular continent or country in Bing maps by adding another layer and specifying the [`type`](../api/maps/layerSettingsModel/#type) property of maps layer to "**SubLayer**".