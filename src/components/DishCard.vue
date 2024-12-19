<template>
	<div
		class="w-full bg-white border border-gray-300 rounded-lg shadow hover:bg-gray-300"
	>
		<a href="#">
			<div class="bg-clip-border rounded-xl h-96 w-full">
				<img class="rounded-t-lg object-cover w-full h-full" :src="dish.imageSrc" :alt="dish.name" />
			</div>
		</a>

		<div class="p-5">
			<a href="#">
				<h5
					class="mb-2 text-2xl font-bold tracking-tight text-gray-900 text-wrap break-words"
				>
					{{ dish.name }}
				</h5>
			</a>
			<p class="mb-3 font-normal text-gray-600 text-wrap break-words">
				{{ dish.description }}
			</p>
			<a
				href="#"
				class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300"
				@click="deleteDish"
			>
				Delete
				<TrashIcon class="w-4 h-4 ml-1" />
			</a>
		</div>
	</div>

</template>

<script setup>
import { TrashIcon } from '@heroicons/vue/24/solid';

const props = defineProps({
	dish: Object,
});

const emit = defineEmits(['delete-dish']);

function deleteDish() {
	emit('delete-dish', props.dish.id);
}
</script>
