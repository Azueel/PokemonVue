<template>
	<div class="options-container">
		<ul>
			<li
				v-for="pokemon in pokemons"
				:key="pokemon.id"
				@click="$emit('selection', pokemon.id)"
			>
				{{ pokemon.name }}
			</li>
		</ul>
	</div>
</template>

<script>
export default {
	props: {
		pokemons: {
			type: Array,
			required: true,
		},
	},
};
</script>

<style scoped>
ul {
	list-style-type: none;
	margin-top: -5rem;
	margin-left: 200px;
}
li {
	background-color: white;
	border-radius: 5px;
	border: 1px solid rgba(0, 0, 0, 0.2);
	cursor: pointer;
	margin-bottom: 5px;
	width: 200px;
	background-color: khaki;
	padding: 0.5rem;
	margin: 1rem;
}

li:hover {
	background-color: rgba(0, 0, 0, 0.05);
}

.options-container {
	display: flex;
	justify-content: center;
}
</style>
