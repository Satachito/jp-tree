# jp-tree

THIS PACKAGE IS NO LONGER MAINTAINED.
PLEASE CONSIDER USING @satachito/jp-tree-view

https://www.npmjs.com/package/@satachito/jp-tree-view


A JSON based object browser / editor Web Component.

* No external resources.
* Very fast. There is no data conversion inside.
* Ultra small. Easy to understand and modify.


## Install
```
npm install @satachito/jp-tree --save
```

## Running demo

In our demo, we are using Bare module specifiers, ( for example `@satachito/jp-tree` to `./node_modules/@satachito/jp-tree/jp-tree.js` ). So run this demo using `es-dev-server` with `--node-resolve` option.

### Serve
```
npm install -g es-dev-server
cd node_modules/@satachito/jp-tree/demo
npm i
es-dev-server --node-resolve
```

### Access to specified address using Chrome

We are testing on Chrome only.


## Write HTML and JavaScript

### index.html
```
<!doctype html>
<html lang=zxx>
	<title>jp-tree demo</title>

	<link href='https://fonts.googleapis.com/css?family=Roboto:300,400,500' rel='stylesheet'>
	<link href='https://fonts.googleapis.com/css?family=Material+Icons&display=block' rel='stylesheet'>

<body>
	<script type=module>
		import '@satachito/jp-tree'
	</script>
	<jp-tree></jp-tree>
	<jp-tree json=null></jp-tree>
	<jp-tree json=true></jp-tree>
	<jp-tree json=false></jp-tree>
	<jp-tree json=123></jp-tree>
	<jp-tree json='"ABC"'></jp-tree>
	<jp-tree
		json='{
			"jockeys": {
				"05339": {
					"name": "Christophe Patrice Lemaire"
				,	"birthday": 19790520
				}
			,	"05212": {
					"name": "Mirco Demuro"
				,	"birthday": 19790111
				}
			}
		,	"races": [
				{	"date":	20181125
				,	"name": "Japan Cup"
				,	"grade": "G1"
				,	"horses": [ "Almond Eye" ]
				}
			,	{	"date":	20181125
				,	"name": "Keihan Hai"
				,	"grade": "G3"
				,	"horses": [ "Danon Smash" ]
				}
			,	{	"date":	20190120
				,	"name": "Tokai S."
				,	"grade": "G2"
				,	"horses": [ "Inti" ]
				}
			,	{	"date":	20190120
				,	"name": "American Jockey Club Cup"
				,	"grade": "G2"
				,	"horses": [ "Sciacchetra" ]
				}
			]
		}'
		isOpen=true
	></jp-tree>
	<script type=module>	
		class
		Undef extends HTMLElement {
			constructor() {
				super()
				const jv = document.createElement( 'jp-tree' )
				jv.props( {}, 'THE UNDEF KEY' )
				this.attachShadow( { mode: 'open' } ).appendChild( jv )
			}
		}
		customElements.define( 'jp-undef', Undef )
		const
		container = {
			"HorseRaces": {
				"jockeys": {
					"05339": {
						"name": "Christophe Patrice Lemaire"
					,	"birthday": 19790520
					}
				,	"05212": {
						"name": "Mirco Demuro"
					,	"birthday": 19790111
					}
				}
			,	"races": [
					{	"date":	20181125
					,	"name": "Japan Cup"
					,	"grade": "G1"
					,	"horses": [ "Almond Eye" ]
					}
				,	{	"date":	20181125
					,	"name": "Keihan Hai"
					,	"grade": "G3"
					,	"horses": [ "Danon Smash" ]
					}
				,	{	"date":	20190120
					,	"name": "Tokai S."
					,	"grade": "G2"
					,	"horses": [ "Inti" ]
					}
				,	{	"date":	20190120
					,	"name": "American Jockey Club Cup"
					,	"grade": "G2"
					,	"horses": [ "Sciacchetra" ]
					}
				]
			}
		}
		class
		App extends HTMLElement {
			constructor() {
				super()
				const jv = document.createElement( 'jp-tree' )
				jv.props( container, 'HorseRaces', true, true )
				this.attachShadow( { mode: 'open' } ).appendChild( jv )
			}
		}
		customElements.define( 'jp-app', App )
	</script>
	<jp-undef></jp-undef>
	<jp-app></jp-app>
```

## Props

* json - The JSON to be displayed. Expects a valid JSON object.
* key - The key of the root object.
* isOpen - Open child elements. Default: true.
* edit - Edit mode. Default: true.
* depth - The maximum level of the JSON Tree to be expanded. Specify 0 to Infinity.

## API

props( container, key, isOpen = false, edit = false, depth = 0 )

* container - Container object. container[ key ] is to be displayed. Expects a valid JSON object.
* key - The key of the root object.
* isOpen - Open child elements. Default: false.
* edit - Edit mode. Default: false.
* depth - The maximum level of the JSON Tree to be expanded. Specify 0 to Infinity.


## Changelog  

* 1.0.0 Initial Release
* 1.0.1 Update README.md
