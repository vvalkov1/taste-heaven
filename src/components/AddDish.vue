<template>
	<div class="block sm:mx-auto sm:w-full sm:max-w-lg">
		<form class="w-full" @submit.prevent="submitForm">
			<div class="pb-12">
				<h2 class="text-base/7 font-semibold text-gray-900">Add Dish</h2>

				<p class="mt-1 text-sm/6 text-gray-600">
					This will add a new dish to the catalog
				</p>

				<div class="mt-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
					<div class="col-span-full">
						<label for="name" class="block text-sm/6 font-medium text-gray-900"
							>Name</label
						>

						<div class="mt-2">
							<input
								v-model="name"
								type="text"
								name="name"
								id="name"
								required
								class="block focus:outline-none w-full px-2 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6"
								placeholder="Spaghetti"
							/>
						</div>
					</div>

					<div class="col-span-full">
						<label
							for="description"
							class="block text-sm/6 font-medium text-gray-900"
							>Description</label
						>
						<div class="mt-2">
							<textarea
								v-model="description"
								id="description"
								name="description"
								placeholder="This is a delicious recipe that is easy to make and requires only a few ingredients."
								required
								rows="3"
								class="block focus:outline-none w-full px-2 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6"
							/>
						</div>
						<p class="mt-3 text-sm/6 text-gray-600">
							Write a few sentences about this dish
						</p>
					</div>

					<div class="col-span-full">
						<label for="image" class="block text-sm/6 font-medium text-gray-900"
							>Cover photo</label
						>

						<div class="mt-2">
							<PhotoIcon
								class="mx-auto size-12 text-gray-300"
								aria-hidden="true"
							/>

							<input
								v-model="image"
								type="text"
								name="image"
								id="image"
								placeholder="https://example.com/image.jpg"
								required
								class="block focus:outline-none w-full px-2 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6"
							/>
						</div>
					</div>
				</div>
			</div>

			<div class="mt-6 flex items-center justify-end gap-x-6">
				<button
					type="submit"
					class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
				>
					Save
				</button>
			</div>
		</form>
	</div>
</template>

<script setup>
import { ref } from 'vue';
import { v4 as uuidv4 } from 'uuid';
import { PhotoIcon } from '@heroicons/vue/24/solid';

const name = ref('');
const image = ref('');
const description = ref('');

const emit = defineEmits(['add-dish']);

function submitForm() {
	const newDish = {
		id: uuidv4(),
		name: name.value,
		imageSrc: image.value,
		description: description.value,
	};

	emit('add-dish', newDish);

	name.value = '';
	image.value = '';
	description.value = '';
}
</script>
