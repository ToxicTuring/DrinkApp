<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${params.id}`
		);
		const drinkDetail = await res.json();

		if (res.ok) {
			return {
				props: { drinkDetail: drinkDetail.drinks[0] }
			};
		}
	}
</script>

<script>
	import GoBackButton from '$lib/components/GoBackButton.svelte';
	import { fly } from 'svelte/transition';

	export let drinkDetail;
	let ingredients = [];

	for (let i in drinkDetail) {
		if (/^strIngredient[0-9]?[0-9]/.test(i)) {
			if (drinkDetail[i] != null) {
				// @ts-ignore
				let t = i.match(/\d+$/)[0];
				let measurement = drinkDetail[`strMeasure${t}`];
				let ingredient = drinkDetail[i];
				ingredients.push({
					ingredient,
					measurement
				});
			}
		}
	}
</script>

<section
	class="flex flex-wrap justify-evenly gap-5 mt-5"
	in:fly={{ y: 50, duration: 500 }}
	out:fly={{ duration: 500 }}
>
	<div
		class="max-w-xl bg-white rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700 mx-8"
	>
		<img class="rounded-t-lg" src={drinkDetail.strDrinkThumb} alt="" />
		<div class="p-5">
			<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
				{drinkDetail.strDrink}
			</h5>
			<ul>
				{#each ingredients as ingredient}
					{#if ingredient.measurement}
						<li>{ingredient.measurement} {ingredient.ingredient}</li>
					{:else}
						<li>{ingredient.ingredient}</li>
					{/if}
				{/each}
			</ul>
			<br />
			<p class="mb-3 font-normal text-gray-700 dark:text-gray-400">{drinkDetail.strInstructions}</p>
			<br />
			<GoBackButton />
		</div>
	</div>
</section>
