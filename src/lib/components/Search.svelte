<script>
	let inputValue = '';
	import { goto } from '$app/navigation';

	function submitSearch() {
		goto('/search/' + inputValue);
	}
</script>

<form class="mx-80 my-10" on:submit|preventDefault={submitSearch}>
	<div class="relative">
		<div class="flex absolute inset-y-0 left-0 items-center pl-3 pointer-events-none">
			<svg
				aria-hidden="true"
				class="w-5 h-5 text-gray-500 dark:text-gray-400"
				fill="none"
				stroke="currentColor"
				viewBox="0 0 24 24"
				xmlns="http://www.w3.org/2000/svg"
				><path
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"
				/></svg
			>
		</div>
		<input
			bind:value={inputValue}
			type="search"
			id="default-search"
			class="block p-4 pl-10 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
			required
			placeholder="Search for a drink"
		/>

		{#if inputValue}
			<button
				type="submit"
				class="text-white absolute right-2.5 bottom-2.5 focus:outline-none font-medium rounded-lg text-sm px-4 py-2 bg-gradient-to-br from-purple-600 to-blue-500 hover:bg-gradient-to-bl focus:ring-4 focus:ring-blue-300 dark:focus:ring-blue-800 "
				>Search</button
			>
		{/if}
	</div>
</form>
