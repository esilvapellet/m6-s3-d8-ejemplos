<template>
	<div id="app">
		<h1 :style="{ color: principal }">Título principal</h1>
		<div>
			<div>
				<strong>Medidas imagen</strong>
			</div>
			<hr>
			<div>
				<label for="anchoImg">Ancho: </label>
				<input type="range" name="vol" id="anchoImg" min="20" max="anchoImagen" step="1" v-model="anchoImagen" />
				<span>
					{{ anchoImagen }}%
				</span>
			</div>

			<div>
				<label for="radioImg">Radio: </label>
				<input type="range" name="vol" id="radioImg" min="20" max="radioImagen" step="10" v-model="radioImagen" />
				<span>
					{{ radioImagen }}%
				</span>
			</div>
			<hr>
			<div>
				<strong>Estilos imagen</strong>
			</div>
			<hr>
			<div>
				<span>Sombra horizontal: </span> <input type="range" id="rangeSombraHorizontal" name="rangeSombraHorizontal"
					min="-20" max="30" step="1" v-model="sHorizontal"><span>{{ sHorizontal
						+ "%" }} </span>
			</div>
			<div>

				<span>Sombra Vertical: </span> <input type="range" id="rangeSombraVertical" name="rangeSombraVertical"
					min="-20" max="30" step="1" v-model="sVertical"><span>{{ sVertical + "%" }} </span>
			</div>
			<div>
				<span>Color sombra: </span> <input type="color" id="rangeSombraColor" name="rangeSombraColor"
					v-model="sColor"><span> </span>


			</div>
			<figure style="display: flex; justify-content: center;">
				<img :width="anchoImagen + '%'" :style="{
					boxShadow: sombraImagen,
					borderRadius: radioImagen + '%'
				}" src="https://picsum.photos/id/1025/1200/800" alt="" />
			</figure>
		</div>
		<br>
		<hr>
		<div>
			<p :class="{ realizado: p1 }">Texto de ejemplo 1 <input type="checkbox" v-model="p1"></p>
			<p :class="{ realizado: p2 }">Texto de ejemplo 2 <input type="checkbox" v-model="p2"></p>
			<p :class="{ realizado: p3 }">Texto de ejemplo 3 <input type="checkbox" v-model="p3"></p>
			<p :class="{ realizado: p4 }">Texto de ejemplo 4 <input type="checkbox" v-model="p4"></p>
		</div>
	</div>
</template>

<script>
export default {
	name: "App",
	components: {},
	data() {
		return {
			principal: "blue",
			anchoImagen: 50,
			radioImagen: 30,
			sHorizontal: 10,
			sVertical: 10,
			sBlurRadius: 5,
			sSpreadRadius: 1,
			sColor: "rgba(0,0,0,0.75)",
			p1: false,
			p2: false,
			p3: false,
			p4: false

		};
	},
	computed: {
		sombraImagen: function () {
			let { sHorizontal, sVertical, sBlurRadius, sSpreadRadius, sColor } = this;
			let boxShadow = `${sHorizontal}px ${sVertical}px ${sBlurRadius}px ${sSpreadRadius}px ${sColor}`;
			return boxShadow;
		}
	}
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	/* text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}

.realizado {
	color: green;
	font-weight: 700;
}
</style>
