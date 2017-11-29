# vue-static-map

> a simple component to generate static google map

![static google map](https://user-images.githubusercontent.com/461124/28100714-6c896d1e-6689-11e7-8a38-327dfe4b6ff5.png)

[Google Documentation](https://developers.google.com/maps/documentation/static-maps/intro)

## Demo

- [JSBin example](http://jsbin.com/gizixekilu/edit?html,js,output)

## Requirements

1. Vue 2.X.X
2. vue-cli https://github.com/vuejs/vue-cli (for development only)

## Usage

1. Install from npm

		npm install --save LouisMazel/vue-static-map#master --save

	Or include in your html using the script tag
	```html
	<script src="https://unpkg.com/vue-static-map/dist/StaticMap.js"></script>
	```

2. Add component in your app

	```javascript
	import StaticMap from 'vue-static-map';
	// or require('vue-static-map')
	// or window.StaticMap if you are including in a script tag

	export default {
		components: {
			StaticMap,
		},
	}

	```

3. Create some parameters in your data object

	```javascript
	export default {
		data: {
			apiKey: 'YOUR_GOOGLE_API_KEY', // required
			format: 'png',
			language: 'fr',
			markers: [
				{
					lat: 48.8396851, lng: 2.3922176, icon: 'https://s3-eu-west-1.amazonaws.com/ct-documents/emails/A-static.png',
				},
				{
					lat: 49.7802536, lng: 4.6953587, icon: 'https://s3-eu-west-1.amazonaws.com/ct-documents/emails/B-static.png',
				},
			],
			paths: [
				{
					color: '0x2f8fb6',
					weight: 5,
					geodesic: true,
					fillcolor: '0x96bf31',
					locations: [
						{
							startLat: 48.8396851, endLng: 2.3922176,
						},
						{
							startLat: 49.7802536, endLng: 4.6953587,
						},
					],
				},
			],
			scale: '2',
			zoom: 7,
			center: 'Reims',
			size: [1280, 250],
			type: 'roadmap',
			url: '',
		},
		components: {
			StaticMap,
		},
	}
	```

4. In your template just call the static map component

	```html
	<static-map :google-api-key="apiKey" :format="format" :markers="markers" :zoom="zoom" :center="center" :size="size" :type="type" :paths="paths" :language="language"></static-map>
	```

## Events

1. What about if you want the URL of the map, you can easily do that using the **getUrl** event

	```javascript
		function getUrl(url) {
			this.url = url;
		}

		export default {
			data: () => {
				const dataValues = {
					apiKey: 'YOUR_API_KEY',
					center: 'Empire State Building',
					url: '',
					zoom: 13,
				};
				return dataValues;
			},
			name: 'app',
			components: {
				StaticMap,
			},
			methods: {
				getUrl,
			},
		};
	```

2. Add the event on your template

	```html
	<static-map :google-api-key="apiKey" v-on:get-url="getUrl" :zoom="zoom" :center="center"></static-map>
	```

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
vue build src/components/StaticMap.vue --prod --lib
```
