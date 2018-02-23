<template>
	<div>
		<input type="text" v-model="newTodoItem" placeholder="할 일을 입력하세요.">
		<button v-on:click="addTodo">추가</button>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				newTodoItem: ''
			}
		},
		methods: {
			addTodo() {
				if ( this.newTodoItem !== ""){
					// console.log( this.newTodoItem );
					// localStorage.setItem( this.newTodoItem, this.newTodoItem );
					this.$emit('addTodo', this.newTodoItem);
					this.clearInput();					
				}
			},
			clearInput() {
				this.newTodoItem = '';
			}
		}
	}
</script>

<style>
	
</style>