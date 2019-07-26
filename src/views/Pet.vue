<template>
	<div>
		<h1>{{ animal.name }} ({{ $route.params.species }})</h1>
		<p>Gender: {{ animal.gender }}</p>
		<p>Age: {{ animal.breed }}</p>
	</div>
</template>

<script>
	import { mapState } from 'vuex'
	export default {
		data() {
			return {
				animal: {}
			}
		},
		computed: {
			...mapState([
				'cats',
				'dogs'
			])
		},

		mounted() {
			const idx = this.$route.params.id;
			const animals = this[this.$route.params.species];
			const animal = animals[idx];
			this.animal = animal;
		},
	}
</script>