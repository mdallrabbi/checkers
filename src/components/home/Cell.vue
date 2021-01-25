<template>
	<div
		:class="getClasses"
		class="cell"
		:style="{flex: size}"
		@click="selectCell">
		<template v-if="cell.piece">
			<app-piece
				:piece="cell.piece"
				@selectPiece="selectPiece"/>
		</template>
	</div>
</template>

<script>
	import Piece from 'Components/home/Piece.vue';

	export default {
		components: {
			appPiece: Piece
		},
		props: ['cell', 'size', 'x', 'y', 'moves'],
		computed: {
			getClasses(){
				const classes = [];
				if((this.x + this.y) % 2){
					classes.push(Constants.COLOR_BOTTOM);
				}else{
					classes.push(Constants.COLOR_TOP);
				}
				if(this.moves && Object.keys(this.moves).length){
					classes.push('selected');
				}
				if(this.cell.targeted){
					classes.push('targeted');
				}
				return classes;
			}
		},
		methods: {
			selectPiece(){
				this.$emit("selectPiece", this.cell.piece, this.moves);
			},
			selectCell(){
				if(this.cell.targeted){
					this.$emit("selectCell", this.x, this.y);
				}
			}
		}
	}
</script>

<style lang="scss">
	.cell{
		display        : flex;
		justify-content: center;
		align-items    : stretch;

		&:before {
			content: '';
			display: table;
			padding-top: 100%;
		}
		&.color-top{
			background-color: #0a1228;
		}
		&.color-bottom{
			background-color: #ffffff;
		}
		&.selected{
			background-color: rgb(123, 133, 117);
			.piece{
				cursor: pointer;
			}
		}
		&.targeted{
			background-color: rgb(1, 226, 43);
			cursor: pointer;
		}
	}
</style>