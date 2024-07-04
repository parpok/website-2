<script lang="ts">
	import { get } from 'svelte/store';
	import { GPDRAccept } from '$lib';

	let consent = get(GPDRAccept);

	function acceptGPDR() {
		GPDRAccept.set(true);
		consent = true;
	}

	function dontAcceptGPDR() {
		GPDRAccept.set(false);
		consent = false;
	}
</script>

{#if consent === null}
	<div id="IsItOkBox">
		<h1>Are you OK with analytics, tracking and such</h1>
		<p>This website uses Vercel for analytics and speed insights.</p>

		<a href="https://vercel.com/docs/analytics/privacy-policy">Here's info about all of that</a>

		<button on:click={acceptGPDR}>I'm OK with that</button>
		<br />
		<button on:click={dontAcceptGPDR}>Nah. That's not for me</button>
	</div>
{/if}

<style>
	:global(#IsItOkBox) {
		margin: 10px;
		padding: 10px;
		border: 1px solid #000;
		border-radius: 10px;
		/* width: 200px; */
		text-align: center;
		background-color: #fff;
	}
</style>
