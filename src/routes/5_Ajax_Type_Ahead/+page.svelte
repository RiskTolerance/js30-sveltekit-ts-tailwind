<script lang="ts">
	import type { PageData } from './$types';

	export let data: PageData;
	let cities = data.data;

	let textbox: string = '';

	const matcher = (textbox: string, cities: any[]) => {
		const regex = new RegExp(textbox, 'gi');
		let matches = cities.filter((place: { state: any; city: string; population: number }) => {
			return place.city.match(regex) || place.state.match(regex);
		});
		let format = matches.map((place) => {
			const cityName = place.city.replace(regex, `<span class="bg-green-300">$&</span>`);
			const stateName = place.state.replace(regex, `<span class="bg-green-300">$&</span>`);
			return { city: cityName, state: stateName, population: place.population };
		});
		return format;
	};

	$: matches = matcher(textbox, cities);
</script>

<div class="w-full h-screen  bg-green-800 flex flex-col items-center justify-center">
	<div class="flex flex-col items-center space-y-2 h-screen overflow-hidden">
		<h1 class="text-white text-4xl m-4">Type Ahead</h1>
		<input
			class="w-96 border-solid border-green-300 border-4 p-3"
			type="text"
			placeholder="type something here..."
			bind:value={textbox}
		/>
		{#each matches as c}
			<div class="flex flex-row justify-between items-center px-6 w-96 bg-white">
				<p>{@html c.city}, {@html c.state}</p>
				<p>{c.population}</p>
			</div>
		{/each}
	</div>
</div>
