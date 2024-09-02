<script>
	import '$lib/global.scss';
	import Calculator from '$lib/components/Calculator.svelte';
</script>

<main>
	<h1>Min enkla miniräknare</h1>
	<Calculator />
</main>

<style lang="scss">
	main {
		text-align: center;
		padding: 20px;
	}

	h1 {
		color: #333;
	}
</style>
