<template>
	<div id="app">
		<h1>Vue Static Map</h1>
		<static-map id="staticMap" :google-api-key="apiKey" :zoom="zoom" :center="center" :scale="scale" :language="language" v-on:get-url="getUrl" :paths="paths" :format="format" :markers="markers" :size="size" :type="type"></static-map>
		<div>
			<pre>{{url}}</pre>
		</div>
	</div>
</template>

<script>
import StaticMap from './components/StaticMap';

function getUrl(url) {
	this.url = url;
}

export default {
	data: () => {
		const dataValues = {
			apiKey: '',
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
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
#staticMap {
	width: 640px;
}
pre {
	white-space: pre-line;
}
</style>
