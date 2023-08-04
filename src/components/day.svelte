<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	export let dayNumber: number;
	function sendDay() {
		dispatch('show-day', dayNumber);
	}
</script>

<div class="day-style" on:click={sendDay}>
	<h1>{dayNumber}</h1>
</div>

<style>
	.day-style {
		border: 1px solid black;
		border-radius: 5px;
		min-width: 50px;
		text-align: center;
	}
</style>
