<script lang="ts">
	let last_time: number | null = null;
	let bpm: number = 0;

	const message = "Tap the button!";

	function handle_click() {
		const current_time = new Date().getTime();
		if (last_time) {
			const difference = (current_time - last_time) / 1000;
			bpm = Math.round(60 / difference);
		}
		last_time = current_time;
	}
</script>

<h1>BPM measurement tool</h1>

<button on:click={handle_click} />

{#if last_time}
	<p class="bpm">
		{bpm}
	</p>
{:else}
	<p class="message">
		{message}
	</p>
{/if}

<style>
	h1 {
		font-weight: 400;
		padding-block: 2rem;
		text-align: center;
		margin-bottom: 1rem;
	}

	button {
		background-color: lime;
		box-shadow: 0em 0em 2rem #000 inset, 0em 0em 1em #fff2;
		width: 9rem;
		height: 9rem;
		border-radius: 50%;
		border: none;
		cursor: pointer;
		-webkit-tap-highlight-color: transparent;
	}

	.bpm {
		margin-top: 2rem;
		font-size: 3rem;
	}

	.message {
		margin-top: 2rem;
		font-size: 1.5rem;
	}
</style>
