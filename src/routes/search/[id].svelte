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
	import GoBackHome from '$lib/components/GoBackHome.svelte';
	import PopularDrinks from '$lib/components/PopularDrinks.svelte';
	import Search from '$lib/components/Search.svelte';
	import { fly } from 'svelte/transition';

	export let drinks;
</script>

<section in:fly={{ y: 50, duration: 500, delay: 500 }} out:fly={{ duration: 500 }}>
	<Search />
	{#if drinks}
		<PopularDrinks {drinks} />
	{:else}
		<div class="flex flex-wrap grid justify-evenly gap-5 mt-5">
			<p>No drink found</p>
			<GoBackHome />
		</div>
	{/if}
</section>
