<script>
	export let todos = [];
	let newTodo = { text: '' };
	readTodos();
	function addTodo(e){
		e.preventDefault();
		todos = [...todos,{...newTodo}];
		newTodo.text = '';
		saveTodos();
	}
	function delTodo(e){
		todos = todos.filter(t => t.text !== e.srcElement.parentElement.firstElementChild.value);
		saveTodos();
	}
	function saveTodos(){
		localStorage.setItem('todos', JSON.stringify(todos));
	}
	function readTodos(){
		let t = JSON.parse(localStorage.getItem('todos'));
		todos = t?t:[];
	}
</script>

<style>
	main {
		padding-top: 60px;
		min-height: 100vh;
	}
</style>

<main class="container">
	<form class="field has-addons" on:submit={addTodo}>
		<input type="text" class="input is-black" bind:value={newTodo.text}>
		<input type="submit" class="button is-black" value="Add">
	</form>
	<ul class="list">
	{#each todos as todo}
		<li class="list-item field has-addons has-border-bottom">
			<input type="text" class="input is-white" bind:value={todo.text}>
			<input type="button" value="x" class="button is-black" on:click={delTodo}>
		</li>
	{/each}
	</ul>
</main>