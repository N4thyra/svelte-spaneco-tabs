<script lang="ts">
	import { onMount } from 'svelte';

	export let items: any = "";
	export let showonpx: number = 150;
	export let clrbg: string = 'transparent';
	export let clrfill: string = '#ccc';
	export let clrfillhover: string = '#333';
	export let width: string = '50px';
	export let margin: string = '15px';
	export let position: number = 0;
	let progressPath;

	let visible: boolean = false;

	$:items = items.split('|')

	function t(i: any): void {
		[...document.querySelectorAll(`[data-id]:not([data-id="${i}"]).active`)].forEach( i => {
			i.classList.remove('active') 
			console.log(i);
		});
		document.querySelector(`[data-id="${i}"]`).classList.add('active')
	}

	onMount(() => {
		console.log(items)
	});
</script>

<!--Add this line to your web component-->
<svelte:options tag="spaneco-tabs" />

<div>
	{#each items as item}
		<div on:click={() => t(item)}>{item}</div>
	{/each}

	<slot name="content"></slot>
</div>

<style></style>