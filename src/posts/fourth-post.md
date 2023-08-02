---
title: Svelte Lessons - Context API
description: Frontend Masters Svelte Workshop - Context API
date: '2023-08-02'
categories: 
    - sveltekit
    - svelte
published: true
---

## Context API 

<Child />

<script>
	import Canvas from '/src/lib/components/svelte-workshop/Canvas.svelte';
	import Square from '/src/lib/components/svelte-workshop/Square.svelte';
    import Child from '/src/lib/components/svelte-workshop/Child.svelte';
	import { setContext } from 'svelte'; // you set the context on the page that later will call a component 
     // that will use this context. In this case `color`
     // The page that imports the component is the parent and the imorted page/component is the child

	let color = 'red';
	setContext('color', color);

	// we use a seeded random number generator to get consistent jitter
	let seed = 1;

	function random() {
		seed *= 16807;
		seed %= 2147483647;
		return (seed - 1) / 2147483646;
	}

	function jitter(amount) {
		return amount * (random() - 0.5);
	}
</script>

<div class="container">
	<Canvas width={800} height={1200}>
		{#each Array(12) as _, c}
			{#each Array(22) as _, r}
				<Square
					x={180 + c * 40 + jitter(r * 2)}
					y={180 + r * 40 + jitter(r * 2)}
					size={40}
					rotate={jitter(r * 0.05)}
				/>
			{/each}
		{/each}
	</Canvas>
</div>

<style>
	.container {
		height: 100%;
		aspect-ratio: 2 / 3;
		margin: 0 auto;
		background: rgb(224, 219, 213);
		filter: drop-shadow(0.5em 0.5em 1em rgba(0, 0, 0, 0.1));
	}
</style>


