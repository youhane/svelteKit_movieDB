<script context="module">
	// KALO MAU BIKIN API REQUEST, LAKUIN DI SCRIPT TAG PAKE CONTEXT="MODULE"
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=${
				import.meta.env.VITE_API
			}&language=en-US&query=${params.id}&page=1&include_adult=false`
		);
		const data = await res.json();
		console.log(data);
		if (res.ok) {
			return {
				// RETURNNYA APA, INI PERLU : SOALNYA, SI DATA DOANG ITU BANYAK YANG GA DIPERLUIN, YANG PERLU DIPAKE CUMAN YANG DI RESULTS DOANG
				props: { searchedMovie: data.results }
			};
		}
	}
</script>

<script>
	import MovieCard from '../../components/MovieCard.svelte';
	import { fly } from 'svelte/transition';
	import.meta.env.VITE_API;
	export let searchedMovie;
</script>

<div
	class="searched-movies"
	in:fly={{ y: 50, duration: 500, delay: 500 }}
	out:fly={{ duration: 500 }}
>
	{#each searchedMovie as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	.searched-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 2rem;
		height: 20vh;
	}
</style>
