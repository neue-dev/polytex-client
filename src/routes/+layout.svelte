<script lang="ts">
	import { onMount } from 'svelte';
	let { children } = $props();
	
	// Present a loader before rendering content
	onMount(() => {
		const content = document.getElementById('content');
		const loader = document.getElementById('content-loader');

		// ! remove timeout
		setTimeout(() => {
			content?.classList.remove('hidden');
			loader?.classList.add('hidden');
		}, 2000)

	})
</script>

<main class="window">
	<div id="content" class="content hidden">
		{@render children()}
	</div>
	<div id="content-loader" class="content-loader">
		<img class="content-loader image" src="/loading.gif">
	</div>
</main>

<style>
	main.window {
		padding: 0;
		margin: 0;
		width: 100vw;
		height: 100vh;
		background-color: #E7DFDD;
		overflow: hidden;
	}

	.content-loader {
		width: 100%;
		height: 100%;
		padding-left: auto;
		padding-right: auto;
	}

	.content-loader.image {
		max-width: fit-content;
		max-height: fit-content;
	}

	.hidden {
		display: none !important;
	}
</style>
