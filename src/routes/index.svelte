<script context="module">
	export async function load({ fetch }) {
		const res = await fetch('https://www.thecocktaildb.com/api/json/v1/1/filter.php?c=Cocktail');
		const data = await res.json();

		if (res.ok) {
			return {
				props: { drinks: data.drinks }
			};
		}
	}
</script>

<script>
	import PopularDrinks from '$lib/components/PopularDrinks.svelte';
	import Search from '$lib/components/Search.svelte';
	export let drinks;
</script>

<section>
	<Search />
	<PopularDrinks {drinks} />
</section>
