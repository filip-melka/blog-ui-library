<script lang="ts">
	import type { Snippet } from 'svelte';

	interface Props {
		children: Snippet;
		language: string;
	}

	let { children, language }: Props = $props();
	let code: HTMLElement;
	let isCopied = $state(false);
	let isHovering = $state(false);
	let showCopyBtn = $derived(isCopied || isHovering);

	$effect(() => {
		if (isCopied) {
			setTimeout(() => {
				isCopied = false;
			}, 2000);
		}
	});

	async function handleCopy() {
		const codeContent = code.innerText;
		try {
			await navigator.clipboard.writeText(codeContent);
			isCopied = true;
		} catch (err) {
			console.error('Failed to copy text: ', err);
		}
	}
</script>

<!-- svelte-ignore a11y_no_static_element_interactions -->
<div
	class="relative w-full overflow-hidden rounded-lg bg-[#282A36] p-8"
	onmouseenter={() => {
		isHovering = true;
	}}
	onmouseleave={() => {
		isHovering = false;
	}}
>
	<button
		onclick={handleCopy}
		class={`${showCopyBtn ? 'opacity-100' : 'opacity-0'} absolute top-4 right-4 z-10 flex h-8 w-7 cursor-pointer items-center justify-center rounded bg-white/20 transition-opacity duration-200`}
	>
		{#if isCopied}
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
				class="lucide lucide-clipboard-check-icon lucide-clipboard-check"
				><rect width="8" height="4" x="8" y="2" rx="1" ry="1" /><path
					d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"
				/><path d="m9 14 2 2 4-4" /></svg
			>
		{:else}
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
				class="lucide lucide-clipboard-icon lucide-clipboard"
				><rect width="8" height="4" x="8" y="2" rx="1" ry="1" /><path
					d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"
				/></svg
			>
		{/if}
	</button>
	<span
		class={`${!showCopyBtn ? 'opacity-100' : 'opacity-0'} absolute top-4 right-4 z-0 text-white/50 transition-opacity duration-200`}
		>{language}</span
	>

	<div bind:this={code}>
		{@render children?.()}
	</div>
</div>
