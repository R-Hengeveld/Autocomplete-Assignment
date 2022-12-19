<template>
	<a href="https://storyteq.com/">
		<img alt="Storyteq logo" src="./assets/storyteq-logo-full_1.png">
	</a>
	<Autocomplete :cities="[
		'San Jose', 'Santiago', 'San Francisco', 'Santa Rosa',
		'San Juan', 'Sabadell', 'Salamanca', 'Salt Lake City',
		'Salinas', 'Salem', 'Sausalito', 'Taipei', 'Tel Aviv',
		'Tempe', 'Termez', 'Temuco', 'Tiajuna', 'Tieling',
		'Thousand Oaks', 'Thunder Bay', 'Tokyo', 'Tulsa'
	]" :books="[
	{
		title: 'Don Quixote',
		author: 'Miguel De Cervantes',
	},
	{
		title: 'Pilgrim\'s Progress',
		author: 'John Bunyan',
	},
	{
		title: 'Robinson Crusoe',
		author: 'Daniel Defoe',
	},
	{
		title: 'Gulliver\'s Travels',
		author: 'Jonathan Swift',
	},
	{
		title: 'Tom Jones',
		author: 'Henry Fielding',
	},
	{
		title: 'Clarissa',
		author: 'Samuel Richardson',
	},
	{
		title: 'Tristram Shandy',
		author: 'Laurence Sterne',
	},
]" />
</template>

<script>
import Autocomplete from './components/Autocomplete.vue';

export default {
	name: 'App',
	components: {
		Autocomplete
	}
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
