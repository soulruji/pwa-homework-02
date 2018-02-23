<template>
	<div>
		<ul>
			<li v-for="(todoItem, index) in propsdata">
				{{ todoItem }}
				<button v-on:click="removeTodo(todoItem, index)">remove</button>

			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		props: ['propsdata'],
		// data() {
		// 	return {
		// 		todoItems: []
		// 	}
		// },
		// created() {
		// 	console.log(localStorage.length);
		// 	if ( localStorage.length > 0) {
		// 		for (var i =0; i < localStorage.length; i++) {
		// 			console.log(localStorage.length);
		// 			this.todoItems.push(localStorage.key(i));
		// 		}
		// 	}
		// },
		methods: {
			removeTodo(todoItem, index) {
				this.$emit('removeTodo', todoItem, index);
			}
		},

	}
</script>

<style>
	ul {
		list-style-type: none;
		text-align: left;
		width: 90%;
		padding: 0;
		margin: 0 auto;
	}
	li {
		padding: 15px;
		background: #fff;
		margin-bottom: 5px;
		border-radius: 5px;
	}
</style>