<script>
	import { pokemon } from '../stores/pokestore';
	import Card from '../components/card.svelte';

	let searchTerm = '';
	let filteredPokemon = [];
	$: {
		if (searchTerm) {
			filteredPokemon = $pokemon.filter((monster) =>
				monster.name.toLowerCase().includes(searchTerm.toLowerCase())
			);
		} else {
			filteredPokemon = [...$pokemon];
		}
	}
</script>

<svelte:head>
	<title>Svelte Pokedex</title>
</svelte:head>
<h1 class="text-4xl text-center my-8 uppercase">Svelte Kit Pokedex</h1>

<input
	class="w-full rounded-md text-lg p-4 border-2 border-gray-200"
	type="text"
	placeholder="search pokemon"
	bind:value={searchTerm}
/>

<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
	{#each filteredPokemon as monster}
		<Card {monster} />
	{/each}
</div>
