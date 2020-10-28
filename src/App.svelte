<script>
	export let name;
</script>

<main>
	<h1>Hello {name}!</h1>

	<textarea bind:value={name} />

	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
<a-scene embedded>
	<a-text  position="0 0 -3"  scale="2 2 2 " rotation="0 45 0" 
	  color="#ff3e00" 
		value={name}></a-text>
</a-scene>

</main>



<style>
a-scene {
  height: 300px;
  width: 600px;
}

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