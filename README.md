# Custom-tiles-and-conditional-coloring-on-Google-Map

Having started work on google maps recently the first challenge that I have encountered is to colour the Google's default tiles.
 
This blog discusses about creation of custom tiles on google maps and display it using the Google Map Javascript API. The API uses a MapType object to hold information about these map. A MapType is an interface that defines the display and usage of map tiles and the translation of coordinate systems from screen coordinates to world coordinates (on the map). Each MapType must contain a few methods to handle retrieval and release of tiles, and properties that define its visual behaviour.

You can also define your own map tiles using custom map types or modify the presentation of existing map types using Styled Maps. When providing custom map types, you will need to understand how to modify the map's Map Type Registry.

Here are several coordinate systems that the Google Maps API uses:
Latitude and Longitude values which refer a point on the world uniquely.
Tile coordinates which refer a specific tile on the map at the specific zoom level.


The Google Map API breaks up imagery at each zoom level into a set of map tiles. When a map scrolls to a new location, or to a new zoom level, the Maps API determines which tiles are needed using pixel coordinates, and translates those values into a set of tiles to retrieve. These tile coordinates are assigned using a scheme which makes it logically easy to determine which tile contains the imagery for any given point.

Tiles in Google Maps are numbered from the same origin as that for pixels. For Google's implementation of the Mercator projection, the origin tile is always at the northwest corner of the map, with x values increasing from west to east and y values increasing from north to south. Tiles are indexed using x,y coordinates from that origin. For example, at zoom level 2, when the earth is divided into 16 tiles, each tile can be referenced by a unique x,y pair. The calculation of the tile coordinates from the specified latitude-longitude value is derived from a formula which I would like to share with you:
	tilex = floor(((((longitude) + 180) / 360) * (2^zoom level)))

	tiley = floor(((1-(log(tan(latitude*((22/7)/180))+1.0/cos(latitude*((22/7)/180))) / (22/7))) * (2^zoom level) / 2.0))


