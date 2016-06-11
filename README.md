# what's that gerber?

[![npm](https://img.shields.io/npm/v/whats-that-gerber.svg?maxAge=2592000?style=flat-square)](https://www.npmjs.com/package/whats-that-gerber)
[![Travis](https://img.shields.io/travis/tracespace/whats-that-gerber.svg?maxAge=2592000?style=flat-square)](https://travis-ci.org/tracespace/whats-that-gerber)
[![David](https://img.shields.io/david/tracespace/whats-that-gerber.svg?maxAge=2592000?style=flat-square)](https://david-dm.org/tracespace/whats-that-gerber)
[![David devDependencies](https://img.shields.io/david/dev/tracespace/whats-that-gerber.svg?maxAge=2592000?style=flat-square)](https://david-dm.org/tracespace/pcb-stackup#info=devDependencies)

Identify the probable PCB layer type of a Gerber or drill file by its filename.

## usage

``` javascript
var whatsThatGerber = require('whats-that-gerber')

var filename = 'my-board-F_Cu.gbr'
var layerType = whatsThatGerber(filename)              // 'tcu'
var layerName = whatsThatGerber.getFullName(layerType) // 'top copper'
```

### layer types and names

There are 12 available layer types. You can get an array of all types with:

``` javascript
var whatsThatGerber = require('whats-that-gerber')
var allLayerTypes = whatsThatGerber.getAllTypes() // ['drw', 'tcu', ...]
```

type | full name (en)     
-----|--------------------
drw  | gerber drawing     
tcu  | top copper         
tsm  | top soldermask     
tss  | top silkscreen     
tsp  | top solderpaste    
bcu  | bottom copper      
bsm  | bottom soldermask  
bss  | bottom silkscreen  
bsp  | bottom solderpaste
icu  | inner copper       
out  | board outline      
drl  | drill hits         

### full name locales

The full name method takes a locale string as its second parameter, which defaults to 'en':

``` javascript
var fullName = whatsThatGerber.getFullName('tcu', 'en')
```

Currently, no other locales are supported (because I don't know any!); contributions are greatly appreciated. If the type or locale is unrecognized, the result will be an empty string. Locale additions will be considered patch-level upgrades.

### supported cad programs

We should be able to identify files output by the following programs:

* KiCad
* Eagle
* Altium
* Orcad

## contributing

1. `$ git clone tracespace/whats-that-gerber`
2. `$ npm install`
3. `$ npm test`

If adding / modifying a filetype matcher, please remember to add / modify an example filename in [test/filenames-by-cad.js](test/filenames-by-cad.js).
