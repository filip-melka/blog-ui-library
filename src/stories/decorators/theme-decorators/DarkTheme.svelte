<script lang="ts">
	import type { Snippet } from 'svelte';
	import Container from './Container.svelte';

	interface Props {
		children: Snippet;
	}

	let { children }: Props = $props();
</script>

<Container theme="dark">
	{@render children()}
</Container>
