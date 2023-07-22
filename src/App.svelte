<script>
	import { writable } from 'svelte/store'
	import Todo from './component/Todo.svelte'

	let title = ''
	let todos = writable([])
	let id = 0

	function createTodo() {
		if(!title.trim()) {
			title = ''
			return
		}
		$todos.push({
			id,
			title
		})
		$todos = $todos
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

	{#each $todos as todo}
	<!-- todos라는 store 객체를 넘겨줌 -->
		<Todo
			{todos}
			{todo}
		/>
	{/each}
</main>