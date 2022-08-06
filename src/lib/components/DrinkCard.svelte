<script>
	export let drink;
</script>

<div
	class="max-w-xs bg-white rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700"
>
	<a href={'/drinks/' + drink.idDrink}>
		<img class="rounded-t-lg" src={drink.strDrinkThumb} alt="" />
	</a>
	<div class="p-5">
		<a href={'/drinks/' + drink.idDrink}>
			<h5
				class="mb-2 text-2xl text-center font-bold tracking-tight text-gray-900 dark:text-white font-['Lobster']"
			>
				{drink.strDrink}
			</h5>
		</a>
	</div>
</div>
