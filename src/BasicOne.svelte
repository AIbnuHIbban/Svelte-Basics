<script>
	// export let name = "World";
	let point = 100;

	const addPoint = () => point += 1;
	const minPoint = () => point -= 1;
	let showControls = false

	const toggle = () => showControls = !showControls
</script>

<main>
	<div class="container">
		<div class="card">
			<h1>Hallo</h1>
			<!-- Toggle -->
			<button class="btn btn-sm" on:click={toggle}>Toggle</button>
			{#if showControls}
			<h2>{point}</h2>
			<!-- Onlclik -->
			<button class="btn" on:click="{addPoint}">+1</button>
			<button class="btn btn-dark" on:click="{minPoint}">-1</button>
			<br>
			<!-- Bind -->
			<input type="number" bind:value={point}>
			{/if}
		</div>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>