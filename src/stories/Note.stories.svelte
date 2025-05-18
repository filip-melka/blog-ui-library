<script module>
	// @ts-nocheck

	import { defineMeta } from '@storybook/addon-svelte-csf';

	import Note from '../lib/Note.svelte';
	import TailwindDecorator from './decorators/TailwindDecorator.svelte';
	import BothThemes from './decorators/theme-decorators/BothThemes.svelte';
	import LightTheme from './decorators/theme-decorators/LightTheme.svelte';
	import DarkTheme from './decorators/theme-decorators/DarkTheme.svelte';

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
		decorators: [() => TailwindDecorator]
	});
</script>

<Story
	name="Primary"
	args={{
		type: 'note',
		includeIcon: true
	}}
	decorators={[() => BothThemes]}
>
	<p>
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima velit molestias praesentium
		aliquid saepe debitis? Vero voluptas ex, maiores praesentium a amet et tempora sint, nobis
		quaerat est soluta debitis.
	</p>
</Story>

<Story
	name="Light"
	args={{
		type: 'note',
		includeIcon: true
	}}
	decorators={[() => LightTheme]}
>
	<p>
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima velit molestias praesentium
		aliquid saepe debitis? Vero voluptas ex, maiores praesentium a amet et tempora sint, nobis
		quaerat est soluta debitis.
	</p>
</Story>

<Story
	name="Dark"
	args={{
		type: 'note',
		includeIcon: true
	}}
	decorators={[() => DarkTheme]}
>
	<p>
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima velit molestias praesentium
		aliquid saepe debitis? Vero voluptas ex, maiores praesentium a amet et tempora sint, nobis
		quaerat est soluta debitis.
	</p>
</Story>
