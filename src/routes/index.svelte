<script context="module">
	// KALO MAU BIKIN API REQUEST, LAKUIN DI SCRIPT TAG PAKE CONTEXT="MODULE"
	export async function load({ fetch }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=${
				import.meta.env.VITE_API
			}&language=en-US&page=1`
		);
		const data = await res.json();
		console.log(data);
		if (res.ok) {
			return {
				// RETURNNYA APA, INI PERLU : SOALNYA, SI DATA DOANG ITU BANYAK YANG GA DIPERLUIN, YANG PERLU DIPAKE CUMAN YANG DI RESULTS DOANG
				props: { popular: data.results }
			};
		}
	}
</script>

<script>
	// TEMPAT BUAT IMPORT SAMA EXPORT COMPONENTS & DATA
	import PopularMovies from '../components/PopularMovies.svelte';
	import SearchMovies from '../components/SearchMovies.svelte';
	import { fly } from 'svelte/transition';

	// INI PAKE VALUE DARI .env nya
	import.meta.env.VITE_API;

	// INI EXPORT popular BIAR HASIL FETCH APINYA BISA DIPAKE KE SEMUA COMPONENTNYA DARI INDEX
	export let popular;
</script>

<!-- y, POSISI VERTIKAL, duration, LAMA ANIMASI, delay, NUNGGU BERAPA LAMA BARU JALAN -->
<section in:fly={{ y: 50, duration: 500, delay: 500 }} out:fly={{ duration: 500 }}>
	<SearchMovies />
	<!-- KITA BISA PAKE NAMA ATRIBUT BARU BUAT PASS VALUENYA -->
	<!-- <PopularMovies movies={popular} /> -->

	<!-- BISA JUGA PAKE NAMA VARIABEL YANG SAMA BUAT PASSNYA, JADI GAUSAH BIKIN ATRIBUT BARU, PAKE NAMA ATRIBUT DARI VARIABEL YANG MAU DIPAKE AJA, GINI -->
	<PopularMovies {popular} />
</section>
