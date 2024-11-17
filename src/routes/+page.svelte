<script lang="ts">
	import Slider from '$lib/components/Slider.svelte';
	import Card from '$lib/components/Card.svelte';

	// Define your elements
	const cardElements = [
		{
			component: Card,
			props: {
				cardTitle: 'Card 1',
				cardDescription: 'This is another card description for testing 1.'
			}
		},
		{
			component: Card,
			props: {
				cardTitle: 'Card 2',
				cardDescription: 'This is another card description for testing 2.'
			}
		},
		{
			component: Card,
			props: {
				cardTitle: 'Card 3',
				cardDescription: 'This is another card description for testing 3.'
			}
		}
	];

	// For a different slider with HTML elements
	const htmlElements = [
		{ html: '<div class="p-4 bg-yellow-500 text-white">Element 1</div>' },
		{ html: '<div class="p-4 bg-blue-500 text-white">Element 2</div>' },
		{ html: '<div class="p-4 bg-green-500 text-white">Element 3</div>' }
	];
</script>

<!-- Card Slider -->
<Slider
	elements={cardElements}
	containerHeight="h-96"
	containerWidth="w-96"
	transitionDuration={400}
	transitionDistance={600}
/>

<!-- HTML Elements Slider -->
<Slider elements={htmlElements} containerHeight="h-32" containerWidth="w-64" />
