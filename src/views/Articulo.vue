<template lang="">
	<div>
		<Titulo texto="Ruta con parametros" />
		<h2>Parametro: {{ $route.params.id }}</h2>
		<h3>{{ articulo.title }}</h3>
		<p>{{ articulo.body }}</p>
	</div>
</template>
<script>
	import Titulo from "../components/Titulo.vue";
	export default {
		components: {
			Titulo,
		},
		data() {
			return {
				articulo: {},
			};
		},
		methods: {
			async consumirArticulo() {
				try {
					const data = await fetch(
						`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`
					);
					const objeto = await data.json();
					console.log(objeto);
					this.articulo = objeto;
				} catch (error) {
					console.log(error);
				}
			},
		},
		created() {
			this.consumirArticulo();
		},
	};
</script>
<style lang=""></style>
