<template>
	<div class="pokemon-container">
		<img
			v-if="!showPokemon"
			:src="imgSrc"
			alt="pokemon"
			class="hidden-pokemon"
		/>

		<img v-else :src="imgSrc" alt="pokemon" class="fade-in" />
	</div>
</template>

<script>
export default {
	props: {
		pokemonId: {
			type: Number,
			require: true,
		},

		showPokemon: {
			type: Boolean,
			requiere: true,
			default: false,
		},
	},

	computed: {
		imgSrc() {
			return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
		},
	},
};
</script>

<style scoped>
/* Pokemon Picture */
.pokemon-container {
	height: 200px;
}
img {
	height: 500px;
	position: absolute;
	bottom: 25%;
	right: 58%;
	user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	-webkit-user-drag: none;
	-webkit-user-select: none;
}
.hidden-pokemon {
	filter: brightness(0);
}
</style>
