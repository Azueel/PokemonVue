<template>
	<div class="container">
		<div class="titleCount">
			<img src="../assets/iconPlayer.png" alt="icon-player" />
			<p class="moveContent">Jugador 1</p>
			<p class="moveContent">Lv:40</p>
		</div>

		<div>
			<div class="container-div">
				<p v-if="live >= 100" class="container-p"></p>
				<p v-else-if="live === 75" class="container-p2"></p>
				<p v-else-if="live === 50" class="container-p3"></p>
				<p v-else-if="live === 25" class="container-p4"></p>
				<p class="text-live">{{ live }}/100</p>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		pokemonLive: {
			type: Number,
			requiere: true,
		},
	},

	data() {
		return {
			live: this.pokemonLive,
			myStyle: {
				backgroundColor: 'green',
				width: '19.vw',
			},
		};
	},
};
</script>

<style>
.container {
	background-color: #f5f5dc;
	width: 30vw;
	height: 15vh;
	margin-left: 67vw;
	margin-top: -58vh;
	border: solid 3px green;
}

.titleCount {
	font-family: 'Press Start 2P', cursive;
	display: flex;
	justify-content: space-between;
	padding: 4px;
}

.container-div {
	border: solid 5px;
	height: 20px;
	width: 19.5vw;
	margin-left: 140px;
	margin-top: -80px;
}

.container-p {
	height: 20px;
	background-color: green;
	width: 19.5vw;
	margin-top: -0.4px;
}

.container-p:hover {
	width: 15vw;
}
.moveContent {
	display: flex;
	margin-right: 90px;
	font-size: 17px;
}

.text-live {
	font-family: 'Press Start 2P', cursive;
	font-size: 20px;
	margin-left: 220px;
}

.container-p2 {
	height: 20px;
	background-color: rgb(84, 202, 84);
	width: 14.625vw;
	margin-top: -0.4px;
}

.container-p3 {
	height: 20px;
	background-color: rgb(235, 223, 68);
	width: 9.75vw;
	margin-top: -0.4px;
}

.container-p4 {
	height: 20px;
	background-color: rgb(226, 12, 12);
	width: 4.875vw;
	margin-top: -0.4px;
}
</style>
