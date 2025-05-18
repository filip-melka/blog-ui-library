<script lang="ts">
	import type { Snippet } from 'svelte';
	import ThemeComponent from './ThemeComponent.svelte';

	interface Props {
		children: Snippet;
		theme: 'light' | 'dark' | 'both';
	}

	let { children, theme }: Props = $props();
</script>

<div class="flex h-fit w-full flex-col">
	{#if theme === 'light' || theme === 'both'}
		<ThemeComponent theme="light">
			{@render children()}
		</ThemeComponent>
	{/if}
	{#if theme === 'dark' || theme === 'both'}
		<ThemeComponent theme="dark">
			{@render children()}
		</ThemeComponent>
	{/if}
</div>
