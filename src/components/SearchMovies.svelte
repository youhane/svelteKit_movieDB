<script>
	// INI PAKE FUNCTION DARI SVELTE SENDIRI, KAYAK USESTATE DLL KALO REACT
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';
	let inputValue = '';
	let active = false;

	function cancelInactive() {
		// INI BUAT NGILANGIN LABEL, JADI KALO ADA ISINYA, LABELNYA BAKAL TETEP ILANG, GA NIMPA
		if (inputValue) {
			active = true;
		} else {
			active = false;
		}
	}
	function submitSearch() {
		goto('/search/' + inputValue);
	}
</script>

<!-- on:submit|preventDefault={namaFunction} -->
<!-- SVELTE BISA PREVENT DEFAULT SAMA BANYAK COMMON FUNCTIONS via | DOANG, NANTI KITA TINGGAL LENGKAPIN SENDIRI MAUNYA APA -->
<form on:submit|preventDefault={submitSearch} class="search">
	<!-- INI CONDITIONAL RENDERING -->
	{#if !active}
		<!-- FLY BISA KASIH ANIMASI FADE PAKE FLY -->
		<label in:fly={{ y: -10, duration: 500 }} out:fly={{ y: -10, duration: 500 }} for="search_movie"
			>Search Movie</label
		>
	{/if}
	<!-- CARA AMBIL VALUE DARI INPUT, PAKE BIND:VALUE={variabelBuatNyimpen} -->
	<input
		on:blur={cancelInactive}
		on:focus={() => (active = true)}
		bind:value={inputValue}
		type="text"
		name="search_movie"
		class={active ? 'selected' : ''}
	/>
	<!-- ITU YANG CLASS SI INPUT, JADI CLASSNYA BAKAL JADI SELECTED, KALO VALUE active ITU TRUE, KALO FALSE, CLASSNYA BAKAL KOSONG -->

	<!-- CONDITIONAL RENDERING, KALO ADA ISINYA SI INPUT, DISPLAY BUTTONNYA -->
	{#if inputValue}
		<button in:fly={{ x: 20, duration: 500 }} out:fly={{ x: 0, duration: 500 }}>Search</button>
	{/if}
	<!-- <h1>{inputValue}</h1> -->
</form>

<style>
	.search {
		position: relative;
		width: 30%;
		margin: 1rem;
	}
	button {
		font-size: 0.7rem;
		padding: 0rem 1rem;
		background-color: rgb(96, 110, 201);
		color: white;
		font-weight: bold;
		border: none;
		position: absolute;
		bottom: 50%;
		right: 0;
		transform: translate(0, 50%);
		height: 100%;
		border-top-right-radius: 10px;
		border-bottom-right-radius: 10px;
		cursor: pointer;
	}
	input {
		width: 100%;
		border: none;
		font-size: 1rem;
		outline: none;
		color: rgb(255, 255, 255);
		transition: background 075s ease-out;
		font-weight: bold;
		background-color: rgb(63, 63, 63);
		border-radius: 10px;
		padding: 1rem;
	}
	label {
		position: absolute;
		font-size: 0.8rem;
		top: 50%;
		left: 0;
		transform: translate(0, -50%);
		pointer-events: none;
		color: #fff;
		padding: 0rem 1rem;
	}
	input.selected {
		background: rgb(50, 50, 50);
	}
</style>
