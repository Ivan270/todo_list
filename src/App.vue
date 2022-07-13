<template>
	<div id="app">
		<div class="container-form">
			<h1>To do List</h1>
			<form action="">
				<label for="">Tareas</label>
				<input type="text" placeholder="Ingresa una tarea" v-model="tarea" />
				<button class="btn-crear" type="submit" @click.prevent="capturar">
					Crear
				</button>
			</form>
		</div>
		<div class="container">
			<ul>
				<my-task
					v-for="tarea in tareas"
					:key="tarea"
					:tareaText="tarea"
					@deletePic="eliminar_tarea"
				></my-task>
			</ul>
		</div>
	</div>
</template>

<script>
	import TareaComp from '@/components/TareaComp.vue';

	export default {
		name: 'App',
		data() {
			return {
				tarea: '',
				tareas: [],
			};
		},
		methods: {
			capturar() {
				this.tareas.push(this.tarea);
				console.log(this.tarea);
				this.tarea = '';
				console.log(this.tareas);
			},
			eliminar_tarea(evento) {
				console.log(evento);
				let task = evento;
				let index = this.tareas.findIndex((tarea) => task == tarea);
				console.log(index);
				this.tareas.splice(index, 1);
			},
		},
		components: {
			'my-task': TareaComp,
		},
	};
</script>

<style>
	body {
		background: #e0e0e0;
	}
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 20px;
		display: grid;
		justify-content: center;
	}
	.container-form {
		padding: 20px 80px;
		text-align: center;
		border-radius: 20px;
	}
	.container {
		border-radius: 50px;
		background: linear-gradient(145deg, #f0f0f0, #cacaca);
		box-shadow: 20px 20px 60px #bebebe, -20px -20px 60px #ffffff;
		margin-top: 30px;
		height: 70vh;
		display: grid;
		place-content: center;
		width: 500px;
	}

	label {
		margin-right: 10px;
		font-weight: 700;
	}
	input {
		border-radius: 10px;
	}
	.btn-crear {
		margin-left: 10px;
		border: 1px solid white;
		border-radius: 50px;
		background: #2c3e50;
		color: white;
		width: 80px;
		transition-duration: 0.5s;
		cursor: pointer;
	}
	.btn-crear:hover {
		background: white;
		border: 1px solid #2c3e50;
		color: #2c3e50;
		font-weight: bolder;
	}
	.btn-crear:active {
		background: white;
		box-shadow: 0 5px #666;
		transform: translateY(3px);
	}
</style>
