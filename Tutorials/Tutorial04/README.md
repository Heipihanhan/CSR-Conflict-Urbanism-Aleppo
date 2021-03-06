######CSR / Conflict Urbanism Aleppo
##Tutorial 4: Creating a Basic Interactive Web Map 

In this tutorial, you will be a making a basic interactive map of Aleppo, Syria through the use of *Open Source* GIS software, [QGIS](http://www.qgis.org/en/site/) and *Open Source* mapping platform for custom designed maps, [Mapbox](https://www.mapbox.com/). You will download *Neighborhood Level Data* and *Informal Settlements Data* from the [CSR](http://www.c4sr.columbia.edu/) Data Repository. You will build the *Neigborhood Level Map* in [Mapbox Studio](https://www.mapbox.com/mapbox-studio/) and the *Informal Settlements Map* in [Mapbox Classic](https://www.mapbox.com/mapbox-studio-classic/#darwin). You will then embed these interactive maps, individually in the case studies and also build a standalone two layer *Web Map*. 

### Tools:
For this tutorial, we will be using the following tools:
* [QGIS](http://www.qgis.org/en/site/)
* [Mapbox](https://www.mapbox.com/)
* HTML, CSS and Javascript 

### Datasets:
For this tutorial, we will be using the following datasets:
* Neighborhood.zip, Download [here](https://www.dropbox.com/s/ih38cxqov27fbdy/Neighborhood.zip?dl=0)
* Informal.zip, Download [here](https://www.dropbox.com/s/ffrfixgoctgf19z/informal.zip?dl=0)
* `Tutorial_4_1.html`, Download [here](https://www.dropbox.com/s/1rhuyoxxgcjsezl/Tutorial_4_1.html?dl=0)
* `Tutorial_4_2.html`, Download [here](https://www.dropbox.com/s/j9k9efjos67zmad/Tutorial_4_2.html?dl=0)

### Datasets Overview:
This section provides detailed explanation of each data source. You can skip this section, if you would like to continue with the tutorial. However, it is recommended that you familiarize yourself with these sources, as they will asssist you in your research.

##### Neighborhood Level Data:
*Neighborhood Level Data* is a dataset prepared by CSR. It uses the *Neighborhood Map* published in the [Aleppo City Profile Report](http://unhabitat.org/city-profile-aleppo-multi-sector-assessment/), pg.24 published by UN-Habitat, in May 2014. We digitized the map based on Google Earth satellite imagery, and added Arabic tranlations for the neighborhood names. In a case, where a neighborhood was divided in parts, we've used roman numerals. A neighborhood map was also developed by [UNITAR/UNOSAT](http://www.unitar.org/unosat/), in early 2015, which slightly varies from the one initially produced by [UN Habitat](http://unhabitat.org/).  

##### Informal Settlements Data:
*Informal Settlements Data* is a dataset prepared by CSR. It uses the *report* on *Informal Settlements Report* from [Madinatuna: Aleppo City Planning Strategy](http://madinatuna.com/en/informals). This report is the first output of the Informal Settlements sub-component of the Syrian German Programme for Sustainable Urban Development (UDP) in Aleppo, which was supported by GTZ, the German Agency for Technical Cooperation. GTZ has been engaged in Syria since 1994, supporting the “Rehabilitation of the Old City of Aleppo”. In 2007, on request of the Syrian Government, GTZ widened its approach to providing technical advice to the Municipality of Aleppo on formulating a City Development Strategy and dealing with informal settlements. The report identifies **28** Informal Settlements. We identified corresponding entries using our Neighborhood map and coded those Neigborhoods and *Informal*. 

### Creating a Basic Interactive Web Map

##### Steps:
  * 01. QGIS: SetUp Neighborhood and Informal Data 
  * 02. MAPBOX: Sign Up, Installation and Introduction 
  * 03. MAPBOX_Editor: Design Map of Informal Neighborhoods
  * 04. MAPBOX_Studio: Design Map of Neighborhoods
  * 05. WEB: Embed Neighborhood and Informal Maps in Case Study
  * 06. WEB: WEB: Set up Interactive Map

##### 01. QGIS: SetUp Neighborhood and Informal Data
**QGIS Project**
 * Open the `Neighborhood.shp` and `Informal.shp` file in QGIS, through `Layer > Add Layer > Add Vector Layer`
 * Look at the `attributes table` to see the available fields. Delete Uncessary fields to save space on mapbox

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12660491/f84ffeca-c5e1-11e5-9c0e-5ffd9d16e9b7.png)

*`Neighborhood.shp`:133 Neighborhoods
  * Id
  * Name
  * Name_A
  
*`Informal.shp`:15 Neighborhoods
  * Id
  * Name
  * Name_A
  * Informal
  
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12677127/c506caac-c664-11e5-8b6d-e1eeeb115e3d.png)

Export these as `geojson`, after setting Coordinate Reference System CRS 
Mapbox only allows *WGS 84/ Pseudo Mercator ([EPSG:3857](https://epsg.io/3857))* but you do not need to change from the default: *WGS 84 EPSG:4326* On upload, mapbox automatically configures the file to Mercator.

##### 02. MAPBOX: Sign Up, Installation and Introduction 
[**Mapbox**](www.mapbox.com) <br>
Mapbox is an open source mapping platform. Below we will look at the 3 different working environments it offers and some basic terminology.<br>

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12666482/6302c9f0-c60f-11e5-8e8f-d3c11283d3ae.png)

[Mapbox Editor](https://www.mapbox.com/editor/#style) <br>
is an online interface where you can choose a Mapbox classic style as a basemap, drag and drop features, and share your project. Editor requires no coding skills and can be easily integrated into a web template. You can import GeoJSON, CSV, KML, or GPX files into Mapbox Editor. You can also export data in GeoJSON or KML format.
<br>

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12666484/66c7e368-c60f-11e5-8cd9-47022b4494b0.png)

[Mapbox Studio Classic](https://www.mapbox.com/help/define-mapbox-studio-classic/) <br>
is a desktop application for designing world maps. It allows you to design maps by using [vector tiles](https://www.mapbox.com/help/define-vector-tiles/) and [CartoCSS](https://www.mapbox.com/help/define-cartocss/). Mapbox Studio Classic allows you to upload your map directly to your Mapbox account and then use your map style with our Developer tools. You can also use the map that you design in Mapbox Studio Classic as a baselayer in Mapbox Editor. You can import shapefiles, KML, GeoJSON, GPX, CSV, TIF, and VRT files into Mapbox Studio Classic. You can export Mapbox Studio Classic sources as MBTiles.
<br>

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12666485/66cc8bac-c60f-11e5-8588-1290bf068b36.png)

[Mapbox Studio](https://www.mapbox.com/mapbox-studio/) <br>
is an online application for designing world maps. It allows you to design maps with vector tiles and Mapbox GL. You can use your map style on the web with Mapbox GL JS and in your mobile apps with the iOS SDK. You can import MBTiles, KML, GPX, GeoJSON, Shapefiles (zipped), CSV, and GeoTIFF files into Mapbox Studio to create vector tiles for styling.
<br>

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12666481/63022e14-c60f-11e5-8792-2f651a648615.png)

Key Terms
* **API Key** <br>
To use any of Mapbox’s tools, APIs, or SDKs, you’ll need a Mapbox access token. Mapbox uses access tokens to associate requests to API resources with your account. There are two types of access tokens:<br>
**Public access tokens**: <br>
use a public access token in websites or applications where they can be easily rotated, like scripts on a web page.<br>
**Secret access tokens**: <br>
only use a secret access token in places where it’s difficult to rotate, like mobile apps which require an approval process. You should also use secret tokens when you need to set specific token parameters, like when using the Uploads API.
<br>

<p>For the purpose of this tutorial, you will have have a `Public API Key`</p>
```
c4sr API Key: https://api.mapbox.com/v4/mapbox.emerald/page.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A
```
* **Map ID** <br>
Any time you create a project with *Mapbox Editor*, upload a style with *Mapbox Studio Classic*, or upload data to your account on *Mapbox.com*, it will receive a `map ID`. The `map ID` allows you to reference that specific project, style, or data with a *Mapbox API* or SDK. This means you can create a custom map style in *Mapbox Studio Classic* and then use that map with your Mapbox.js project or upload a dataset and add it as a custom source in Mapbox Studio Classic. <br>
```
Your map ID will always start with your Mapbox username followed by your map’s unique handle: `username.handle`
```
There are three different types of `map IDs`:
* [Projects](https://www.mapbox.com/studio/classic/projects/) — projects are made with Mapbox Editor. Share your map from Mapbox Editor or use your project map ID with Mapbox APIs or SDKs.
* [Styles](https://www.mapbox.com/studio/classic/styles/) — styles are custom maps and styled data made with Mapbox Studio Classic. Use your style map ID with Mapbox APIs or import it into Mapbox Editor.
* [Data](https://www.mapbox.com/studio/data) — You can upload data or sources on Mapbox.com and from Mapbox Studio Classic. Add your data map ID as a custom source in Mapbox Studio Classic or update it with the Mapbox Upload API.

There are also some common `map IDs`, that you can use:
* *mapbox.streets*: Street Layer, OpenStreetMaps
* *mapbox.satellite*: Satellite Layer, Digital Globe
* *mapbox.high-contrast*: Stamen Design high Contrast Map

* **Baselayer** <br>
A `baselayer` often refers to the map style that you designed in [Mapbox Studio Classic](https://www.mapbox.com/help/define-mapbox-studio-classic/) or the [Mapbox classic styles](https://www.mapbox.com/maps/). The baselayer provides geographic context and serves as a starting point for your map.

* **Layers** <br>
`Layers` are used in GL styles to add styling rules to specific subsets of data. Layers contain both a reference to the data for which they’re defining a style as well as the styling rules to be applied.


##### 03. MAPBOX_Editor: Design Map of Informal Neighborhoods

Once you sign into mapbox, goto `New Mapbox Editor Project` to start designing your map:
* `Tab: Style`: <br>
By *Default* always select this as `transparent`. You can select a different layer, if you always want to have your *data* rendered with that particular style. We leave it *transparent* as their are easier ways to switch these in code. Next, click on the `data` tab.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12677124/c5015766-c664-11e5-9dae-bfca632726e8.png)

* `Tab: Data`:<br>
This is where you can **import** data and stylize your data. Bring in the `informal_map.geojson` file. It takes a few minutes to download the data, but if it takes too long, choose to work with mapbox studio instead. Once you bring in the file, it should appear seen below. If you don't see anything or a straightline, there might be an error with the projection setting. 
	+ Click on `import` and select `informal_map.geojson`
	+ `Import features` shows the data that mapbox reads and how it can be preset. 
	+ Select `NAME` for popup title and `NAME_A` for popup description.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12677128/c5077088-c664-11e5-9171-ee0e01cac009.png)

+ For each `polygon` in the map area, you can edit the *text*, *Stroke* and *Fill*. 
+ You can draw additional *polygons*, drop *markers* or add *lines*.
+ We will not edit the `text` 
+ For each polygon, set the following Stroke Settings:<br>
	+ Transparency: `1`
	+ Thickness: `1`
	+ Color: `#000000`
+ For each polygon, set the following Fill Settings:<br>
	+ Transparency: `0.4`
	+ Color: `#6c6c6c`

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12677129/c5082898-c664-11e5-8181-7816ddc6a6d3.png)

* `Tab: Project`:<br>
This is where you add a `Name` and `Description` to you project.
	+ Name: `Informal`
	+ Description: `Informal Settlements in Aleppo, 2009`

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12677126/c5055474-c664-11e5-9c5f-73a807a9666a.png)

* `Tab: Save` :<br>
After saving the project, mapbox provides the following:

+ Map ID: `c4sr.p10e979a`

+ Share:  
```
https://a.tiles.mapbox.com/v4/c4sr.p10e979a/page.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A#12/36.2351/37.220
```
+ Embed: iframe code to embed in any other site
```html
<iframe width='100%' height='500px' frameBorder='0' src='https://a.tiles.mapbox.com/v4/c4sr.p10e979a/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'></iframe>
```

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12677125/c50449c6-c664-11e5-88d1-9274b0c6d601.png)

Note: This is now saved in your projects on mapbox. Regardless of environment, you can always locate this project and re-edit it. It's Map ID would remain the same. So if you have a webmap live, it will be automatically updated. 

##### 04. MAPBOX_Studio: Design Neighborhood Map
It is important to note here why there are multiple versions of mapbox and understand which one you should use. First mapbox, like many other open source development platforms is constatntly under development. Mapbox Studio is built to replace mapbox classic which was we were using, when the platform was built. Their even earlier version `Tilemill` is still around and can be used, but we recommend using the three mapbox versions currently up. 

However, there's a considerable difference between Mapbox Editor and Mapbox Studio. Mapbox Editor let's you create simple interactive maps and add them to a browser, without much knowledge of code. It's a simple graphical interface. On the other hand Mapbox Classic/Studio, let's you work through multiple layers to create advanced maps. But to develop those as interactive maps on the web requires more knowledge of html, javascript and css. I recommened using the Editor when you have limited amount of data. In the editor, you have to individually style components, as opposed to Classic and Studio. Editor is also the way to go, if you don't want to go deeper in code. 

##### 05. WEB: Embed Neighborhood and Informal Maps

+ Embed: iframe code to embed in any other site
```html
<iframe width='100%' 
height='500px' 
frameBorder='0' 
src='https://a.tiles.mapbox.com/v4/c4sr.p10e979a/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'>
</iframe>
```

+ Embed: iframe code to embed in any other site
```html
<iframe width='100%' 
height='500px' 
frameBorder='0' 
src='https://a.tiles.mapbox.com/v4/c4sr.p10e979a/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'>
</iframe>
```

##### 06. WEB: Set up Interactive Map 

There are 2 parts to this. You can skip the *first* part. I have added it just to allow you to get familiar with *web mapping*. It is not a requirement to complete this tutorial. Part 1 focuses on simply showing a layer on your map.

**Basic Map Layout**

Once you have initiated a mapbox account, note down your mapbox access token. You can use the `Tutorial_4_1.html` file or copy/paste the below code in [sublime](http://www.sublimetext.com/) as HTML. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12675624/95c49cfc-c659-11e5-9771-26975860a408.png)

In order to make a map of Syria, you need to do the following:
* Add your mapbox access token: Ln:35 <br>
`C4SR: pk.eyJ1Ijoic2lkbCIsImEiOiJkOGM1ZDc0ZTc5NGY0ZGM4MmNkNWIyMmIzNDBkMmZkNiJ9.Qn36nbIqgMc4V0KEhb4iEw`
* Note Long, Lat of Syria: Ln:37 <br>
`Lat:  36.198, Long = 37.1518;`
* Test desired Zoom Level: Ln:37 <br>
`Zoom Level 13 seems to work well. You can adjust this as per your requirement.`

All these are to be changed in the following section, between the `script` tags:
```javascript
L.mapbox.accessToken = '<your access token here>';
var map = L.mapbox.map('map', 'mapbox.streets')
    .setView([40, -74.50], 9);
```

```html
<!--Tutorial: Setting a Base Map
	Conflict Urbanism: Aleppo
    Center for Spatial Research
================================================================= -->

<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />

<!-- Set your Project Name here -->
<title>Tutorial_4_1</title>

<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />

<!-- In order to set up the webmap, you need to link to mapbox.js and mapbox.css -->
<script src='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.js'></script>
<link href='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.css' rel='stylesheet' />

<!-- Style your map with changing the options below -->
<style>
  body { margin:0; padding:0; }
  #map { position:absolute; top:0; bottom:0; width:100%; }
</style>
</head>

<body>
<!-- Add the map to a div -->
<div id='map'></div>

<script>
// Add your access token here: 
L.mapbox.accessToken = 'pk.eyJ1Ijoic2lkbCIsImEiOiJkOGM1ZDc0ZTc5NGY0ZGM4MmNkNWIyMmIzNDBkMmZkNiJ9.Qn36nbIqgMc4V0KEhb4iEw';
// Add the layer you would like to use as your base layer. In this case we are using mapbox.satellite
var map = L.mapbox.map('map', 'mapbox.satellite')
// .setView([Lat, Long], Zoom)
    .setView([36.198, 37.1518], 13);
</script>

</body>
</html>
```

You can save the file as `Tutorial_4_1.html` and open it in Chrome. This is how it should appear:

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12675623/95ad91ce-c659-11e5-99b1-d37b9c78199a.png)

This is how you can bring in any base layer into a web map. In later tutorials, you will use `layer control` to add multiple layers and then allow users to switch between them. 

Now, with a slight addition to the code, you can add your `neighborhood map` or `informal map` that was made in mapbox editor. This way you can customize different aspects of the map including the base layer. The `base-layer` can be a `style` you created or any of the common styles in mapbox. If you are interested in creating your own style, tutorial 5 walks you through the steps of creating the `figure-ground` map used in the Aleppo Platform. You can select zoom levels, the entry zoom point, the style of your tooltips and also add custom tool tip text. 

Using the below code, you add your map from mapbox editor by adding it's Map.Id. You then add a custom tooltip, which is the text bar that appears when you clickon the image. This will allow you to selct which property from your shape file you would like to add. You can add multiple categories and also custom text.

```html
// Add your neighborhood or any uploaded shape file here
var myLayer = L.mapbox.featureLayer('c4sr.p10e979a').addTo(map);
myLayer.on('layeradd', function(e) {
// Add a pop up to see attributes from your file
  var popupContent = '<strong>' + e.layer.feature.properties.title;
  e.layer.bindPopup(popupContent);
});
```

![Add Layer](<img width="1353" alt="screen shot 2016-02-11 at 2 00 37 am" src="https://cloud.githubusercontent.com/assets/16892784/12967245/3da23ca8-d065-11e5-95af-626a46eb97c0.png">)

You can use the file `Tutorial_4_2.html` or copy/paste the below into sublime. 

```html
<!--Tutorial: Setting a Base Map
    Conflict Urbanism: Aleppo
    Center for Spatial Research
================================================================= -->

<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />

<!-- Set your Project Name here -->
<title>Tutorial_4_2</title>

<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />

<!-- In order to set up the webmap, you need to link to mapbox.js and mapbox.css -->
<script src='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.js'></script>
<link href='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.css' rel='stylesheet' />

<!-- Style your map with changing the options below -->
<style>
  body { margin:0; padding:0; }
  #map { position:absolute; top:0; bottom:0; width:100%; }
</style>
</head>

<body>
<!-- Add the map to a div -->
<div id='map'></div>

<script>
// Add your access token here: 
L.mapbox.accessToken = 'pk.eyJ1Ijoic2lkbCIsImEiOiJkOGM1ZDc0ZTc5NGY0ZGM4MmNkNWIyMmIzNDBkMmZkNiJ9.Qn36nbIqgMc4V0KEhb4iEw';
// Add the layer you would like to use as your base layer. In this case we are using mapbox.satellite
var map = L.mapbox.map('map', 'mapbox.high-contrast')
// .setView([Lat, Long], Zoom)
    .setView([36.198, 37.1518], 13);

// Add your neighborhood or any uploaded shape file here
var myLayer = L.mapbox.featureLayer('c4sr.p10e979a').addTo(map);
myLayer.on('layeradd', function(e) {
// Add a pop up to see attributes from your file
  var popupContent = '<strong>' + e.layer.feature.properties.title;
  e.layer.bindPopup(popupContent);
});

</script>

</body>
</html>
```
For clarity, I switched the base layer from `mapbox.satellie` to `mapbox.high-contrast`. You can add any style you want. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12967272/81925b1e-d065-11e5-8f1a-9446758cb0f2.png)

Lastly, you can customize the text that appears on the tool tip. For instance if instead of just showing the neighborhood you wanted to say, `Neighborhood = title` then you can make the following changes to the code. If there are multiple 'attributes' in your shp file, you can tag multiple within the same tool tip.

```
  var popupContent = '<strong>' + e.layer.feature.properties.title;
```
```
  var popupContent = '<strong>' + 'Neighborhood =' + e.layer.feature.properties.title;
```

### Deliverable:
Template with Interactive Map 

##### Tutorial Checklist:
- [x] 01. QGIS: SetUp Neighborhood and Informal Data 
- [x] 02. MAPBOX: Sign Up, Installation and Introduction 
- [x] 03. MAPBOX_Editor: Design Map of Informal Neighborhoods
- [x] 04. MAPBOX_Studio: Design Map of Neighborhoods
- [x] 05. WEB: Embed Neighborhood and Informal Maps in Case Study
- [x] 06. WEB: WEB: Set up Interactive Map


