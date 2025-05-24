<script lang="ts">
	interface Props {
		correctAnswer: string;
		otherOptions: string[];
	}

	let { correctAnswer, otherOptions }: Props = $props();

	const options = [correctAnswer, ...otherOptions];

	shuffle(options);

	let selectedOption: null | string = $state(null);

	const State = {
		selecting: 0,
		selected: 1,
		correct: 2,
		incorrect: 3
	};

	let currentState: number = $state(State.selecting);

	function selectOption(option: string) {
		currentState = State.selected;
		selectedOption = option;
	}

	function check() {
		currentState = selectedOption === correctAnswer ? State.correct : State.incorrect;
	}

	function shuffle(array: any[]) {
		let currentIndex = array.length;

		while (currentIndex != 0) {
			let randomIndex = Math.floor(Math.random() * currentIndex);
			currentIndex--;

			[array[currentIndex], array[randomIndex]] = [array[randomIndex], array[currentIndex]];
		}
	}
</script>

<div class="h-fit w-full">
	<p class="mb-6 text-center text-lg font-medium">
		Lorem ipsum dolor, sit amet consectetur adipisicing elit.
	</p>
	{#each options as option}
		<button
			class="mt-4 flex w-full cursor-pointer items-center justify-start gap-4 rounded-lg bg-blue-100/40 py-3 pr-6 pl-2 hover:bg-blue-100/80"
			onclick={() => selectOption(option)}
		>
			<div class={`flex h-6 w-6 items-center justify-center rounded-full border-2 border-blue-500`}>
				{#if option === selectedOption}
					<div class="h-4 w-4 rounded-full bg-blue-500"></div>
				{/if}
			</div>
			<p>{option}</p>
		</button>
	{/each}
	<button
		onclick={check}
		disabled={currentState !== State.selected}
		class="mt-8 flex w-full cursor-pointer items-center justify-center gap-4 rounded-lg bg-blue-400 py-3 pr-6 pl-2 disabled:cursor-default"
	>
		{#if currentState === State.correct}
			<p>Correct!</p>
		{:else if currentState === State.incorrect}
			<p>Try again!</p>
		{:else}
			<p>Submit</p>
		{/if}
	</button>
</div>
