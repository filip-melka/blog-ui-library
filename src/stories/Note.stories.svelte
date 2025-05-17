<script module>
	import { defineMeta } from '@storybook/addon-svelte-csf';

	import Note from '../lib/Note.svelte';
	import TailwindDecorator from './TailwindDecorator.svelte';

	const { Story } = defineMeta({
		component: Note,
		title: 'Components/Note',
		argTypes: {
			includeIcon: {
				control: 'boolean'
			},
			type: {
				control: 'select',
				options: ['note', 'warning', 'error']
			}
		},
		// @ts-ignore
		decorators: [() => TailwindDecorator]
	});
</script>

<Story
	name="Primary"
	args={{
		type: 'note',
		includeIcon: true
	}}
>
	<!-- prettier-ignore -->
	<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima velit molestias praesentium aliquid saepe debitis? Vero voluptas ex, maiores praesentium a amet et tempora sint, nobis quaerat est soluta debitis.</p>
</Story>
