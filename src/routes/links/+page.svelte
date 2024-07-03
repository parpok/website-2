<script lang="ts">
	import CustomLink from '$lib/CustomLink.svelte';
</script>

<h1>Links for all sorts of things</h1>
<div id="LinksList">
	<CustomLink linkIcon="🫠" linkName="My website - I mean this" linkURL="/" />
	<CustomLink linkIcon="💌" linkName="Email me" linkURL="mailto:me@parpok.xyz" />

	<CustomLink linkIcon="🐤" linkName="Twitter" linkURL="https://twitter.com/parpok206" />
	<CustomLink linkIcon="🦣" linkName="Boring ahhh Fedi" linkURL="https://101010.pl/@parpok" />

	<CustomLink linkIcon="🐙😺" linkName="GitHub" linkURL="https://github.com/parpok" />
	<CustomLink linkIcon="🦝🐕" linkName="Gitlab" linkURL="https://git.parpok.xyz/parpok" />

	<CustomLink linkIcon="🅰🔨" linkName="Projects" linkURL="./projects" />

	<CustomLink
		linkIcon="🅱️"
		linkName="BruhSoftware"
		linkURL="https://misskey.parpok.lomza.pl/@BruhSoftware"
	/>
</div>

<style>
	#LinksList {
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-template-rows: auto auto;
		gap: 5%;
		justify-content: center;
		align-items: center;

		@media only screen and (max-width: 600px) {
			display: flex;
			flex-direction: column;
		}
	}
</style>
