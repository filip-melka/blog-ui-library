<script lang="ts">
	import type { Snippet } from 'svelte';

	interface Props {
		children: Snippet;
		theme: 'light' | 'dark';
	}

	let { children, theme }: Props = $props();

	const classes = {
		light: {
			bg: 'bg-white',
			text: 'text-[#2b2b2b]'
		},
		dark: {
			bg: 'bg-[#17181c]',
			text: 'text-[#efefef]'
		}
	};
</script>

<div class={`relative w-full py-16 ${classes[theme].bg} ${classes[theme].text}`}>
	<div class="absolute top-2 right-2 opacity-50">
		{#if theme === 'light'}
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="24"
				height="24"
				viewBox="0 0 24 24"
				fill="none"
				stroke="currentColor"
				stroke-width="2"
				stroke-linecap="round"
				stroke-linejoin="round"
				class="lucide lucide-sun-icon lucide-sun"
				><circle cx="12" cy="12" r="4" /><path d="M12 2v2" /><path d="M12 20v2" /><path
					d="m4.93 4.93 1.41 1.41"
				/><path d="m17.66 17.66 1.41 1.41" /><path d="M2 12h2" /><path d="M20 12h2" /><path
					d="m6.34 17.66-1.41 1.41"
				/><path d="m19.07 4.93-1.41 1.41" /></svg
			>
		{:else if theme === 'dark'}
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="24"
				height="24"
				viewBox="0 0 24 24"
				fill="none"
				stroke="currentColor"
				stroke-width="2"
				stroke-linecap="round"
				stroke-linejoin="round"
				class="lucide lucide-moon-icon lucide-moon"
				><path d="M12 3a6 6 0 0 0 9 9 9 9 0 1 1-9-9Z" /></svg
			>
		{/if}
	</div>
	<div class="mx-auto w-full max-w-2xl">
		{@render children()}
	</div>
</div>
