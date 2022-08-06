<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${params.id}`
		);
		const data = await res.json();

		if (res.ok) {
			return {
				props: { drinks: data.drinks }
			};
		}
	}
</script>

<script>
	import GoBackButton from '$lib/components/GoBackButton.svelte';
	import PopularDrinks from '$lib/components/PopularDrinks.svelte';

	export let drinks;
	console.log(drinks);
</script>

<section>
	{#if drinks}
		<PopularDrinks {drinks} />
	{:else}
		<div class="content-center">
			<h1 class="my-20 text-5xl text-center ">No drink found</h1>
			<GoBackButton />
		</div>
	{/if}
</section>
