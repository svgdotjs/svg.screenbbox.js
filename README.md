# svg.screenbbox.js

A plugin for the [svgjs](https://github.com/svgdotjs/svg.js) library which gets the bbox of a path/polygon/polyline after all transformations applied.

The returned bounding box is in the screens coordinate space which means that the scroll offset is not applied (same as with screenCTM)

## Getting started


    bower install svg.screenbbox.js


```javascript

// add some viewbox madness to make this more interesting
var nested = draw.viewbox(0, 0, 300, 200).nested().viewbox(-50, 20, 200, 300)

// create path with transformation
var path = draw.path('M150 0 L75 200 L225 200 Z').rotate(25).scale(0.5)

// get bounding box in screen coordinates
var bbox = path.screenBBox()

// do something with it, e.g. draw a reactangle around (with jQuery here)
$('<div>').css({
  position:'absolute',
  width:bbox.width,
  height:bbox.height,
  left:bbox.x+window.pageXOffset, // dont forget to add the scroll offset
  top:bbox.y+window.pageYOffset,  // dito
  outline:'3px solid black'
}).appendTo('body')
```

## Dependencies
This module requires svg.js >= v2.2.0