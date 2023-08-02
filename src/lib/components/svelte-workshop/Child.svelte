<script>
// @ts-nocheck
	import { getContext } from 'svelte';

	let color_from_child = getContext('color');

</script>
<p>Context variable that was set in Child: {color_from_child}</p>


