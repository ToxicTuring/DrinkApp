<script>
	import '../app.css';
</script>

<div class="container mx-auto mt-3">
	<a href="/">
		<h1 class="text-7xl font-['Lobster']">
			<i class="fa-solid fa-martini-glass-citrus" />
			frontend drink
		</h1>
	</a>
	<slot />
</div>

<style>
	:global(body) {
		background-color: #1d3040;
		color: #bfc2c7;
	}
</style>
