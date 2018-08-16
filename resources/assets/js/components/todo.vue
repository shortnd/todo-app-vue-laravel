<template>
  <div>
      <div>
          <h1>Todo List</h1>
          <div>
              <input v-model="newTodo" placeholder="Add Todo">
              <button @click="add" :disabled="newTodo.length === 0">Add</button>
          </div>
      </div>
      <div>
          <div v-for="(todo, index) in todos" :key="todo.id">
              <p>{{todo.text}}</p>
              <button @click="updateStatus(todo)" v-text="todo.finished ? 'Not Done' : 'Done'"></button>
              <button @click="remove(index)">Remove</button>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    data(){
        return {
            todos: [],
            newTodo: '',
            baseId: 1,
        }
    },
    methods: {
        add() {
            let todo = {
                id: this.baseId,
                text: this.newTodo,
                finished: false
            }

            this.todo.push(todo);

            this.newTodo = '';
            this.baseId++;
        },
        updateStatus(todo) {
            todo.finished = !todo.finished;
        },
        remove(index) {
            this.todos.splice(index, 1);
        }
    }
}
</script>

<style lang="css">
</style>
