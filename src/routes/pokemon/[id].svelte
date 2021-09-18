<script context="module">
	export async function load({ page }) {
		const id = page.params.id;
		const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
		const res = await fetch(url);
		const monster = await res.json();
		return { props: { monster } };
	}
</script>

<script>
	export let monster;
	const type = monster.types[0].type.name;
</script>

<div class="flex flex-col items-center">
	<h2 class="text-4xl text-center my-8 uppercase">{monster.name}</h2>
	<p>
		Type: <strong>{type}</strong> | Height: <strong>{monster.height}</strong>
		| Weight: <strong>{monster.weight}</strong>
	</p>
	<img class="card-image" src={monster.sprites['front_default']} alt={monster.name} />
</div>
