<script setup>
	import { ref } from 'vue';
	const title = ref("");
	const ingredients = ref([]);
	const newIngredient = ref("");

	function addIngredient(){
		ingredients.value.push(newIngredient.value);
	}

	function checkEnter(e){
		if(e.key == "Enter"){
			addIngredient();
		}
	}

	function save(){
		let recipe = {
			title: title.value,
			ingredients: [...ingredients.value] 
		}

		console.log(recipe);
	}
</script>

<template>
	<label for="title">
		Name of Recipe:
		<input type="text" placeholder="Recipe Title" v-model="title" id="title" />
	</label>

	<h2>{{ title }}</h2>
	<ul v-for="i in ingredients">
		<li>{{ i }}</li>
	</ul>
	<input v-model="newIngredient" type="text" placeholder="New Ingredient" @keyup="checkEnter" />
	<button @click="addIngredient">Add</button>
	<button @click="save">Save</button>
</template>