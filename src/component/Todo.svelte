<script>
  export let todos, todo

  let isEdit = false
  let updatedTitle = ''

  function onEdit() {
    isEdit = true
    updatedTitle = todo.title
  }

  function offEdit() {
    isEdit = false
  }

  function updateTodo() {
    todo.title = updatedTitle
    offEdit()
  }

  function onDelete() {
    $todos = $todos.filter(t => t.id !== todo.id)
  }
</script>

{#if isEdit}
  <div>
    <input
      type="text"
      on:keydown={(e) => {e.key === 'Enter' && updateTodo()}}
      bind:value={updatedTitle}
    />
    <button on:click={updateTodo}>
      OK
    </button>
    <button on:click={offEdit}>
      Cancle
    </button>
  </div>
{:else}
  <div>
    {todo.title}
    <button on:click={onEdit}>
      Edit
    </button>
    <button on:click={onDelete}>
      Delete
    </button>
  </div>
{/if}
