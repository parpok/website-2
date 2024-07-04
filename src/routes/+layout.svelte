<script>
	import Top from '$lib/Top.svelte';
	import Bottom from '$lib/Bottom.svelte';
	import './style.css';
	import { injectSpeedInsights } from '@vercel/speed-insights/sveltekit';
	import { dev } from '$app/environment';
	import { inject } from '@vercel/analytics';
	import { page } from '$app/stores';

	import { GPDRAccept } from '$lib';
	import { get } from 'svelte/store';
	import GpdrToggle from '$lib/GPDRToggle.svelte';
	let consent = get(GPDRAccept);

	GPDRAccept.subscribe(value => {
    consent = value;
    if (consent) {
		injectSpeedInsights();
        inject({ mode: dev ? 'development' : 'production' });
    }
});

// So now vercel will only spy when marked OK :3

	const appName = $page.url.hostname;
	$: title = [appName, ...$page.url.pathname.split('/').slice(1)].filter(Boolean).join(' - ');
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content="My personal website" />
	<meta name="author" content="parpok" />
	<meta name="keywords" content="{appName}, personal page, links, blog, projects, gallery" />
	<link rel="icon" href="/avatar.png" />

	<a rel="me" href="https://101010.pl/@parpok">⠀</a>
	<a rel="me" href="https://misskey.parpok.lomza.pl/@parpok">⠀</a>
	<!-- Links for those fediverse bots bruh  -->
	<!-- This is just in case Svelte doesn't catch up with app.html -->
</svelte:head>

<Top />

<div class="Container">
	<slot></slot>
</div>
{#if consent === null}
	<GpdrToggle />
{/if}
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
