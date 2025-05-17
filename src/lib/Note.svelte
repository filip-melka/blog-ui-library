<script lang="ts">
	import type { Snippet } from 'svelte';

	interface Props {
		children: Snippet;
		type: 'note' | 'warning' | 'error';
		includeIcon: boolean;
	}

	let { children, type, includeIcon }: Props = $props();

	const colors = {
		note: {
			borderBg: 'bg-blue-800',
			bg: 'bg-blue-200',
			border: 'border-blue-800',
			text: 'text-blue-800'
		},
		warning: {
			borderBg: 'bg-yellow-600',
			bg: 'bg-yellow-200',
			border: 'border-yellow-600',
			text: 'text-yellow-700'
		},
		error: {
			borderBg: 'bg-red-800',
			bg: 'bg-red-200',
			border: 'border-red-800',
			text: 'text-red-800'
		}
	};
</script>

<div class={`relative w-full overflow-hidden rounded ${colors[type].bg}`}>
	<div class={`absolute top-0 right-0 h-full w-1 ${colors[type].borderBg}`}></div>
	<div class={`absolute top-0 left-0 h-full w-1 ${colors[type].borderBg}`}></div>
	<div
		class={`absolute -top-8 -left-8 h-16 w-16 rounded-full border-4 bg-white ${colors[type].border}`}
	></div>
	<div
		class={`& absolute -right-8 -bottom-8 h-16 w-16 rounded-full border-4 bg-white ${colors[type].border}`}
	></div>
	<div class="px-12 pt-4 pb-6">
		<div class="flex items-center gap-3">
			{#if includeIcon}
				{#if type === 'note'}
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
						class={`w-6 ${colors[type].text}`}
						><path
							d="M4.5 16.5c-1.5 1.26-2 5-2 5s3.74-.5 5-2c.71-.84.7-2.13-.09-2.91a2.18 2.18 0 0 0-2.91-.09z"
						/><path
							d="m12 15-3-3a22 22 0 0 1 2-3.95A12.88 12.88 0 0 1 22 2c0 2.72-.78 7.5-6 11a22.35 22.35 0 0 1-4 2z"
						/><path d="M9 12H4s.55-3.03 2-4c1.62-1.08 5 0 5 0" /><path
							d="M12 15v5s3.03-.55 4-2c1.08-1.62 0-5 0-5"
						/></svg
					>
				{:else if type === 'warning'}
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
						class={`w-6 ${colors[type].text}`}
						><path
							d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3"
						/><path d="M12 9v4" /><path d="M12 17h.01" /></svg
					>
				{:else if type === 'error'}
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
						class={`w-6 ${colors[type].text}`}
						><path d="m8 2 1.88 1.88" /><path d="M14.12 3.88 16 2" /><path
							d="M9 7.13v-1a3.003 3.003 0 1 1 6 0v1"
						/><path
							d="M12 20c-3.3 0-6-2.7-6-6v-3a4 4 0 0 1 4-4h4a4 4 0 0 1 4 4v3c0 3.3-2.7 6-6 6"
						/><path d="M12 20v-9" /><path d="M6.53 9C4.6 8.8 3 7.1 3 5" /><path d="M6 13H2" /><path
							d="M3 21c0-2.1 1.7-3.9 3.8-4"
						/><path d="M20.97 5c0 2.1-1.6 3.8-3.5 4" /><path d="M22 13h-4" /><path
							d="M17.2 17c2.1.1 3.8 1.9 3.8 4"
						/></svg
					>
				{/if}
			{/if}
			<p class={`mb-1 text-lg font-semibold ${colors[type].text}`}>Note</p>
		</div>
		{@render children?.()}
	</div>
</div>
