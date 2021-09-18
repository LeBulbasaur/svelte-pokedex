<script>
	import { fade } from 'svelte/transition';
	export let monster;
</script>

<a
	class="p-6 bg-gray-100 text-gray-800 text-center rounded-md shadow-sm hover:shadow-md flex flex-col items-center"
	href={`/pokemon/${monster.id}`}
	transition:fade
>
	<img class="h-40 w-40" src={monster.image} alt={monster.name} />
	<h2 class="text-2xl capitalize">{monster.id}. {monster.name}</h2>
</a>
