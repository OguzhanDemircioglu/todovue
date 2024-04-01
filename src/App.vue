<template>
  <div class="app">
    <form @submit.prevent="addTodo">
      <div class="field">
        <label class="label">Todo</label>
        <div class="control">
          <input
              v-model="todo"
              class="input"
              type="text"
              placeholder="Text input"
          />
        </div>
      </div>
      <button type="submit" class="button is-warning">Ekle</button>
    </form>

    <div v-for="item in todos" :key="item.id" class="card my-5">
      <div class="card-image">
      </div>
      <div class="card-content">
        <div class="media">
          <div class="media-left">
          </div>
          <div  class="media-content">
            <p @click="done(item)"
               class="title is-4"
               :class="{done: item.completed}"
            >{{item.text}}</p>
            <p class="subtitle is-6">Done: {{item.completed}}</p>
          </div>
        </div>
      </div>
    </div>

  </div>

</template>

<script>
import {ref} from "vue";

export default {
  setup() {
    const todo = ref(null);
    const todos = ref([]);

    function addTodo() {
      todos.value.push({
        id: Date.now(),
        text: todo.value,
        completed: false
      })
    }

    function done(todo){
      todo.completed = !todo.completed
    }

    return {
      todo,
      todos,
      addTodo,
      done
    }
  }
}
</script>

<style Lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 30%;
}

.done {
  background-color: cadetblue;
}
</style>
