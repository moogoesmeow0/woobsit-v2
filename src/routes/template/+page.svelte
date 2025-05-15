<script lang="ts">
	import { fade } from 'svelte/transition';
	import Blocks from './Blocks.svelte';
	import Preview from './Preview.svelte';
	import Settings from './Settings.svelte';
	import Variables from './Variables.svelte';

	let state: string = 'variables';
    let document = {text: "greetings"};
</script>

{#if state == 'variables'}
	<div transition:fade><Variables bind:document /></div>
{:else if state == 'blocks'}
	<div transition:fade><Blocks bind:document/></div>
{:else if state == 'preview'}
	<div transition:fade><Preview bind:document/></div>
{:else if state == 'settings'}
	<div transition:fade><Settings bind:document/></div>
{/if}

<button on:click={() => state = 'blocks'}>blocks</button>