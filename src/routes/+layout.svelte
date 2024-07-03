<script>
	import Top from '$lib/Top.svelte';
	import Bottom from '$lib/Bottom.svelte';
	import './style.css';

	import { page } from '$app/stores';
	import { injectSpeedInsights } from '@vercel/speed-insights/sveltekit';

	injectSpeedInsights();
	// yes vercel will spy

	const appName = $page.url.hostname;
	$: title = [appName, ...$page.url.pathname.split('/').slice(1)].filter(Boolean).join(' - ');
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content="My personal website" />
	<meta name="author" content="parpok" />
	<meta name="keywords" content="{appName}, personal page, links, blog, projects, gallery" />
	<link rel="icon" href="/avatar.png" />
	<!-- This is just in case Svelte doesn't catch up with app.html -->
</svelte:head>

<Top />

<div class="Container">
	<slot></slot>
</div>
<Bottom />

<style>
	:global(.Container) {
		display: flex;
		margin-top: 2.5%;
		margin-left: 5%;
		margin-right: 5%;
		margin-bottom: 2.5%;
		padding: 10%;
		border: 1px solid #000;
		border-radius: 10px;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
</style>
