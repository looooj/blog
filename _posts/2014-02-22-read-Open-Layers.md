---
layout: post
title: read OpenLayers 
tags: [OpenLayers]
---

###.\OpenLayers\lib\OpenLayers\Layer\Grid.js

calc tile 

    initGriddedTiles:function(bounds) {
        ...

          this.addTile(tileBounds, px);
        ...
    }

###.\OpenLayers\lib\OpenLayers\TileManager.js
draw tile

    drawTilesFromQueue: function(map) {
         ...
    }


###.\OpenLayers\lib\OpenLayers\Map.js

map setCenter call moveto


map getExtent call baseLayer getExtent Layer call 

    this.map.calculateBounds();

