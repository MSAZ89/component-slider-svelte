<script lang="ts">
	export let cardTitle = 'Card Title';
	export let cardDescription = 'This is a brief description of the card content.';
</script>

<div class="mx-auto max-w-sm overflow-hidden rounded-lg bg-white shadow-lg">
	<!-- svelte-ignore a11y_img_redundant_alt -->
	<img
		src="https://via.placeholder.com/400x200"
		alt="Card Image"
		class="h-48 w-full object-cover"
	/>
	<div class="p-6">
		<h2 class="text-xl font-bold text-gray-800">
			{cardTitle}
		</h2>
		<p class="mt-2 text-sm text-gray-600">{cardDescription}</p>
		<div class="mt-4">
			<a
				href="#"
				class="inline-block rounded bg-indigo-600 px-4 py-2 text-sm font-medium text-white hover:bg-indigo-500"
			>
				Read More
			</a>
		</div>
	</div>
</div>
