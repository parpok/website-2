<script lang="ts">
	function getYear(): string {
		let date = new Date();

		let currentYear = date.getFullYear();

		return String(currentYear);
	}

	let year = getYear();
</script>

<footer>
	<p id="CurrentYear">{year}</p>
</footer>

<style>
	:global(footer) {
		text-align: center;
	}
</style>
