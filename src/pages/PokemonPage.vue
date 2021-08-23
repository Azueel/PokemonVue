<template>
	<h1 v-if="!pokemon">Espere Por Favor...</h1>

	<div v-else>
		<img
			class="pokemonFrase"
			src="../assets/who-is-pokemonm.png"
			alt=""
		/>

		<PokemonPicture
			:pokemonId="pokemon.id"
			:showPokemon="showPokemon"
		/>
		<PokemonOptions
			:pokemons="pokemonArr"
			@selection="checkAnswer"
		/>
		<div v-if="showAnswer">
			<h2 class="fade-in">{{ message }}</h2>

			<button @click="newGame">Nuevo Juego</button>
		</div>
		<PokemonLive
			:pokemonLive="pokemonVida"
			v-if="selectedId !== pokemon.id"
			class="animate__animated
			animate__shakeX"
		/>

		<PokemonCount :pokemonScore="0" />
	</div>
</template>

<script>
import PokemonOptions from '@/components/PokemonOptions';
import PokemonPicture from '@/components/PokemonPicture';
import getPokemonOptions from '../helpers/getPokemonOptions';
import PokemonCount from '../components/PokemonCount.vue';
import PokemonLive from '../components/PokemonLive.vue';

export default {
	components: {
		PokemonOptions,
		PokemonPicture,
		PokemonLive,
		PokemonCount,
	},

	data() {
		return {
			pokemonArr: [],
			pokemon: null,
			showPokemon: false,
			showAnswer: false,
			message: '',
			pokemonVida: 100,
		};
	},

	methods: {
		async mixPokemonArray() {
			this.pokemonArr = await getPokemonOptions();

			const rndInt = Math.floor(Math.random() * 4);
			this.pokemon = this.pokemonArr[rndInt];
		},

		checkAnswer(selectedId) {
			this.showPokemon = true;
			this.showAnswer = true;

			if (selectedId === this.pokemon.id) {
				this.message = 'Felicidades Acertaste';
			} else {
				this.message = `Incorrecto, Como no vas a saber que es un ${this.pokemon.name}`;
				this.pokemonVida = this.pokemonVida - 25;
			}
		},

		newGame() {
			if (this.pokemonVida === 0) {
				this.showPokemon = false;
				this.showAnswer = false;
				this.pokemonArr = [];
				this.pokemon = null;
				(this.pokemonVida = 100), this.mixPokemonArray();
			} else {
				this.showPokemon = false;
				this.showAnswer = false;
				this.pokemonArr = [];
				this.pokemon = null;
				this.mixPokemonArray();
			}
		},
	},

	mounted() {
		this.mixPokemonArray();
	},
};
</script>

<style>
.pokemonFrase {
	width: 40rem;
	margin-right: 40vw;
}

button {
	padding: 1.5rem;
	background-color: yellow;
	color: blue;
	font-size: 1rem;
	margin-left: 230px;
	border-radius: 10px;
}
h2 {
	margin-left: 200px;
	font-weight: bold;
	font-size: 1.3 rem;
}
</style>
