<template>
	<div class="mt-10 mb-10 px-10 grid grid-cols-1 gap-x-8 gap-y-10 2xl:grid-cols-4 xl:grid-cols-3 lg:grid-cols-2
	justify-items-center lg:justify-items-start">
		<DishCard
			v-for="dish in dishes"
			:key="dish.id"
			:dish="dish"
			@delete-dish="emitDelete"
		/>
	</div>
</template>

<script setup>
import DishCard from './DishCard.vue';

const props = defineProps({
	dishes: Array,
});

const emit = defineEmits(['delete-dish']);

function emitDelete(id) {
	emit('delete-dish', id);
}
</script>
