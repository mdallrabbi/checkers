<template>
	<v-toolbar
		light
		class="avatar">
		<img
			class="logo"
			src="assets/logo.png">
		<v-toolbar-title class="white--text">checker game</v-toolbar-title>
		<v-spacer/>
		<v-btn
			flat
			@click="newGame">new game</v-btn>
	</v-toolbar>
</template>

<script>
	import 'Assets/logo.png';

	export default {
		methods: {
			newGame(){
				this.$emit("newGame");
			}
		}
	}
</script>

<style lang="scss">
	.logo{
		width : 20px;
		height: 20px;
	}
</style>

