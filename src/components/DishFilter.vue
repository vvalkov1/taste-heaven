<template>
	<div class="h-32 mt-10 bg-slate-600 flex flex-col items-center justify-center">
		<h2 class="font-bold text-lg">Filter dishes</h2>
		<input
			v-model="filterTerm"
			@input="emitFilter"
			placeholder="Filter by name"
			class="block focus:outline-none mt-2 w-2/3 px-2 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6"
		/>
	</div>
</template>

<script setup>
import { ref } from 'vue';

const filterTerm = ref('');

const emit = defineEmits(['filter-dishes']);

function emitFilter() {
	emit('filter-dishes', filterTerm.value);
}
</script>
