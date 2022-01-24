<script>
	// INI GLOBAL STYLES
	import global from '../global.css';
	import Nav from '../components/Nav.svelte';
</script>

<svelte:head>
	<!-- INI BUAT SEO, TITLE, HEAD DLL -->
	<title>Movie DB</title>
</svelte:head>

<!-- PRINSIPNYA INI STRUKTURNYA KAYAK HTML BIASA, JADI ADA HEAD, TERUS BODYNYA YANG NAV SAMA SLOT, TERUS FOOTER -->
<Nav />
<!-- slot INI BIAR SI LAYOUT TAU, KALO SI __layout INI, BAGIAN DARI WEBSITENYA SECARA UTUH, JADI DI slot INI BAKAL DIISI SAMA ISI PAGE SISANYA YANG BAKAL DIMASUKIN -->
<!-- KAYAK CONTAINER DI LARAVEL -->
<slot />
