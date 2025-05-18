<script module>
	// @ts-nocheck

	import { defineMeta } from '@storybook/addon-svelte-csf';
	import CodeBlock from '../lib/CodeBlock.svelte';
	import TailwindDecorator from './decorators/TailwindDecorator.svelte';
	import BothThemes from './decorators/theme-decorators/BothThemes.svelte';
	import DarkTheme from './decorators/theme-decorators/DarkTheme.svelte';
	import LightTheme from './decorators/theme-decorators/LightTheme.svelte';

	const { Story } = defineMeta({
		component: CodeBlock,
		title: 'Components/Code Block',
		argTypes: {
			language: {
				control: 'text'
			}
		},
		decorators: [() => TailwindDecorator]
	});
</script>

<Story
	name="Primary"
	args={{
		language: 'ts'
	}}
	decorators={[() => BothThemes]}
>
	<!-- prettier-ignore -->
	<pre><code><span class="line"
            ><span style="color:#FF79C6">const</span><span style="color:#F8F8F2"> myVar </span><span
                style="color:#FF79C6">=</span
            ><span style="color:#BD93F9"> 5</span></span
        >
<span class="line"></span>
<span class="line"
        ><span style="color:#FF79C6">function</span><span style="color:#50FA7B"> handleClick</span
        ><span style="color:#F8F8F2">() &#10627;</span></span
    >
<span class="line"
        ><span style="color:#F8F8F2">	console.</span><span style="color:#50FA7B">log</span><span
            style="color:#F8F8F2">(</span
        ><span style="color:#E9F284">'</span><span style="color:#F1FA8C">Hello World</span><span
            style="color:#E9F284">'</span
        ><span style="color:#F8F8F2">)</span></span
    >
<span class="line"><span style="color:#F8F8F2">&#10628;</span></span></code
    ></pre>
</Story>

<Story
	name="Dark"
	args={{
		language: 'ts'
	}}
	decorators={[() => DarkTheme]}
>
	<!-- prettier-ignore -->
	<pre><code><span class="line"
            ><span style="color:#FF79C6">const</span><span style="color:#F8F8F2"> myVar </span><span
                style="color:#FF79C6">=</span
            ><span style="color:#BD93F9"> 5</span></span
        >
<span class="line"></span>
<span class="line"
        ><span style="color:#FF79C6">function</span><span style="color:#50FA7B"> handleClick</span
        ><span style="color:#F8F8F2">() &#10627;</span></span
    >
<span class="line"
        ><span style="color:#F8F8F2">	console.</span><span style="color:#50FA7B">log</span><span
            style="color:#F8F8F2">(</span
        ><span style="color:#E9F284">'</span><span style="color:#F1FA8C">Hello World</span><span
            style="color:#E9F284">'</span
        ><span style="color:#F8F8F2">)</span></span
    >
<span class="line"><span style="color:#F8F8F2">&#10628;</span></span></code
    ></pre>
</Story>

<Story
	name="Light"
	args={{
		language: 'ts'
	}}
	decorators={[() => LightTheme]}
>
	<!-- prettier-ignore -->
	<pre><code><span class="line"
            ><span style="color:#FF79C6">const</span><span style="color:#F8F8F2"> myVar </span><span
                style="color:#FF79C6">=</span
            ><span style="color:#BD93F9"> 5</span></span
        >
<span class="line"></span>
<span class="line"
        ><span style="color:#FF79C6">function</span><span style="color:#50FA7B"> handleClick</span
        ><span style="color:#F8F8F2">() &#10627;</span></span
    >
<span class="line"
        ><span style="color:#F8F8F2">	console.</span><span style="color:#50FA7B">log</span><span
            style="color:#F8F8F2">(</span
        ><span style="color:#E9F284">'</span><span style="color:#F1FA8C">Hello World</span><span
            style="color:#E9F284">'</span
        ><span style="color:#F8F8F2">)</span></span
    >
<span class="line"><span style="color:#F8F8F2">&#10628;</span></span></code
    ></pre>
</Story>
