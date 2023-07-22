<script>
	import Todo from './component/Todo.svelte'

	let title = ''
	let todos = []
	let id = 0;

	function createTodo() {
		todos.push({
			id,
			title
		})
		todos = todos
		title = ''
		id++
	}
</script>

<main>
	<input
		type="text"
		bind:value={title}
		on:keydown={(e) => {e.key === 'Enter' && createTodo()}}
	/>
	<button on:click={createTodo}>
		Create Todo
	</button>

	{#each todos as todo}
		<Todo
			bind:todos={todos}
			{todo}
		/>
	{/each}
</main>