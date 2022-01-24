<script context="module">
	// KALO MAU BIKIN API REQUEST, LAKUIN DI SCRIPT TAG PAKE CONTEXT="MODULE"
	export async function load({ fetch, params }) {
		// PARAMS ITU BUAT AMBIL DATA YANG DI PASS KE PAGE INI DARI TEMPAT LAIN
		// console.log(params.id);
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=${
				import.meta.env.VITE_API
			}&language=en-US`
		);
		const movieDetail = await res.json();
		console.log(movieDetail);
		if (res.ok) {
			return {
				// RETURNNYA APA, INI GAADA : SOALNYA DIA RETURNNYA BENTUKNYA UDAH DI BAGIAN+BENTUK YANG DIPERLUIN
				props: { movieDetail }
			};
		}
	}
</script>

<script>
	import.meta.env.VITE_API;
	export let movieDetail;
</script>

<div class="movie-details">
	<div class="img-container">
		<img
			src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path}
			alt={movieDetail.title}
		/>
		<div class="txt-container">
			<h1>{movieDetail.title}</h1>
			<p class="overview">{movieDetail.overview}</p>
			<p>
				<span>Release Date</span>
				{movieDetail.release_date} <br />
				<span>Budget:</span> ${movieDetail.buget} <br />
				<span>Rating:</span>
				{movieDetail.vote_average} <br />
				<span>Runtime: </span>
				{movieDetail.runtime} mins
			</p>
		</div>
	</div>
</div>

<style>
	h1 {
		padding: 1rem 0rem 2rem;
	}
	p {
		padding: 1rem 0rem;
	}
	.img-container {
		width: 100%;
	}
	img {
		width: 100%;
		border-radius: 1rem;
	}
	.movie-details {
		margin: 2rem 20%;
	}
	span {
		font-weight: bold;
	}
</style>
