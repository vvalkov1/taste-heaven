<template>
	<div class="app">
		<header class="h-16 mb-10 bg-slate-600 flex items-center justify-center">
			<h1 class="font-bold text-lg">Taste Heaven</h1>
		</header>
		<AddDish @add-dish="addDish" />
		<DishFilter @filter-dishes="filterDishes" />
		<DishList :dishes="filteredDishes" @delete-dish="deleteDish" />
	</div>
</template>

<script setup>
import { ref, computed } from 'vue';
import AddDish from './components/AddDish.vue';
import DishFilter from './components/DishFilter.vue';
import DishList from './components/DishList.vue';

const dishes = ref([]);
const filterTerm = ref('');

// Method to add a new dish
function addDish(newDish) {
	dishes.value.push(newDish);
}

// Method to filter dishes by name
function filterDishes(term) {
	filterTerm.value = term;
}

// Filtered dishes based on the filter term
const filteredDishes = computed(() =>
	dishes.value.filter((dish) =>
		dish.name.toLowerCase().includes(filterTerm.value.toLowerCase()),
	),
);

// Method to delete a dish
function deleteDish(id) {
	dishes.value = dishes.value.filter((dish) => dish.id !== id);
}
</script>

<style>
/* Add basic styling or use TailwindCSS if preferred */
</style>
