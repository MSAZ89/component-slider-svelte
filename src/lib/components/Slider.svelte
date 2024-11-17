<script lang="ts">
	import { fly } from 'svelte/transition';

	// Define the type for our elements
	type SliderElement = {
		component?: any;
		props?: any;
		html?: string;
	};

	// Accept elements as a prop
	export let elements: SliderElement[] = [];

	// Optional props for customization
	export let transitionDuration = 300;
	export let transitionDistance = 500;
	export let containerHeight = 'h-32';
	export let containerWidth = 'w-64';

	let currentIndex = 0;
	let direction = 1; // 1 for right-to-left, -1 for left-to-right

	function showPrevious() {
		if (elements.length <= 1) return;
		direction = -1;
		currentIndex = (currentIndex - 1 + elements.length) % elements.length;
	}

	function showNext() {
		if (elements.length <= 1) return;
		direction = 1;
		currentIndex = (currentIndex + 1) % elements.length;
	}
</script>

<div class="flex flex-col items-center justify-center space-y-4">
	<div class="space-x-4">
		<button
			class="rounded bg-gray-300 px-4 py-2 text-gray-700 hover:bg-gray-400 disabled:opacity-50"
			on:click={showPrevious}
			disabled={elements.length <= 1}
		>
			Previous
		</button>
		<button
			class="rounded bg-gray-300 px-4 py-2 text-gray-700 hover:bg-gray-400 disabled:opacity-50"
			on:click={showNext}
			disabled={elements.length <= 1}
		>
			Next
		</button>
	</div>

	<div class="relative {containerHeight} {containerWidth}">
		{#if elements.length > 0}
			{#key currentIndex}
				<div
					class="absolute left-0 right-0"
					transition:fly={{
						x: transitionDistance * direction,
						duration: transitionDuration,
						opacity: 0
					}}
				>
					{#if elements[currentIndex]?.component}
						<svelte:component
							this={elements[currentIndex].component}
							{...elements[currentIndex].props}
						/>
					{:else if elements[currentIndex]?.html}
						{@html elements[currentIndex].html}
					{/if}
				</div>
			{/key}
		{/if}
	</div>
</div>
