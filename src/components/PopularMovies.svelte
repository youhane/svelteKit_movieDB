<script>
	// INI CARA SVELTE NERIMA DATA YANG DIEXPORT DARI TEMPAT LAIN
	// PROPSNYA PER NAMA YANG ADA DI ATRIBUTTENYA
	// export let movies;
	// console.log(movies);

	// KALO PAKE NAMA VARIABEL YANG SAMA KAYAK NAMA VARIABEL DARI PASSING VALUE APINYA
	// DISINI PAKE NAMA PROPS YANG SESUAI SAMA NAMA VARIABELNYA JUGA
	export let popular;
	// console.log(popular[0]);

	import MovieCard from './MovieCard.svelte';
</script>

<h3>Popular Movies</h3>

<div class="popular-movies">
	<!-- FOR EACH POPULAR, AS MOVIE, DO SOMETHING INSIDE -->
	{#each popular as movie}
		<MovieCard {movie} />
	{/each}
	<!-- END FOREACH -->
</div>

<style>
	h3 {
		padding: 0 1rem;
	}
	.popular-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 2rem;
	}
</style>
