<script module>
	import { defineMeta } from '@storybook/addon-svelte-csf';
	import { expect, userEvent, within } from '@storybook/test';
	import Quiz from '../lib/Quiz.svelte';
	import TailwindDecorator from './TailwindDecorator.svelte';

	const { Story } = defineMeta({
		component: Quiz,
		title: 'Components/Quiz',
		argTypes: {
			correctAnswer: {
				control: 'text'
			},
			otherOptions: {
				control: 'object'
			}
		},
		// @ts-ignore
		decorators: [() => TailwindDecorator]
	});
</script>

<Story
	name="Primary"
	args={{
		correctAnswer: 'Correct option',
		otherOptions: ['Option 1', 'Option 2']
	}}
	play={async ({ canvasElement, args }) => {
		const canvas = within(canvasElement);

		expect(args.otherOptions.length).toBeGreaterThanOrEqual(1);

		const correctAnswer = args.correctAnswer;
		const incorrectAnswer = args.otherOptions[0];

		expect(correctAnswer).not.toBeNull();
		expect(incorrectAnswer).not.toBeNull();

		const correctAnswerBtn = canvas.getByRole('button', { name: correctAnswer });
		const incorrectAnswerBtn = canvas.getByRole('button', { name: incorrectAnswer });

		const submitBtn = canvas.getByRole('button', { name: 'Submit' });

		expect(submitBtn).not.toBeNull();

		await userEvent.click(incorrectAnswerBtn);
		await userEvent.click(submitBtn);

		expect(submitBtn).toHaveTextContent('Try again!');

		await userEvent.click(correctAnswerBtn);
		await userEvent.click(submitBtn);

		expect(submitBtn).toHaveTextContent('Correct!');
	}}
/>
