<template>
	<li>
		<div class="container-form">
			<p>{{ tareaText }}</p>

			<button class="btn-form" @click="deletePic(tareaText)">eliminar</button>
		</div>
	</li>
</template>

<script>
	export default {
		name: 'tarea-comp',
		props: {
			tareaText: {
				type: String,
				required: true,
			},
		},
		data: function () {
			return {};
		},
		// computed: {},
		methods: {
			deletePic(tareaText) {
				this.$emit('deletePic', tareaText);
			},
		},
		// watch: {},
		// components: {},
		// mixins: [],
		// filters: {},
		// -- Lifecycle Methods
		// -- End Lifecycle Methods
	};
</script>

<style scoped>
	li {
		padding-left: 20px;
		text-align: left;
	}
	.container-form {
		display: grid;
		grid-template-columns: 1fr 1fr;
		padding: 0;
		grid-gap: 20px;
	}
	p {
		display: inline-block;
		text-align: left;
		grid-column: span 1;
		font-weight: 600;
	}
	.btn-form {
		align-self: center;
		border: 1px solid #2c3e50;
		border-radius: 50px;
		background: white;
		color: #2c3e50;
		height: 20px;
		width: 80px;
		transition-duration: 0.5s;
		cursor: pointer;
	}
	.btn-form:hover {
		background: #ef7c8e;
		border: 1px solid white;
		color: white;
	}
</style>
