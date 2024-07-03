<script lang="ts">
	export let linkURL: string;
	export let linkIcon: string;
	export let linkName: string;
</script>

<div id="link{linkName}" class="CustomLink">
	<a href={linkURL}>{linkIcon + linkName}</a>
</div>

<style>
	:global(.CustomLink) {
		margin: 10px;
		padding: 10px;
		border: 1px solid #000;
		border-radius: 10px;
		width: 200px;
		text-align: center;
		background-color: #fff;
		transition: 0.3s;
	}
</style>
