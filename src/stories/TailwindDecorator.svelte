<script lang="ts">
	import type { Snippet } from 'svelte';
	import '../app.css';

	let { children }: { children: Snippet } = $props();
</script>

<div class="h-fit w-[90vw]">
	<div class="mx-auto max-w-2xl">
		{@render children()}
	</div>
</div>
