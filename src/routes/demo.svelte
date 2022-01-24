<script>
	let count = 0;
	function incrementBtn() {
		count++;
	}
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<a href="/about">About</a>

<button on:click={incrementBtn}>Increment</button>
<h2>Number: {count}</h2>

<style>
	h1 {
		color: red;
	}
</style>
