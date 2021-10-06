<script lang="ts">
	import Header from '$lib/header/Header.svelte';
	import '../app.scss';
</script>

<svelte:head>
	<meta name="author" content="Bruno Nascimento" />
</svelte:head>

<Header />

<main>
	<slot />
</main>

<footer />

<style>
</style>
