<script>
	export let drinks;
	import DrinkCard from './DrinkCard.svelte';
</script>

<div class="flex flex-wrap justify-evenly gap-5">
	{#each drinks as drink}
		<DrinkCard {drink} />
	{/each}
</div>
